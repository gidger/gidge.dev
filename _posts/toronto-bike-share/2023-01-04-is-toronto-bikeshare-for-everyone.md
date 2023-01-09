---
title: "Is Toronto Bike Share for Everyone?"
date: 2022-12-30T04:00:00-04:00
show_date: true
header:
  overlay_image: assets/posts/toronto-bike-share/header.jpg
  overlay_filter: 0.5
  teaser: assets/posts/toronto-bike-share/header.jpg
  actions:
    - label: "Live Report"
      url: "https://app.powerbi.com/view?r=eyJrIjoiNzE4ZDAwMTgtMTU2Yy00NzUzLTk4NGYtZGFjZWQ3Y2E1M2IyIiwidCI6IjNmN2FhNDA3LTJjY2EtNDI5YS04MzhlLTY0N2IxOTRlMDJiOCJ9"
excerpt: "A visual analysis of Toronto's Bike Share & cycling infrastructure"
categories:
  - Toronto Bike Share
tags:
  - Data Visualization
  - Sports
  - Power BI

---

<b>TL;DR</b> analysis of Toronto's Bike Share & cycling infrastructure using Power BI – see interactive report below.

<figure style="margin: auto;">
  <iframe title="Is Bike Share for Everyone" width="800" height="420" src="https://app.powerbi.com/view?r=eyJrIjoiNzE4ZDAwMTgtMTU2Yy00NzUzLTk4NGYtZGFjZWQ3Y2E1M2IyIiwidCI6IjNmN2FhNDA3LTJjY2EtNDI5YS04MzhlLTY0N2IxOTRlMDJiOCJ9" frameborder="0" allowFullScreen="true">
  </iframe>
  <figcaption style="text-align: left;">
    <i>Be sure to view in full screen (button in bottom right) for the best experience.</i>
  </figcaption>
</figure><br>

This past fall I spent some time looking into Toronto’s Bike Share and cycling infrastructure networks. This research culminated into the report you see above.

Some background – I am passionate about cycling, riding nearly every day for most of the year as my primary source of transportation. As such, cycling infrastructure is of huge importance to me, as is getting more people riding during this ongoing global climate emergency.

But that’s not <i>really</i> why I started this project. 

In reality, I wanted to learn more about effectively using geospatial data. I had never worked with geospatial data in the past, and this seemed like a great way to get started, as well as dive into a topic that I’m truly interested in. Wrap it all up in a public facing Power BI report and here we are!

For those unaware, Bike Share Toronto allows users 24/7 access to a fleet of rental bicycles designed for short trips within the city. A user can rent a bike from any station (or dock) and return it to any station within the network.

<div style="margin: auto; width: 85%;">
  <figure>
    <a href="{{ site.url }}{{ site.baseurl }}/assets/posts/toronto-bike-share/rider-station.jpg">
      <img src="{{ site.url }}{{ site.baseurl }}/assets/posts/toronto-bike-share/rider-station.jpg" >
    </a>
    <figcaption style="text-align: left;">
      <b>Foreground</b>: Rider on Bike Share bike.<br>
      <b>Background</b>: Bike Share docking station.<br>
      <b>Source</b>: <a href="https://signalhfx.ca/toronto-bike-sharing-trips-have-surged-during-covid-19/">The Signal</a>. Photo by <b>Robyn Miyuki Hughes</b>.
    </figcaption>
  </figure>
</div>

My goals for this project (besides learning more about the wild world of geospatial data) were pretty simple:
1. Visualize and identify areas where the Bike Share network is underdeveloped.
2. Visualize and identify gaps within the Toronto cycling network, especially when it comes to safe, protected infrastructure.
3. Allow a user to explore neighbourhoods that are underserviced within each network, and analyze them from the lens of income, etc.

Ultimately, I wanted a user to be able to visually explore both networks and see for themselves the clear gaps that exist (especially outside of the borough of Old Toronto). I won’t push my agenda or findings any further here – if you haven’t already, explore the report above and come to your own conclusions. I’m sure you’ll discover something that you find interesting.

<div style="text-align: center;">
  <i>*cough*</i> Look at cycle tracks in Scarborough. <i>*cough*</i><br><br>
</div>

As for the data feeding this report, all of it came from the Toronto Open Data Portal. Data was collected on the following topics (hyperlinks to the data sources):
- [Bike Share Station Info](https://open.toronto.ca/dataset/bike-share-toronto/) & [Locations]()
- [Bike Share Usage](https://open.toronto.ca/dataset/bike-share-toronto-ridership-data/)
- [Cycling Infrastructure Shapes](https://open.toronto.ca/dataset/bikeways/)
- [Census Statistics by Social Planning Neighbourhood](https://open.toronto.ca/dataset/neighbourhood-profiles/)
- [Social Planning Neighbourhood Shapes](https://open.toronto.ca/dataset/neighbourhoods/)

One of the main challenges of this project was figuring out how to slice the data by social planning neighbourhood. These neighbourhoods are the way the Toronto city government divides the city’s area for urban planning purposes. Unfortunately, neither the Bike Share station locations, nor the cycling infrastructure datasets included these neighbourhoods. To remedy this, I used the GeoPandas Python package to perform a spatial join and map stations and infrastructure into their respective neighbourhoods.

Without getting into unnecessary details on the data used or cleansing performed, you can see a high level visual depicting the data transformations below.

<div style="margin: auto; width: 95%;">
  <figure>
    <a href="{{ site.url }}{{ site.baseurl }}/assets/posts/toronto-bike-share/data-transformation.png">
      <img src="{{ site.url }}{{ site.baseurl }}/assets/posts/toronto-bike-share/data-transformation.png" >
    </a>
    <figcaption style="text-align: left;">
      <i>Click to enlarge.</i>
    </figcaption>
  </figure>
</div>

It wouldn’t be fair for me to end this post without mentioning Bike Share Toronto’s [Four-Year Growth Plan](https://parking.greenp.com/app/uploads/2022/09/BikeShareToronto_FYGP_wAppendix.pdf) that was unveiled as I was finishing up this project. Many of the key takeaways I wanted a user to come away with are being addressed by this plan. People with more time, resources, and knowledge than myself created it and I highly recommend checking it out if you have any interest in cycling within Toronto.

Additionally, you’ll notice in my Power BI report, the city is split into 140 social planning neighbourhoods. As of Spring 2022 there are now 158 neighbourhoods as the City divided some up into smaller areas as their populations grew. As of when I was building my report, the City hasn’t released compiled census data for the new set of neighbourhoods. As a result, you’ll see 140 neighbourhoods and demographic data from the 2016 census.

If you’re interested in making cycling a safe and accessible option for the thousands of Torontonians in which it is not, check out the final page of my report above. Also, let your [City Councillor](https://www.toronto.ca/city-government/council/members-of-council/) know that safe cycling inftastructure is important to you, and consider donating time or money to advocacy groups such as [Cycle Toronto](https://www.cycleto.ca/) who do great work in this space.

If you have any questions about this project, feel free to shoot me an email at [stephen@gidge.dev](mailto: stephen@gidge.dev). Also, if you’re interested in a deeper dive of the data, how this report works, or the message I want to convey, please reach out – I'm happy to chat more. I hope this makes you really think about factors that affect cycling accessibility in cities. Thanks for reading!

Cheers,

*Stephen*