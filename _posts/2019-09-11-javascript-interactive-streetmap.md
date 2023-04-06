---
layout: post
title: Interactive street maps in JavaScript
---

During summer of 2019, my then-girlfriend (now wife) and I started looking at buying a house. Due to Seattle's [infamously hot housing 
market](https://seattlebubble.com/blog/2018/04/19/reader-comment-now-all-i-seem-to-be-able-to-afford-are-the-meth-houses/), we ended up looking at >30 houses before making an offer. The geek in me saw this as an opportunity to do some 
mapping and visualization, and also learn some new technologies.

The last time I worked with maps, it was on a [larger scale](https://github.com/ptvan/nutria2007) and I didn't have to worry about street addresses. This time, I imagined an interactive map that would show the location of each house we looked at, along with metadata so we could potentially look at trends. I was also interested in using open-source mapping service, rather than GoogleMaps.

### 1. Choosing a JavaScript mapping framework

Since my map would be web-based and interactive, I thought [React](https://react.dev/) would be a good fit since it's a widely used JavaScript framework with a few different mapping solutions: [google-map-react](https://www.npmjs.com/package/google-map-react) and [react-map-gl](https://uber.github.io/react-map-gl). After some digging, however, using React just to make a clickable map seemed a little overkill to me. I settled on [Leaflet](https://leafletjs.com/) which was lighter weight and also supported some interactivity.  

### 2. Choosing an (open-source) mapping service

Next, I looked into several services providing open-source mapping data: [OpenStreetMap](https://www.openstreetmap.org) and [MapBox](https://www.mapbox.com/), which has a free tier, ultimately settling on the former since I didn't need MapBox's more advanced features.

### 3. Performing geocoding

 Mapping the street addresses I have to geographical coordinates ("geocoding") can get a little complicated. Thankfully, since it's a fairly common problem, there are tons of tools available. I naturally gravitated towards R, where there are some excellent packages like [tmap](https://github.com/mtennekes/tmap) and [tmaptools](https://github.com/mtennekes/tmaptools). These combined with OpenStreetMap's API gave me latitudes and longitudes of the houses in a few minutes. As I do with many new datasets, I also did a bit of [exploratory data analysis](https://github.com/ptvan/python-snippets/blob/master/cozycottage_EDA.ipynb).

### 4. Reading geocoded data into framework

In looking for ways to load my coordinates into the webpage, I again became cursed with options: there are simply [too](https://www.js-tutorials.com/jquery-tutorials/reading-csv-file-using-jquery/). [many](https://www.papaparse.com/). [solutions](https://www.quora.com/What-is-the-best-way-to-read-a-CSV-file-using-JavaScript-not-JQuery). Could a guy just not have an `open()` call ? In any case, I settled on using [D3](https://github.com/d3/d3-dsv), which had a simple 2-line solution.

### 5. Host the results and test

![CozyCottage screenshot](/images/cozycottage_screenshot.png "cozycottage_screenshot.png")

Lastly, though JavaScript itself started out being client-side, the mapping API calls means that I still need to have a HTTP server that could host the final prototype. Since this was just a fun personal project, I opted to forego an ISP and just run my [own personal HTTP server on the source directory](https://gist.github.com/willurd/5720255) using python3's `http.server` module.

You can see the source for this project, which I call CozyCottage [here](https://github.com/ptvan/cozycottage). I took a screenshot above in case the mapping API changed (which it did a while after I originally made this post).
