---
layout: post
title: Earthquake Tracker - Tableau Dashboard
#@ image: "/posts/<nameoffile>.jpg"
tags: [Tableau, Data Viz]
---

This interactive Tableau dashboard tracks global earthquake activity for a given data set of a 30 day period.

!!!Note: formatting this dashboard has proven difficult to do with the .md file/java/html..., Please click on the "View on Tableau Public" to see the dashboard in full

!! Scroll through each day in the upper right hand slide bar
!! Hover your mouse over the data circles on the map to easily see earthquake information such as magnitude, and location
!! See the earthquake frequency and magnitude of each location for the entire dataset or by day 

___

<div class="tableauPlaceholder" id="viz1785185599814" style="position: relative;">
  <noscript>
    <a href="#">
      <img 
        alt="Earthquake Tracker" 
        src="https://public.tableau.com/static/images/DJ/DJM658XPR/1_rss.png" 
        style="border: none;" 
      />
    </a>
  </noscript>
  <object class="tableauViz" style="display: none;">
    <param name="host_url" value="https%3A%2F%2Fpublic.tableau.com%2F" />
    <param name="embed_code_version" value="3" />
    <param name="path" value="shared/DJM658XPR" />
    <param name="toolbar" value="yes" />
    <param name="static_image" value="https://public.tableau.com/static/images/DJ/DJM658XPR/1.png" />
    <param name="animate_transition" value="yes" />
    <param name="display_static_image" value="yes" />
    <param name="display_spinner" value="yes" />
    <param name="display_overlay" value="yes" />
    <param name="display_count" value="yes" />
    <param name="language" value="en-US" />
  </object>
</div>

<script type="text/javascript">
  var divElement = document.getElementById('viz1785185599814');
  var vizElement = divElement.getElementsByTagName('object')[0];

  if (divElement.offsetWidth > 800) {
    vizElement.style.width = '100%';
    vizElement.style.height = (divElement.offsetWidth * 0.75) + 'px';
  } else if (divElement.offsetWidth > 500) {
    vizElement.style.width = '100%';
    vizElement.style.height = (divElement.offsetWidth * 0.75) + 'px';
  } else {
    vizElement.style.width = '100%';
    vizElement.style.height = '1427px';
  }

  var scriptElement = document.createElement('script');
  scriptElement.src = 'https://public.tableau.com/javascripts/api/viz_v1.js';
  vizElement.parentNode.insertBefore(scriptElement, vizElement);
</script>
___

# **Data disclaimer**: This earthquake data in this dashboard is not realistic whatsoever. The frequency of high magnitude quakes are drastically exagerated to provide diverse datapoints to demonstrate data vizulization.

# Fun Fact(s): 
* The greatest magnitude of an earthquake recorded was in Chili in 1960 at a magnitude of 9.5. 
* Earthquakes cannot exceed a magnitude of 10 because no tectonic fault line is long enough to produce one. A magnitude 10 earthquake would require a fault wrapping all the way around the equator
* The USGS (United States Geological Survey) estimates an average of 16 major earthquakes per year, with a magnitude of 7.0 or higher 

# to do!! 
* fix viz (how it's formatted on the gitpage)
* deeper description of what the dashboard entails
* upload image of dashboard for main page
