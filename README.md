# Analysis of [**Mapping Police Violence**](https://mappingpoliceviolence.org/) Web Map

## GEOG 458 - Final Essay
### Tom Truong

![Screen Cap](https://mappingpoliceviolence.org/s/mpvmap2.png)
*A screen capture of the main web map on the website.*
---
#### Introduction

In light of [**current events** in America](https://en.wikipedia.org/wiki/Killing_of_George_Floyd) right now, I would like to critique a web map reporting on police brutality in the past year of 2019. To further educate myself on this pertinent issue like many others at this time, the goal of this project is to [*"provide greater transparency and accountability for police apartments"*](https://mappingpoliceviolence.org/aboutthedata) in hopes to end police violence within communities. When it's unclear if police departments comply to mandating this information to the public, especially in a timely manner, this uncomplete database is compiled to make various visuals.

The major functions of this web map are a **continuous timer** that plots new marker points that corresponds to the date the incident happened on the map. Each **marker point** is clickable and provides primary information about the supposed victim; the location, description, news article, and result of the respective incident. For better viewing purposes, **zoom** and **full screen** options are provided along with being able to **share** on social media.

The target audience is the general public, possibly ranging from *people who like to become more aware of this matter* to *vulnerable people in certain ethnic groups or communities* that are affected disproportionately by police violence. The authors are [**Samuel Sinyangwe**](https://twitter.com/samswey) and [**DeRay McKesson**](https://twitter.com/deray) who are both African American activists and community organizers, along being data scientists for this project.


#### Systematic Architecture

The operations of the **client workstation** is to collect data points from the data sources that send from a web/geospatial server to two seperate file and database servers, to plot on the web map. The corresponding **web servers** gathers data from web clients, with the prominent ones being [*FatalEncounters.org*](https://fatalencounters.org/) and [*KilledbyPolice.net*](https://killedbypolice.net/). These sites provide databases that includes both geospatial and categorized data. Both of this data is collated into the Mapping Police Violence database, that is also manually evaluated through **secondary sources** such as *social media*; *obituaries, criminal records, and police report* databases. This is mainly to identify the race of the victims, which can provide major overarching results during data analysis.

The geospatial services that provide the web map functionality are: [**OpenStreetMap**](https://www.openstreetmap.org/copyright), [**MapTiler**](https://www.maptiler.com/copyright/), [**CARTO**](https://carto.com/attribution), and respective contributors from OpenStreetMap. CARTO provided the basemap which seems to be a dark map with labels. The vector marker points that are plotted throughout the map is powered by MapTiler with corresponding details from the database provided as a clickable, hosted by **Mapbox SDK** to allow the functionality of the vector tiles. Lastly, OpenStreetMap provides the interactive elements including draging, zooming, temporality, and the option to query data. The data itself is from a compiled database as a collaborative effort in the format of a CSV. The three main data tables from the database is listed to be the **2013-2019 Killings by Police Department**, **2013-2019 Killings by State**, and **Police Killings of Black Men.**


#### Inspecting the Code

The data that is flowed in between the client and server is the dedicated full database that the authors compiled, that I mentioned earlier. From their dedicated database server, it is able to plot points on the web map based on temporality and also dynamically generate some of the data visualizations at the bottom; such as bar charts, plot graphs, and bubble charts. Some of the visualizations itself are pre-generated and published as an image file, as it might have required tools and libraries beyond the ones used for the live server. Most of the data is collated from the two external database sites I mentioned earlier.

**Major Libaries Used and Their Functions**
- *Piktochart*: This library was used to generate and embed some of the data visualizations into infographics displayed under the web map. The visualization formats such as the **line plot** and the **statistical visualization** using the imagery of human bodies were used. This was used to aggregate the various details of the collective police violence incidents.
- *Google Analytics*: This JavaScript library was used for a data analytic tool to analyze the visitor's of this website activity. Through monitoring the **page and interactive requests** by the users, the authors can see which elements on their page is most prevalent and useful for users.
- *D3*: This other JavaScript library is used to use the website elements to create **data-driven** representations that can be viewed as documents on the website. It also provides the interactive and animated elements of the visualizations that website visitors can interact with.

This project **does support responsive design** as through the *Device Toolbar* function on Google Chrome Inspect, the whole site was able to adapt and shape to various variables such as **resolution**, **devices**, **orientation**, **zoom**, and **network availability**. I was able to confirm this test by viewing the site on my *iPhone 11* using Google Chrome.


#### Data Sources

| Vectors | Rasters |
| GeoJSON elements to plot the points onto the map and embed the details as a clickable overlay | |MapTiler elements to generate the raster tiles on the map, to allow for use of Leaflet and such |

Overall, I think the **UI/UX** experience diplayed on this website is visually sound and provides enough to get the point across. The use of plain text is great, especially not to take attention away from the main infographics and visualizations that should be the vocal point to the audience. I think the use of coloring and orientation of the visuals is fine, but could be better if it was intergrated into a *smart dashboard* on the side and could work dynamically along with the web map too. Unfortunately, the web map and infographics are two seperate entities giving the web map limited functionality.
In terms of the **Web Mapping design**, I think it does fine for the one function it serves, which is to display the plot points of police violence incidents along the locations of the US depending on the date. The simplicity of the web map elements is enough for its limited functionality and it doesn't take away from the main purpose of the map, which is to display each incident on the map formally.


#### Map Elements

The **basemap** is a nice *Dark Matter* map with labels that provides *geographic context* of the map. From state to county to city to neighborhood level, this whole basemap successfully displays all levels of space in the United States. That is crucial for this sensitive type of data, since location is critical in terms of jurisdictions and giving accountability to respective police departments.

In terms of **thematic layers**, there doesn't seem to display any layer on top of the basemap. The use of a thematic layer would have been beneficial for this web map to show the **density of police violence incidents** within city or county boundaries, or even at a state level. But, it seems that data aggregation can be visualized in one of the data visualizations by different categorizes, but not on a geospatial level on a map.

For the **interactive features** besides the typical **zoom in/out** functionality, there seems to be absence in other map elements such as a **scale bar**, a **compass rose**, or a **legend**. The main interactive feature is the **timeline bar** that is looping through all calendar dates in the year 2019 as points are being plotted on the map. It provides a **play/pause** button and a **slider** for the looping bar that can be scrubbed to a certain date.

`<ul>    <li class="controls"><a href="#/pause" class="button stop">pause</a></li>   <li class="time"><p class="value">08/06/2019</p></li>   <li class="last"><div class="slider-wrapper"><div class="slider ui-slider ui-slider-horizontal ui-widget ui-widget-content ui-corner-all"><div class="ui-slider-range ui-widget-header ui-slider-range-min" style="width: 59.8826%;"></div><a class="ui-slider-handle ui-state-default ui-corner-all" href="#" style="left: 59.8826%;"></a></div></div></li> </ul>`
*HTML code of the temporal slider while its looping through the web map.*

**Web Map Elements Used**
- Zoom In/Zoom out
- Toggle Full Screen
- Query Search Bar
- Clickable Plot Points with Overlay Information
- Embedded Sharing Option for Social Media and Linking
- Temporal Timeline Bar with Play/Pause Button, Date Display, and Scrubber Sider for dates


#### Strengths and Weaknesses

The **strengths of this overall project** are that it is sufficent and efficient with their use of elements to convey their message effectively. To get the point across that People of Color victims, especially African American, are disproportionately killed by the fate of police violence (especially unarmed) the use of the web map and infographic elements strongly supported their claim and message.

What I can see as the **weaknesses of this project** are that the web map and visualizations work as two different entities. So it would be hard to correlate the data visualizations spatially on the web map, which would be more helpful. If interactions with the visuals could dynamically influence what is displayed on the web map, the audience could have a clearer image of the data.


#### Social Implications

Finally, in terms of **social theories**, I think this project does its best to adapt and accommodate for that. Especially with **digital divide**, which minority and older groups would likely have less accessibility to a device and network capability. The acknowledgement of this social issue is crucial for the mission of this project because it informs the results of police violence data that affects minority and older groups the most. The application is able to be adaptive to various stationary and mobile devices ranging from all performance value and the website can be viewed offline, since everything is pre-rendered and just needs an initial connection to a network for it to display.

For **resistance** purposes, this project helps a lot with informing the public about police brutality activity and giving them an informed decision in terms of protest for possible reform in our policing. This project supports social activism from this data being compiled and available to the public, which is something uncomfortable to address even at a police department level. This could evoke dialog of what could classify as a justifiable or abuseful use of police force based on the data that is collated from multiple sources. Projects like this provide opportune information that prevalent in our current civil climate as many major US cities are transitioning and reforming to prevent anymore tragedies that could cause more outrage.
