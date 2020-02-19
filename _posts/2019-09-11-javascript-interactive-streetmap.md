---
layout: post
title: Interactive street maps in JavaScript
---

During summer of 2019, my then-girlfriend and I started looking at buying a house. Due to Seattle's [infamously hot housing market](https://seattlebubble.com/blog/2018/04/19/reader-comment-now-all-i-seem-to-be-able-to-afford-are-the-meth-houses/), we ended up looking at >30 houses before making an offer. The geek in me saw this as an opportunity to do some 
mapping and visualization, and also learn some new technologies.

I imagined an interactive map that would show the location of each house we looked at, along with metadata so we could potentially look at trends. I was hoping to use open-source data, rather than GoogleMaps which require an API key.

### 1. Choose the right technology

Since my map would be web-based and interactive, I thought React would be a good fit. I found a few different mapping solutions: [google-map-react](https://www.npmjs.com/package/google-map-react) and [react-map-gl](https://uber.github.io/react-map-gl). In the end, using React just to make a clickable map seemed a little overkill to me, especially since [Leaflet](https://leafletjs.com/) already supported some interactivity.  

### 2. Clean the data

The last time I worked with maps, it was on a [larger scale](https://github.com/ptvan/nutria2007) and I didn't have to worry about street addresses. Mapping street address to geographical coordinates ("geocoding") can get a little complicated. Thankfully, since it's a fairly common problem, there are tons of tools available. I naturally gravitated towards R, where there are some excellent packages like [tmap](https://github.com/mtennekes/tmap) and [tmaptools](https://github.com/mtennekes/tmaptools). These combined with [OpenStreetMap](https://www.openstreetmap.org)'s API gave me latitudes and longitudes of the houses in a few minutes. As I do with all datasets, I also did a bit of [exploratory data analysis](https://github.com/ptvan/python-snippets/blob/master/cozycottage_EDA.ipynb).

### 3. Pick the path of least resistance

In looking for ways to load my coordinates into the webpage, I again became cursed with options: there are simply [too](https://www.js-tutorials.com/jquery-tutorials/reading-csv-file-using-jquery/). [many](https://www.papaparse.com/). [solutions](https://www.quora.com/What-is-the-best-way-to-read-a-CSV-file-using-JavaScript-not-JQuery). Could a guy just not have an `open()` call ? In any case, I settled on using [D3](https://github.com/d3/d3-dsv), which had a simple 2-line solution.

### 4. Minimally viable product

![CozyCottage screenshot](/images/cozycottage_screenshot.png "cozycottage_screenshot.png")

So, you can see the MVP, which I call CozyCottage [here](https://github.com/ptvan/cozycottage). In the end, I couldn't shake the reliance on JavaScript-everywhere (ie. you still have to serve the resultant HTML with some kind of server), but it was the quickest, least cumbersome way I found to do what I set out to do.

Funnily enough, making an interactive map using D3, a library known for its visualization, can get rather [involved](https://bl.ocks.org/mbostock/2522624ada2c1f9e0fafb75cca09442b).
