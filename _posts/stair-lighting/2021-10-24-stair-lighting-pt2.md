---
title: "LED Stair Lights Part 2: Real-Time Bass Visualization"
date: 2021-10-24T04:00:00-04:00
show_date: true
header:
  overlay_image: assets/posts/stair-lighting/music/header-music.jpg
  overlay_filter: 0.5
  teaser: assets/posts/stair-lighting/music/header-music.jpg
  #video:
  #  id: ydQNKzl7In4
  #  provider: youtube
  actions:
    - label: "GitHub Repository"
      url: "https://github.com/gidger/under-stair-lighting"
excerpt: "Real-Time bass visualizer, powered by Arduino and arduinoFFT."
categories:
  - Stair Lights
tags:
  - LED
  - Arduino
  - Home Improvement
  - Music

---

_Be sure to check out [Part 1](https://gidge.dev/stair%20lights/stair-lighting/) focusing on basic functionality and normal operation first. It's pretty cool, I promise!_

_And before we begin, here's a demonstration reel of the finished product:_
<iframe width="560" height="315" src="https://www.youtube.com/embed/AO4oNaiYNIw" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe><br>

After finishing up the installation of the cascading stair lights, I was pretty pleased with the results. But whenever I simply stopped and watched them in action, I couldn't help but think there was so much untapped potential to do more interesting things with the same lights. For a few months, I thought on-and-off about what else could be done...

Then I saw _it_. And I knew what I wanted to make.

In a the front window of a shop, I had seen an LED spectrum analyzer reacting to music, similar to the following:
<iframe width="560" height="315" src="https://www.youtube.com/embed/f814I4J8dEI?start=50" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe><br>

Immediately, I knew that I wanted to utilize the stair lights to do something similar – react to music in real-time with lights cascading up in a similar fashion as the video.

There’s an obvious difference between the stair lights and a full spectrum analyzer that you may notice. The stairs have only one "column" of lights, whereas a full spectrum analyzer has many columns in its LED matrix – each pertaining to a set of frequencies that compose the overall sound. The more of that frequency range that is present, the more lights that are illuminated.

Having only one column of lights to work with left me with a decision. I could either:
1. Simply have it react to the music volume, ignoring individual frequencies and only looking at the overall; or
2. Focus on a single range of frequencies and only react to those.

I chose to build the latter for a couple reasons. First, it gave me a good opportunity to learn to harness Fourier transforms on an Arduino to extract specific frequency ranges. And second, I had actually already completed a project that reacts to music volume in real time years ago!

_\*Sitcom flashback transition\*_

Back in January 2016, I had built a light-up dance floor for an engineering design competition. The whole project was done on a tight timeline, so the code was as kept simple as possible to allow for more time to build and wire the actual dance floor. As a result, the Arduino simply accepted an analogue audio input (line in) and lit up a selection of lights based on the overall volume. Was a fine MVP for what it needed to be.

Sadly, I only have a couple videos of it in action. This floor actually got recycled and used as a light wall for a special event at my university pub a couple months later. I don't think it survived much longer than that. Here's all the footage I have in one video:

<iframe width="560" height="315" src="https://www.youtube.com/embed/mynbzUVXnwU" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe><br>

So with that out of the way, ultimately what I decided to create was a real-time bass visualizer making use of a [MAX9814 microphone module](https://www.adafruit.com/product/1713) for audio detection and the [arduinoFFT library](https://www.arduino.cc/reference/en/libraries/arduinofft/) to extract the amount of bass present.

To support the multiple operating modes for the stairs (standard cascade and music), I've added a toggle button. When switching modes, all lights will flash a certain number of times to alert you to which mode you're in. One flash for standard mode, two for music.

<figure class="half">
  <a href="{{ site.url }}{{ site.baseurl }}/assets/posts/stair-lighting/music/mode-switch-close.gif"><img src="{{ site.url }}{{ site.baseurl }}/assets/posts/stair-lighting/music/mode-switch-close.gif" style='width: 85%;'>
  </a>
  <a href="{{ site.url }}{{ site.baseurl }}/assets/posts/stair-lighting/music/mode-switch-far.gif"><img src="{{ site.url }}{{ site.baseurl }}/assets/posts/stair-lighting/music/mode-switch-far.gif" style='width: 85%;'>
  </a>
</figure>

The MAX9814 microphone module was chosen over the similar [MAX4466 microphone module](https://www.adafruit.com/product/1063) due to its automatic gain control. This should better account for variability in the volume of music.

<figure style="text-align: center;">
  <a href="{{ site.url }}{{ site.baseurl }}/assets/posts/stair-lighting/music/button-mic.jpg"><img src="{{ site.url }}{{ site.baseurl }}/assets/posts/stair-lighting/music/button-mic.jpg" style='width: 85%;'>
  </a>
  <figcaption style="text-align: left;">I still need to come up with a perminant mounting solution for the button and mic. I don't want to leave them hanging like this forever.</figcaption>
</figure>

In the updated code, you'll see a variety of new functions relating to the new music mode. I won't get into the nitty-gritty in this blog post, but at a high level here's the overall logic of the music_mode() function:
- Audio is sampled for a period of time.
- This audio undergoes a Fourier transform to separate it into frequency bins (i.e. ranges) with associated amounts (e.g. how much of that frequency range was present in the sampled audio).
- The bass frequencies (less than ~320 Hz) are analyzed and translated into a number of lights to illuminate.
- If that number is higher than the number of lights currently illuminated, the lights will quickly cascade up until the correct number of lights are illuminated.
- The lights will cascade downwards (turn off) at a regular interval unless further bass is detected.

The code can be viewed in the project's [GitHub repository] (https://github.com/gidger/under-stair-lighting). Music mode is currently set up for 12 stairs, but can easily be modified for any number of stairs. Be sure to adjust the scaling factors (bin_multipliers and amplitude_divisor) as well. If you have any questions or issues, feel free to reach out to me at [stephen@gidge.dev](mailto: stephen@gidge.dev) for assistance.

My next steps for this project are to make a mount for the microphone module and further tune the parameters/scaling factors that convert bass into the number of stairs to illuminate. I need to dedicate some time to trying different combinations to determine what looks best. This project was never the most practical – the more people talking and walking around, the worse it performs (though that could be solved by using an analog line-in rather than a microphone). While not super practical, I do think the outcome was very cool, and I learned a lot about FFTs and more along the way. In the future, I'd like to try something similar with a more powerful board. The Arduino Mega's clock speed placed some very real limitations on what could be done when sampling audio and performing the Fourier transform. I hope this post gave you some inspiration for ways to take an old project and breathe some creative new life into it. Thanks for reading!

Cheers,

Stephen