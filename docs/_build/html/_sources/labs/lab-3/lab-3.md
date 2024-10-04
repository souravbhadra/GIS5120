# Lab 3: Rediscovering Trails in National Parks (10 pts)

## Read before proceeding

- The questions for this lab are embedded within the instructions.
- Each question carries specific points, clearly indicated alongside it.
- The questions might have subsections within them.
- The total score for this assignment is 10 points. Your final grade will be scaled from the total points you earn out of the maximum possible score to fit within a 0 to 10 scale.
- When working on a lab, always create a dedicated folder for it and store all related files within that specific folder. For instance, avoid saving intermediate files in the `C:/Documents` directory; keep all materials organized and together.
- Create a word document and name it as `Lab-3-answers-YOURLASTNAME.docx`. Insert each questions provided in this document and write down your answers for each questions. Upload the `.docx` file in Canvas. Do NOT upload a `.pdf` of the document.
- Upload any additional file(s) required by this instructions in Canvas. You will find specific list of deliverables at the end of this page.
- You do not have to upload any large ArcGIS Pro Project (`.asprx`) file unless explicitly mentioned in the instructions.

## Due Date

Oct 3, 2024 10:00 PM CDT

## Background

The natural landscapes of national parks offer a unique blend of topographical diversity and ecological richness. Trails winding through these parks often lead to high vantage points that provide breathtaking views and immersive experiences in nature. Understanding these landscapes requires an integration of various geospatial analyses to assess both the physical terrain and the ecological attributes.

In this lab, you will analyze hiking trails to identify those with the highest average slope and the highest peaks. Slope is a critical factor in assessing trail difficulty, as trails with greater slopes require more physical effort and can be more challenging for hikers. Trails that reach high elevations provide scenic views but may also be more strenuous. By analyzing slope and elevation data along the trails, you will determine which trails are the steepest and which lead to the highest points, helping to evaluate their difficulty and appeal for different types of users.

We will be working with Rocky Mountain National Park in Colorado. One of my personal favorites.

```{figure} fig-3-1.png
---
name: fig-3-1
---
Rocky Mountain National Park Official Map
```

## Setup ArcGIS Project

Create an ArcGIS Porject file in your lab directory named as `Rocky_Mountain`.

## Download the data

You will have to download your own data. Followings are the steps to download your data. We will download Rocky Mountain National Park boundary, trail, and corresponding DEM data.

