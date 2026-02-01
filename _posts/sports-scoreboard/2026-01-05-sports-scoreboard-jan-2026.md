---
title: "LED Matrix Sports Scoreboard — Updates January 2026 (NBA)"
date: 2026-01-05T09:00:00-04:00
show_date: true
header:
  overlay_image: assets/posts/sports-scoreboard/2026-01/ex_nba_game_in_progress.jpg
  overlay_filter: 0.5
  teaser: assets/posts/sports-scoreboard/2026-01/ex_nba_game_in_progress.jpg
  actions:
    - label: "GitHub Repository"
      url: "https://github.com/gidger/rpi-led-sports-scoreboard"
excerpt: "January 2026 updates to the Raspberry Pi LED Sports Scoreboard."
categories:
  - Sports Scoreboard
tags:
  - LED
  - Raspberry Pi
  - Sports
  - NHL
  - NBA
toc: false

---

Woah, a second post in as many months?! Wild, I know...

In the last post, I mentioned that the refactoring efforts laid the foundation to expand functionality to additional sports. Well, that's exactly what happened. The NBA is now supported!

All existing NHL functionality has been created for the NBA. Live scores, next game for your favourite team, and standings! Here's a video of it in action, as well as some additional screenshots.

<iframe width="560" height="315" src="https://www.youtube.com/embed/BjqVBXsv_c8?si=tfnI6bRxXL9TylyE" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe><br>

<figure style="text-align: center;">
  <a href="{{ site.url }}{{ site.baseurl }}/assets/posts/sports-scoreboard/2026-01/ex_nba_fav_team_next_game.jpg">
    <img src="{{ site.url }}{{ site.baseurl }}/assets/posts/sports-scoreboard/2026-01/ex_nba_fav_team_next_game.jpg" style='width: 85%;'>
  </a>
</figure>

<figure style="text-align: center;">
  <a href="{{ site.url }}{{ site.baseurl }}/assets/posts/sports-scoreboard/2026-01/ex_nba_game_in_progress.jpg">
    <img src="{{ site.url }}{{ site.baseurl }}/assets/posts/sports-scoreboard/2026-01/ex_nba_game_in_progress.jpg" style='width: 85%;'>
  </a>
</figure>

<figure style="text-align: center;">
  <a href="{{ site.url }}{{ site.baseurl }}/assets/posts/sports-scoreboard/2026-01/ex_nba_standings_conference.jpg">
    <img src="{{ site.url }}{{ site.baseurl }}/assets/posts/sports-scoreboard/2026-01/ex_nba_standings_conference.jpg" style='width: 85%;'>
  </a>
</figure>

Next up:
- Find an API for the PWHL and implement over the winter.
- Implement the WNBA (shares APIs with the NBA so should be easy) over the winter. The WNBA season doesn't start until the spring, so won't release until then as I want to test with live data.
- Implement MLB in the spring, once spring training has begun. This will require new some new visuals.

You can view all the code for this project, along with installation instructions, at my GitHub Repository [here](https://github.com/gidger/rpi-led-sports-scoreboard).

If you have any questions feel free to shoot me an email at [stephen@gidge.dev](mailto: stephen@gidge.dev).

Cheers,

*Stephen*