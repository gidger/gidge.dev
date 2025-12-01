---
title: "LED Matrix NHL Scoreboard — Updates November 2025"
date: 2025-11-28T09:00:00-04:00
show_date: true
header:
  overlay_image: assets/posts/nhl-scoreboard/2025-11/ex_nhl_fav_team_next_game.jpg
  overlay_filter: 0.5
  teaser: assets/posts/nhl-scoreboard/2025-11/ex_nhl_fav_team_next_game.jpg
  actions:
    - label: "GitHub Repository"
      url: "https://github.com/gidger/rpi-led-nhl-scoreboard"
excerpt: "November 2025 updates to the Raspberry Pi LED NHL Scoreboard."
categories:
  - NHL Scoreboard
tags:
  - LED
  - Raspberry Pi
  - Sports
toc: false

---

Hey there, long time no post... Anyhow, I'm alive and here's some updates on the NHL LED Scoreboard project.

Over the last month, I've refactored the entire solution, added new functionality, and laid the foundation to expand it to additional sports.

Here's some of the new features:
- Installation has moved to Docker, greatly simplifying the install and setup process.
- You'll now have the ability to set a favourite team and see that team's next game.
- You can view standings for any combination of wildcard, division, conference, or overall.

<iframe width="560" height="315" src="https://www.youtube.com/embed/dtqFqR9JHCA?si=C9POcf6CL1PxFehB" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe><br>

<figure style="text-align: center;">
  <a href="{{ site.url }}{{ site.baseurl }}/assets/posts/nhl-scoreboard/2025-11/ex_nhl_fav_team_next_game.jpg">
    <img src="{{ site.url }}{{ site.baseurl }}/assets/posts/nhl-scoreboard/2025-11/ex_nhl_fav_team_next_game.jpg" style='width: 85%;'>
  </a>
</figure>

<figure style="text-align: center;">
  <a href="{{ site.url }}{{ site.baseurl }}/assets/posts/nhl-scoreboard/2025-11/ex_nhl_standings_wildcard.jpg">
    <img src="{{ site.url }}{{ site.baseurl }}/assets/posts/nhl-scoreboard/2025-11/ex_nhl_standings_wildcard.jpg" style='width: 85%;'>
  </a>
</figure>

I'll write here more often as the project progresses. Some planned upcoming functionality includes:
- Expanding to additional sports. Current plan is to integrate the NBA in the winter, and MLB in the spring. American football is dumb, so someone else can tackle that one. Open source, hurrah!
- Add in a "leaders" scene, showing the goal/point/whatever leaders for a league.
- Create a local web app to configure settings via a GUI rather than manually editing config.yaml.

You can view all the code for this project, along with installation instructions, at my GitHub Repository [here](https://github.com/gidger/rpi-led-nhl-scoreboard).

If you have any questions feel free to shoot me an email at [stephen@gidge.dev](mailto: stephen@gidge.dev).

Cheers,

*Stephen*