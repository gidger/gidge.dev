---
title: "Cascading Stair Lighting"
date: 2021-06-02T15:34:30-04:00
categories:
  - Stair Lighting
tags:
  - LED
---

My household has a problem.

The main staircase has very poor lighting. There is no light fixture that illuminates the stairs, and as a result they can be quite treacherous overnight. Any sensible person would have thought "hey, let's just leave lights on in the nearest rooms at the top and bottom", and we did as well. But as you can guess by the existence of this blog post, we wanted to do something a little more fun and challenging to pass the time. This is the story of how my roommate Ben and overengineered a motion activated understair lighting system.

Why? 

Well, simply put, because we can.

If you're interested in learning more about how these lights came to life, check out the rest of this post. If not... well, here's some gifs of the finished product.

/inset gifs of finished product

---

Oh hey, you're still reading! Thanks!

After some light research we found inspiration in lights like these.

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/a10b5c8b-4a51-4f7a-af2f-d3acc2e79c8b/006bef502acd7df6cdaf5c33f220aff6.jpg](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/a10b5c8b-4a51-4f7a-af2f-d3acc2e79c8b/006bef502acd7df6cdaf5c33f220aff6.jpg)

Static understair lights.

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/4f5cf852-4d07-4606-9925-6ed6c59c2d54/e3b6d02087e5770025dd92364d87d349.gif](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/4f5cf852-4d07-4606-9925-6ed6c59c2d54/e3b6d02087e5770025dd92364d87d349.gif)

Raising side light.

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/fe3d387d-2734-48b8-b4e5-67d507a1dca2/smart-stair-lights-7080.gif](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/fe3d387d-2734-48b8-b4e5-67d507a1dca2/smart-stair-lights-7080.gif)

Cascading understair lights.

We ultimately decided that we wanted to make lights that cascade on upwards when one walks up the stairs, and downwards when one walks down. The lights should also cascade off in the same direction after being lit up for a set amount of time. A cooldown delay would be implemented so you wouldn't trigger the lights in the opposite direction if you're slightly too slow going up or down the stairs – essentially some extra buffer time.

With Ben and myself both having experience with Arduinos in the past, we decided to build on the familiar platform. Each stair would have a short LED strip that is connected to a shared power supply. A transistor between each LED strip and the power supply would be controlled by the Arduino and make the lights turn off and on. An ultrasonic sensor would be installed at the top and bottom of the staircase to detect when a person walks by.

Unfortunately, 16 stairs lights and two ultrasonic sensors exceeds the number of digital pins available on a standard Arduino Uno. As we already had a couple of Arduino Unos lying around, we decided to set up a master-slave system in order to gain access to the additional digital pins.

Well... until one of them died. Then we just decided to simplify the whole thing and order an Arduino Mega – simplifying things greatly.

After a couple iterations (and one terrifying spaghetti board that would surely not make it through airport security; see below) we settled on a super simple circuit on a breadboard. Essentially, there exists 16 identical circuits where a transistor acts as a simple "on/off" switch. Each of these are connected to a pin on the Arduino. The ultrasonic sensors are also connected to the Arduino and placed near the top and bottom of the stairs.

/insert image of final circuit

/insert image of sensors

/insert image of stairs with lights

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/e8068bed-a1e6-46f5-aa8b-ad534f2194ad/IMG_4768.jpg](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/e8068bed-a1e6-46f5-aa8b-ad534f2194ad/IMG_4768.jpg)

V1 - "Grounded Spaghetti Monster". Yep, there's two Arduinos in there. No, it didn't quite work...

If you're interested in the code running this build, you can view the repository here. It's currently set up for our 16 stair configuration, but only requires a few modifications if you'd like to make your own cascading lights. If you have any questions or issues, feel free to reach out to me at stephen@gidge.dev for assistance.

We're not totally done with this project yet. Up next is to make and mount an enclosure for the circuit so it's not living out in the open forever. Following that our focus will shift to 3D printing a mount for each ultrasonic sensor (well, once the world reopens and we have access to a 3D printer) so we don't have to rely on duct tape indefinitely. We'd also like to explore implementing a real-time clock to keep a single light on overnight.

I may publish a follow-up to this article once the last few loose ends of the project get settled. Until then, if you have any questions feel free to shoot me an email.

Until next time,

Stephen

P.S. Here's one last gif of the lights in action.