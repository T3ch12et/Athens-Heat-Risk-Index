# Athens Heat Risk Index
An interactive map illustrating the intensity of heat across various areas in Athens, Greece. Designed to aid in implementing preventative measures for cooling the city and enhancing its resilience.

**Link to project:** http://recruiters-love-seeing-live-demos.com/

![alt tag](http://placecorgi.com/1200/650)

## How It's Made:

**Tech used:** ArcGIS Pro, ArcGIS Online, ArcGIS Living Atlas of the World, ArcGIS Spatial Analyst extension

The first step is to get the land surface temperature through a Multispectral Landsat imagery layer. It was received from ArcGIS Living Atlas.

Next up was to set the study area to Athens, Greece, zooming to the GRC_Postcodes3 layer, going into the attriubtes layer and filter out postcodes that can skew the data and removed them accordingly. I then used the Copy Features tool to reproduce a copy of the remaining postcodes into a new layer called Athens_Postcodes.

Now it starts the 3 steps process of creating a Heat Risk Index:
The first step is land surface temperature. The Multispectral Landsat layer holds decades  of information for many visualization types, including thermal energy emitted from the earth's surface in two distinct bands. I went the layer properties on the Processing Templates tab and changed it to Band 10 Surface Temperature in Celsius. Went to the Mosaic tab of the layer properties menu and chose the mean option for the mosaic operator. After I went to the Definition Query tab and put in a query statement _Where Cloud Cover is less than or equal to 0.05_. This causes all images with more than 5 percent of cloud cover since the imagery layer contains cloud and cloud shadows that could interfere with the analysis. I then went to the Symbology layer after to change the color scheme and a few settings to symboloize the layer to visualize land surface temperature properly. Areas with cool areas are dark purple while hotter temperature are shown as orange and yellow.

Next up is to define the study area for the land surface temperature input variable. I filtered by extent of the Athens_Postcodes layer with the Multispetral Layer on, then I used the Copy Raster tool to create a new layer based on Athens with the correct settings. The last part is summarizing the temperature values in a table using the Zonal Statistics As Table to create a table with the High Surface Temperature by Postcodes.

The second step is including the tree canopy coverage. I went into ArcGIS Living Atlas and added the European Space Agency WorldCover 2020 Land Cover layer. It shows all geographic areas dominated by trees with a cover of 10 percent or more. Using the Raster Functions tool, the cells are isolated and grouped and then assigns and remaps them into a new value for a new layer to be created. Next up is to calculate tree canopy coverage and set the boundaries to the study area of Athens. I did the same process of utilizing the Copy Raster and Zonal Statistics As Table tools akin to the Multispectral layer with correct settings to create a new raster layer and table to count the number of tree cover cells in each postcode region. I calculated the tree canopy as a percentage by using the Calculate Field tool and created a new field on the table to reflect that as well as percentage of the tree canopy that is lacking using calculations to reflect that.




Here's where you can go to town on how you actually built this thing. Write as much as you can here, it's totally fine if it's not too much just make sure you write *something*. If you don't have too much experience on your resume working on the front end that's totally fine. This is where you can really show off your passion and make up for that ten fold.

## Optimizations
*(optional)*

You don't have to include this section but interviewers *love* that you can not only deliver a final product that looks great but also functions efficiently. Did you write something then refactor it later and the result was 5x faster than the original implementation? Did you cache your assets? Things that you write in this section are **GREAT** to bring up in interviews and you can use this section as reference when studying for technical interviews!

## Lessons Learned:

No matter what your experience level, being an engineer means continuously learning. Every time you build something you always have those *whoa this is awesome* or *wow I actually did it!* moments. This is where you should share those moments! Recruiters and interviewers love to see that you're self-aware and passionate about growing.

## Examples:
Take a look at these couple examples that I have in my own portfolio:

**Palettable:** https://github.com/alecortega/palettable