1. Go to [https://public-nps.opendata.arcgis.com/](https://public-nps.opendata.arcgis.com/), click the search button on the top right corner and type "rocky mountain national park boundary".

    ```{figure} fig-3-2.png
    ---
    name: fig-3-2
    ---
    NPS website
    ```

2. Click the `Rocky Mountain National Park - Boundary Polygon` and download it as a Shapefile in your Lab 3 `data` directory.

   ```{figure} fig-3-3.png
    ---
    name: fig-3-3
    ---
    RMNP Boundary shapefile
    ```

    ```{figure} fig-3-4.png
    ---
    name: fig-3-4
    ---
    RMNP Boundary shapefile download
    ```

3. Go to [https://public-nps.opendata.arcgis.com/](https://public-nps.opendata.arcgis.com/) one more time, click the search button on the top right corner and type "rocky mountain national park trails". You should see a `Rocky Mountain National Park - Trails` label and download it as a shapefile.

    ```{figure} fig-3-5.png
    ---
    name: fig-3-5
    ---
    RMNP Trails shapefile download
    ```

4. Go to [https://apps.nationalmap.gov/downloader/](https://apps.nationalmap.gov/downloader/), which is the official site to download USGS open source data. Here you can find a lot of good curated dataset published and/or maintained by USGS. We want to download the Digital Elevation Model (DEM) products from here.

    ```{figure} fig-3-6.png
    ---
    name: fig-3-6
    ---
    The National Map Downloader
    ```

5. There are multiple ways to download data, i.e., Extent (whatever extent the map is in the right side section), Polygon (you can upload your own polygon), Point, Enter Coords (the extent of your area of interest). We will use the `Enter Coords` option to insert the RMNP boundary extent information.

    ```{figure} fig-3-7.png
    ---
    name: fig-3-7
    ---
    Extent window
    ```

6. Now go to you ArcGIS Pro project and click the properties of the `Boundary_(Polygon)` (which is the RMNP boundary) layer. To find the Extent of this layer, click `Source` on the left side pane, and then click `Extent`. You will see that the Extent information (Top, Bottom, Left, Right) are available in meters as the layer is in a projected coordinate system. On the other hand, the National Map requires the extent to be in geographic coordinate system or latutide/longitude values rather than meters. Therefore, we need to change the projection of this layer to a geographic coordinate system. Find the **Project** tool in the Geoprocessing tools and create a feature class named as `Boundary_Polygon_GCS` in the project geodatabase with `GCS_WGS_1984` system. Click the little globe icon in the `Output Coordinate System` parameter and select `WGS 1984` from the `Geographic Coordinate System` options.

    ```{figure} fig-3-8.png
    ---
    name: fig-3-8
    ---
    Projecting boundary polygon
    ```

    ```{figure} fig-3-9.png
    ---
    name: fig-3-9
    ---
    Finding WGS coordinate system
    ```

7. Now open the properties of `Boundary_Polygon_GCS` layer and locate the `Extent`. Make sure it matches with the following information.

    ```{figure} fig-3-10.png
    ---
    name: fig-3-10
    ---
    RMNP Extent
    ```

    Top: 40.553794
    Bottom: 40.158073
    Left: -105.913724
    Right: -105.493594

8. In your browser, clear the Extent window if it was open. First, select the dataset we need to download. We will be downloading a 10-m resolution DEM from USGS, which is a very common and good DEM data within US. However, the 10-m resolution is an approximation from 1/3 arc second resolution. Check the `Elevation Products (3DEP)` in the left side pane on the `Data` section, then select the `1/3 arc-second DEM` (`Current`).

    ```{figure} fig-3-11.png
    ---
    name: fig-3-11
    ---
    Selecting data
    ```

9. Now, we need to provide the Extent information. Make sure the Extent information of your RMNP Boundary in geographic coordinate system is handy in ArcGIS Pro. Then clicl the `Enter Coords` button on the `Area of Interest` section of the window on the left. Now provide the extent information correctly with absolute precision. The Xmax, Xmin, Ymax, Ymin are actually Right, Left, Top, and Bottom, respectively in terms of ArcGIS Pro's Extent information. It should look like below and once you are satisfied, click `Add to Map`.

    ```{figure} fig-3-12.png
    ---
    name: fig-3-12
    ---
    Providing extent information
    ```

10. After adding the extent, there will be a AOI drawn on the right side map. If it makes sense, click `Search Products`.

    ```{figure} fig-3-13.png
    ---
    name: fig-3-13
    ---
    Showing extent on the map
    ```

11. There should be one product as the result. Make sure it matches with the following. Click ``Download Link (TIF)` to download it as a tif file. You can also clik `Footprint` to see the footprint of the DEM on the right map, click `Zoom To` to interact with the DEM on top of the topographic basemap. Download the DEM in your `data` directory.

    ```{figure} fig-3-14.png
    ---
    name: fig-3-14
    ---
    Search results of DEM
    ```

## Workflow using ArcGIS Pro

### Explore the datasets

1. Insert the RMNP Boundary shapefile that you downloaded.

    ```{admonition} Question 1
    :class: note

    a. What is the total area of the RMNP in Square Kilometers? ***<1 pt>***  
    ```

2. Insert the RMNP Trails shapefile you downloaded.

    ```{admonition} Question 2
    :class: note

    a. What is the total length of trails in Miles within RMNP? ***<1 pt>***  
    b. How many unique trails are within RMNP? (Hint: if you examine the `TRLNAME` column, you will find that there are some Polylines with same `TRLNAME`. Therefore, you need to do `Dissolve` of the `TRLNAME` so any trail with same name will be merged together. While doing so, also calculate the `Sum` statistic of the `Length_Mile` field, so you get the total length of each unique trail in Miles.) ***<3 pt>***  
    c. Which trail is the longest and what is its length? (Hint: Remember to use the dissolved trail feature) ***<2 pt>***  
    d. What is the mean and median length of trails in RMNP? (Hint: Remember to use the dissolved trail feature) ***<2 pt>***  
    e. Is the distribution of trail length normal or skewed? If skewed, positive or negative? (Hint: Remember to use the dissolved trail feature) ***<2 pt>***  
    ```

3. Insert the `USGS_13_n41w106_20230314.tif` you downloaded. Explore the DEM. Look at its values in the table of contents which is in Meters. Let's convert this to Feet. The conversion formula for meter to feet is to multiply the raster data by a constant value of `3.28084`.

    ```{admonition} Question 3
    :class: note

    a. Create a DEM where the unit of the elevation is in Feet. Save it in the default geodatabase without mentioning any file extension. This will create a native ESRI Grid format raster data. (Hint: Use Raster Calculator from Spatial Analyst extension) ***<3 pt>***  
    b. What is the maximum and minimum value of the elevation for this entire raster in Feet?***<3 pt>***  
    ```

### Clip the DEM to analysis boundary

Since the DEM is quite larger than the RMNP boundary, we do not need the entire DEM for our analysis. Therefore, it is better to clip or mask the DEM by the RMNP boundary extent. To do this, find the **Clip Raster** tool and use the `Boundary_(Polygon)` as the Output Extent to clip the `DEM_Feet` raster. Make sure the output data is saved in the default geodatabase as `DEM_Feet_Clip`. Also check the `Maintain Clipping Extent` at the end.

```{figure} fig-3-15.png
---
name: fig-3-15
---
Clip raster
```

### Find the peak points within trail lines

To find the highest/peak points within the trails, we can use many different approaches. Here is a simple approach:

- First, we can generate equal distant points on top of the line(s)
- Then, we use those points to extract the elevation values from the DEM
- Once we know the elevation of each points, we can find the maximum value for each trails
- Then we filter out the top 5 peak points to calculate viewshed.

1. Find the [Generate Points Along Lines (Data Management Tools)](https://pro.arcgis.com/en/pro-app/latest/tool-reference/data-management/generate-points-along-lines.htm). Use `Trail_Dissolve` as the `Input Features`, name the `Output Feature Class` as `Trail_Points` within the default geodatabase, use `10 Meters` as the `Distance` as we know that the USGS DEM is 10 m resolution. Approximating 10 meters interval points will be good enough for our analysis. If you want more precision, you can use smaller number but for this lab, let's stick to 10 meters. Makse sure to check the `Include end points` so the starting and ending points are also included in the results.

    ```{figure} fig-3-16.png
    ---
    name: fig-3-16
    ---
    Generate points along lines
    ```

    ```{admonition} Question 4
    :class: note

    a. How many points you got? (Hint: it should be 54,070 points, if not, something was wrong in your previous steps) ***<1 pt>***  
    ```

2. Find the [Extract Values to Points (Spatial Analyst Tools)](https://pro.arcgis.com/en/pro-app/latest/tool-reference/spatial-analyst/extract-values-to-points.htm). Use the `Trail_Points` as the `Input point features`; `DEM_Feet_Clip` as the `Input raster`; name the `Output point features` as `Trail_Points_Elevation` in the deafault geodatabase.

    ```{figure} fig-3-17.png
    ---
    name: fig-3-17
    ---
    Extract values to points
    ```

3. Explore the `Trail_Points_Elevation` feature's attributes. See that there is an attribute called `RATERVALU` which includes the elevation in feet underneath each point. Now we need to find out the highest point within each trail.

4. We can use the [Dissolve (Data Management Tools](https://pro.arcgis.com/en/pro-app/latest/tool-reference/data-management/dissolve.htm) to aggragte unique `TRLNAME` within each points. Use the following parameters in the **Dissolve** tool. Make sure you are calculating the `Maximum` `RASTERVALU` as the `Statistics Fields` and the `Dissolve Fields` is the `TRLNAME`.

    ```{figure} fig-3-18.png
    ---
    name: fig-3-18
    ---
    Dissolve points
    ```

5. Explore the attribute table of the `Trail_Points_Elevat_Dissolve` feature. See that we have `160` unique trails only, which makes sense. Now we need to find out the 10 meter interval points of each trail that matches with the `MAX_RASTERVALU` values. To do this, we can join the dissolved points' `MAX_RASTERVALU` attribute to the `Trail_Points_Elevation` attrbute by using the `TRLNAME` as the join field.

    ```{figure} fig-3-19.png
    ---
    name: fig-3-19
    ---
    Join maximum elevation value
    ```

6. Explore the attribute of the `Trail_Points_Elevation` feature. See that we have `RASTERVALU` which is the actual elevation value for each point, and the `MAX_RASTERVALU`, which is the maximum elevation within each trail. The points where the difference between these two attributes are `0`, are the peak points for each trail. Therefore, create a new field called `ELEV_DIFF` (Elevation difference) and compute the difference between `MAX_RASTERVALU` and `ELEV_DIFF`. The points that has a value of `0` would mean that point is the corresponding peak within that particular trail. Now, select the points that has `0` values in the `ELEV_DIFF` attribute (by using the `Select By Attributes`) and export that data to a new feature called `Trail_Peak_Points` in the default geodatabase (Hint: right click the selected layer, click Data, then Export Features).

    ```{admonition} Question 5
    :class: note

    a. How many points you got? ***<1 pt>***  
    b. If you have done the analysis correctly, then the number of peak points you got should be slightly larger than 160, which is the unique number of trails within RMNP. Why you have got more peak points? ***<2 pt>***  
    ```

7. Since there are some duplicated trail points in the `Trail_Peak_Points` feature, we can use the [Delete Identical (Data Management Tools)](https://pro.arcgis.com/en/pro-app/latest/tool-reference/data-management/delete-identical.htm) to remove identical entries from the `TRLNAME` attribute.

    ```{figure} fig-3-20.png
    ---
    name: fig-3-20
    ---
    Delete identical
    ```

8. Select the top 5 highest peaks from the `Trail_Peak_Points` feature and export it seperately as `Top_Five_Peak_Trails`.

### Calculate slope of the DEM

Use the [Slope (Spatial Analyst)](https://pro.arcgis.com/en/pro-app/latest/tool-reference/spatial-analyst/slope.htm) tool to calculate slope of the DEM. Save it as `Slope` in the default geodatabase.

```{figure} fig-3-21.png
---
name: fig-3-21
---
Slope
```

### Find which trails have the highest mean slope

Find [Zonal Statistics as Table (Spatial Analyst)](https://pro.arcgis.com/en/pro-app/latest/tool-reference/spatial-analyst/zonal-statistics-as-table.htm) to calculate the mean slope value for each trail (`Trails_Dissolve`).

```{figure} fig-3-22.png
---
name: fig-3-22
---
Zonal Statistics as table
```

```{admonition} Question 6
:class: note

a. Zonal statistics as table will give you a table within ArcGIS. Join this zonal table with the `Trails_Dissolve` layer and identify the top five trails that has the highest mean slope. ***<2 pt>***  
```

```{admonition} Question 7
:class: note

Create a map with the following items:  
a. An appropriate basemap of the Rocky Mountain National Park with boundary  
b. 5 Trail lines that has the highest peaks  
c. On top of the 4 highest peak trails, show the corresponding peak points with its elevation as label  
d. Top 5 trails that shows higher average slope  
e. The trails that has highest peak and highest slope should not have same color  
f. Any other necessary items
  
***<10 pt>***  
```

## Deliverables

- Your completed `Lab-3-answers-YOURLASTNAME.docx`
- The final map you generated

## Answers

```{admonition} Question 1
:class: note

a. *1080*  
```

```{admonition} Question 2
:class: note

a. *334.97*  
b. *160*
c. *Beaver Meadows / Moraine Park Complex Trail, 15.07 Miles*
d. *Mean: 2.08 Miles and Median: 1.51 Miles*
e. *Not normal, positively skewed.*
```

```{admonition} Question 3
:class: note

a. *No Answer*  
b. *Maximum is 1452.1 feet and minimum is 4837.17 feet.*  
```

```{admonition} Question 4
:class: note

a. *54,070*  
```

```{admonition} Question 5
:class: note

a. *177*  
b. *Because of the 10 meters interval during the generate points step. Since we included the end points when generating points along lines, there could be very adjacent points that share the same elevation cell from the DEM. So sometimes more than one points were sharing the maximum elevation cell resulting in more peak points.*  
```
