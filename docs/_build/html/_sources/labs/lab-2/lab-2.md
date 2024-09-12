# Lab 2: Analyzing violent crime (20 pts)

## Read before proceeding

- The questions for this lab are embedded within the instructions.
- Each question carries specific points, clearly indicated alongside it.
- The questions have subsections within them.
- The total score for this assignment is 20 points. Your final grade will be scaled from the total points you earn out of the maximum possible score to fit within a 0 to 20 scale.
- When working on a lab, always create a dedicated folder for it and store all related files within that specific folder. For instance, avoid saving intermediate files in the `C:/Documents` directory; keep all materials organized and together.
- Create a word document and name it as `Lab-2-answers-YOURLASTNAME.docx`. Insert each questions provided in this document and write down your answers for each questions. Upload the `.docx` file in Canvas. Do NOT upload a `.pdf` of the document.
- Upload any additional file(s) required by this instructions in Canvas. You will find specific list of deliverables at the end of this page.

## Data

[Download the data from this link](https://www.arcgis.com/sharing/rest/content/items/653c890653244e72b122d8bbbf2c0f11/data)

## Background

### Broken Bottles

Despite an overall decline in crime, the bloodshed and violence continues in many of the City's poorest neighborhoods. Frustrated and distressed, community and religious leaders are calling for immediate action. Citing studies linking alcohol to gang violence and to other violent crime, they are putting pressure on city and state officials to close liquor establishments, to decline new liquor license requests, and to reduce access to alcohol in the most violent neighborhoods. Meanwhile, local business owners are banding together, rallying to block the proposed restrictions. They cite violations of the fifth and fourteenth U.S. Constitutional Amendments and claim the proposed restrictions would negatively impact the social fabric and tourism of the City.

The Chief of Police is asking you, the Crime Analyst, to determine if there is indeed a relationship between violent crime and liquor establishments in your City. She wants your recommendations for an effective solution.

You know that this issue has surfaced for different cities around the country and that a number of [research studies](https://isr.unm.edu/reports/2011/place-and-neighborhood-crime--schools-churches-alcohol.pdf) have demonstrated [a correlation between liquor establishments and violent crime](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC3412911/). There are also theoretical explanations supporting this relationship such as [routine activity theory](https://onlinelibrary.wiley.com/doi/full/10.1002/9781118517390.wbetc198) and [social disorganization theory](https://en.wikipedia.org/wiki/Social_disorganization_theory).

Your workflow is summarized below.

```{figure} fig-1.png
---
name: fig-1
---
Broken Bottles
```

### What data will you need?

Since you are interested in violent crime, you collect data for the homicides, rape, robbery, aggravated assault, and aggravated battery incidents over the past year. Next, using [ArcGIS Business Analyst](https://www.esri.com/en-us/arcgis/products/arcgis-business-analyst/overview), you obtain a dataset of businesses that either sell or serve alcohol (this includes bars, nightclubs, lounges, taverns, liquor stores, and so on). If you need additional data, you will use the [data enrichment](https://resources.arcgis.com/en/communities/sharepoint/01t800000007000000.htm) tools in ArcGIS to get it. Your point data is shown below.

```{figure} fig-2.png
---
name: fig-2
---
Liquor vendors in blue; Violent crime incidents in brown. It is difficult to discern spatial patterns with so many points on the map.
```

### Where are the violent crime hot spots? Where are the hot spots for businesses selling or serving alcohol? Do they overlap?

To make sense of the more than 22,000 crime points, and over 1,500 business points, you map them using hot spot analysis. These maps show you the statistically significant hot spots (red) and cold spots (blue) for violent crime and for liquor establishments. If violent crime is linked to liquor establishments, you expect to see spatial correspondence between their activity spaces.

```{figure} fig-3.png
---
name: fig-3
---
Compare the violent crime and liquor vendor hot spot mapsv. The violent crime and liquor vendor hot spot maps look very different.
```

You notice some overlap in the downtown area. To ensure that the remediation efforts you propose focus on your city's most vulnerable neighborhoods, while avoiding areas that could impact tourism, you will need a better understanding of neighborhood poverty patterns within those overlap areas.

### Where are the City's most vulnerable neighborhoods?

You obtain the data needed to create a hot spot map of poverty.

```{figure} fig-4.png
---
name: fig-4
---
Poverty hot spots. The red areas are statistically significant hot spots for poverty.
```

### Which areas should be included in a moratorium on new liquor licenses?

You will recommend remediation measures for statistically significant hot spots (99 percent confidence) across all three variables: violent crime, existing liquor establishments, and poverty. To find these areas, you overlay all three maps, keeping only the hot spot locations that overlap.

```{figure} fig-5.png
---
name: fig-5
---
Violent crime, liquor vendor, poverty hotspots and their overlaps.
```

With the exception of the small overlapping areas identified above, you didn't find a strong spatial correlation between violent crime and businesses that sell or serve alcohol.

Still, the community representatives have indicated that the problem is serious. While you work with numbers every day, you know that there are real faces—real people—behind your data. You decide to dig deeper.

### Has violent crime been increasing in the City? If so, where?

Space-time pattern mining will show you if violent crime has been increasing or not. The maps below show the results of this analysis. You notice several locations with intensifying violent crime hot spots and a number of persistent hot spots as well. Consecutive hot spots are also worrisome; these represent hot spot locations that have been statistically significant for several of the most recent time periods.

```{figure} fig-6.png
---
name: fig-6
---
Violent Crime Trends. There are several concerning trends including new, intensifying, and persistent hot spot areas.
```

The 3D map below is zoomed in to the area of both sporadic and consecutive violent crime hot spot trends in the downtown area. The green squares at the base of the map delineate one of the liquor moratorium remediation areas you identified above. Each bin in the 3D stack represents a four-week time period, with the most recent time period at the top. The darkest red bins reflect locations and time periods with intense violent crime activity.

```{figure} fig-7.png
---
name: fig-7
---
3D view of violent crime trends downtown.
```

There are definitely locations around the City where violent crime is persistent and even intensifying; most of these do not correspond to high densities of businesses serving or selling alcohol, however.

### What else might be contributing to violent crime?

Two years ago the City implemented a [Summer Jobs Program](https://www.chicagomag.com/city-life/December-2014/How-a-Chicago-Summer-Job-Program-Reduced-Violent-Crime/) that has proven tremendously effective at reducing violent crime. You obtain unemployment data and repeat your hot spot analysis to see if you find a stronger spatial correlation between unemployment and violent crime than you did between liquor establishments and violent crime. Interestingly, you do.

```{figure} fig-8.png
---
name: fig-8
---
Compare the violent crime and unemployment hot spot maps. There are a number of locations where the violent crime and unemployment hot spots overlap.
```

### Where do persistent, intensifying, and consecutive hot spots overlap with unemployment hot spots?

You will recommend remediation measures for the areas where persistent, intensifying, and consecutive hot spot trends overlap with the statistically significant unemployment hot spots (99 percent confidence).

```{figure} fig-9.png
---
name: fig-9
---
Overlap between violent crime trends and unemployment hot spots. The blue areas are the locations where intensifying, persistent, and consecutive hot spot trends overlap with the most intense unemployment hot spots.
```

### Which specific high schools should be targeted for an expanded summer jobs program?

You identify high schools within a quarter mile of the remediation areas where high violent crime and high unemployment overlap.

```{figure} fig-10.png
---
name: fig-10
---
Selected schools. You will recommend that several schools be included in an expanded summer jobs program.
```

Your analyses have gone well! You have several recommendations to propose to the Chief of Police.

### Final recommendations

```{figure} fig-11.png
---
name: fig-11
---
Final recommendations.
```

Your final report will include the map above showing your recommendations below.

- Areas with high densities of violent crime, businesses selling or serving alcohol, and poverty. Suggested remediation: Review the existing liquor licenses for violations. Impose a moratorium on new liquor licenses.

    ```{figure} fig-12.png
    ---
    name: fig-12
    ---
    legend1
    ```

- Areas with intensifying or persistent violent crime and high unemployment rates. Suggested remediation: Add the public high schools within 0.25 miles of these areas to the existing summer jobs program. Consider a PR campaign to make people aware of the tremendous success this program has had on reducing violent crime over the past two years.

    ```{figure} fig-13.png
    ---
    name: fig-13
    ---
    legend2
    ```

- New violent crime hot spots. Suggested remediation: Assign officers to work with residents and community advocates in these areas to understand what's behind the sudden increase in violent crime and hopefully keep violent crime in these areas from becoming endemic.

    ```{figure} fig-14.png
    ---
    name: fig-14
    ---
    legend3
    ```

In addition, it will be important to evaluate the space-time violent crime patterns monthly to assess the effectiveness of these remediation measures.

## Workflow using ArcGIS Pro

### Do some exploratory data analysis

1. If you haven't done so already, download and unzip the data package provided at the top of this workflow.
2. Open ArcGIS Pro and browse to the `BrokenBottlesPkg.ppkx` project package.
3. Open the **Attribute Table** of `Violent Crime 2014` layer and explore the data.

    ```{admonition} Question 1
    :class: note

    a. What Primary Type crimes have been reported in the data? (Note that I am not asking for the total number of crime, I am asking how many classes of primary types crime has been reported in this dataset?) ***<1 pt>***    
    b. Which primary type of crime is the most frequent in the area and what is the number? ***<1 pt>***  

4. Download the [neighborhood boundary data of Chicago](https://data.cityofchicago.org/Facilities-Geographic-Boundaries/Boundaries-Neighborhoods/bbvz-uum9) and bring the layer into the Project. (Click the `Export` and select `Shapefile`)

    ```{admonition} Question 2
    :class: note

    a. Which neighborhood had the highest number of robberies and what was the number? ***<1 pt>***   
    b. Which primary type of crime is the most frequent in the area and what is the number? ***<1 pt>***    
    c. How did you get these information? Please explain in few sentences about the approach you took. (There are multiple ways to do it, you just need to explain the one you did.) ***<3 pt>***  

### Create a hot spot map of violent crime densities

1. Once the project opens, find and open the [Optimized Hot Spot Analysis](https://pro.arcgis.com/en/pro-app/latest/tool-reference/spatial-statistics/optimized-hot-spot-analysis.htm) tool. If the Geoprocessing pane isn't open, click the **Analysis** menu tab, then click the **Tools** button. (Tips: Whenever possible and appropriate, create your workflow output in a geodatabase rather than as a shapefile. Field names in shapefile output may be truncated, and there are other advantages to using a geodatabase to store your data.)
2. Run the [Optimized Hot Spot Analysis](https://pro.arcgis.com/en/pro-app/latest/tool-reference/spatial-statistics/optimized-hot-spot-analysis.htm) tool with the following parameters. The **Analysis Boundary** layer defines the study area.
   - Input Features : `Violent Crime 2014`
   - Output Features : the name of your output feature class such as `ViolentCrimeHotSpots`
   - Incident Data Aggregation Method : Count incidents within fishnet grid
   - Bounding Polygons Defining Where Incidents Are Possible : `Analysis Boundary`

    ```{figure} fig-15.png
    ---
    name: fig-15
    ---
    Optimized Hot Spot Analysis tool parameters for Violent Crime 2014.
    ```

While the tool runs, it reports the cell size it used for aggregation and the distance it used for analysis (the scale of the analysis). To see this information, hover over the progress bar below the Geoprocessing pane and click the icon to pop out the progress messages. You may resize the message pane by pulling on the lower right corner of the pop out window.

```{figure} fig-16.png
---
name: fig-16
---
View tool messages.
```

Notice that for this analysis the cell size is 1,375 feet and the scale of analysis is 4,563 feet (4,554 Feet with the most current software).f you are comparing multiple hot spot maps, you will want to make sure that the study area, cell size, and scale of analysis all match.

```{figure} fig-17.png
---
name: fig-17
---
Optimized Hot Spot Analysis message output.
```

The output map created by [Optimized Hot Spot Analysis](https://pro.arcgis.com/en/pro-app/latest/tool-reference/spatial-statistics/optimized-hot-spot-analysis.htm) is shown below:

```{figure} fig-18.png
---
name: fig-18
---
Violent crime hot spot map.
```

```{admonition} Question 3
:class: note

a. You used `Count incidents within fishnet grid` as the **Incident Data Aggregation Model**. What is fishnet? ***<1 pt>***  
b. Similarly there is another option called `Count incidents within hexagon grid`. Create another Hot Spot map using hexagon grids and look at the differences. In your words, explain when Hexagons can be useful. (Hint: Explore [here](https://pro.arcgis.com/en/pro-app/latest/tool-reference/spatial-statistics/h-whyhexagons.htm) to find out more.) (Note: For the rest of the analysis, do not use the hot spot results from hexagon, use it from the fishnet.) ***<2 pt>***
```  

### Create a hot spot map of liquor vendor densities

Use the Optimized Hot Spot Analysis tool again with the following parameter settings. You will use the output from the violent crime hot spot analysis to define the study area and cell size.

- Input Features : `Liquor Vendors`
- Output Features : the name of your output feature class such as `LiquorVendorHotSpots`
- Incident Data Aggregation Method : Count incidents within aggregation polygons
- Polygons For Aggregating Incidents Into Counts : `ViolentCrimeHotSpots`

```{figure} fig-19.png
---
name: fig-19
---
Optimized Hot Spot Analysis of liquor vendors, tool parameters.
```

Note: Because you used the exact same study area for both analyses, the scale of analysis should match exactly. Be sure to check it, though. Sometimes, when the distributions of points are vastly different, there will be a mismatch. If you do see a mismatch, run Hot Spot Analysis on the output from Optimized Hot Spot Analysis, setting the Distance Band or Threshold Distance parameter explicitly to match the hot spot map you want to compare.

Now you can compare the hot spot maps to see where their activity spaces overlap.

```{figure} fig-20.png
---
name: fig-20
---
Violent crime and liquor vendor hot spot maps.
```

```{admonition} Question 4
:class: note

a. Why did you use `Count incidents within aggregation polygons` in this case? What would have been happened if you created the hot spot map the same way you did for the Violent Crime layer? ***<2 pt>***  
```  

### Create a hot spot map of poverty

While you may use the [Enrich Layer](https://pro.arcgis.com/en/pro-app/latest/tool-reference/analysis/enrich-layer.htm) tool to get poverty data, to ensure your results match those below and to avoid consuming credits, use the data provided in the data package you downloaded. The [Enrich Layer](https://pro.arcgis.com/en/pro-app/latest/tool-reference/analysis/enrich-layer.htm) tool always gives you the most current data available. When this workflow was created, the ACS poverty data was for 2009-2013.

1. Navigate to `Poverty.lpk` included with the data package you downloaded. Drag it on the map.
2. Find and open the Optimized Hot Spot Analysis tool a third time.
3. Set the parameters as follows and run the analysis.
    - Input Features: `Poverty`
    - Output Features: the name of your output feature class such as `PovertyHotSpots`
    - Analysis Field: `2009-2013 ACS Households with Income Below Poverty Level`

```{figure} fig-21.png
---
name: fig-21
---
Violent crime and liquor vendor hot spot maps.
```

### Overlay the hot spot maps to determine areas of overlap

1. Find and open the Select Layer By Attribute tool. You will run the tool on all three hot spot maps, each time selecting records where the Gi_Bin field is equal to 3 (a three for this field indicates a statistically significant hot spot at the 99 percent confidence level). The Gi_Bin field name will reflect the scale of analysis (4554 for the most current version of the software).

    ```{figure} fig-22.png
    ---
    name: fig-22
    ---
    Select the most intense violent crime, liquor vendor, and poverty hot spots.
    ```

2. Next, find and open the Intersect tool. Add all three layers as Input Features, provide a name for the output, such as iCrimeLiquorPoverty, and run the analysis.

    ```{figure} fig-23.png
    ---
    name: fig-23
    ---
    Find the intersection between the violent crime, liquor vendor, and poverty 99 percent confidence level hot spots.
    ```

3. Clear the selections, and turn off all other layers in order to see the output showing the overlapping locations. These locations will be your proposed areas for a liquor moratorium.

    ```{figure} fig-24.png
    ---
    name: fig-24
    ---
    Areas where the violent crime, liquor vendor, and poverty hot spots overlap.
    ```

### Create a space-time cube and analyze the crime trends within it

1. Find and open the [Create Space Time Cube By Aggregating Points](https://pro.arcgis.com/en/pro-app/latest/tool-reference/space-time-pattern-mining/create-space-time-cube.htm) tool.
2. For version 1.4 or later of ArcGIS Pro, to ensure the cube output aligns with the hot spot output, you must set the **Processing Extent** to match the **Analysis Boundary** layer. Click the **Environments** tab and change the **Extent** to **Analysis Boundary**.

    ```{figure} fig-25.png
    ---
    name: fig-25
    ---
    Setting the processing Extent.
    ```

3. Set the Create Space Time Cube **Parameters** as follows and run the analysis. The cube is a [netCDF file](https://pro.arcgis.com/en/pro-app/latest/help/data/multidimensional/what-is-netcdf-data.htm), so it must be created in a folder rather than inside a [file geodatabase](https://pro.arcgis.com/en/pro-app/latest/help/data/geodatabases/overview/what-is-a-geodatabase-.htm). Setting the **Distance Interval** to match the hot spot map cell size will allow you to overlay the crime trends with hot spot maps later. For version 1.4 of ArcGIS Pro only, you must convert 1375 US Feet to 1375 International Feet (1375.00275).
   - Input Features: `Violent Crime 2014`
   - Output Space Time Cube: the name of your output cube such as `ViolentCrimeCube.nc`
   - Time Field: `Date`
   - Time Step Interval: `4 Weeks`
   - Time Step Alignment: `End time`
   - Distance Interval: `1375 Feet`; for version 1.4 and 2.0 of ArcGIS Pro only, use 1375.00275 instead (see note below).

    Note:
    With version 1.4 and 2.0 of ArcGIS Pro, the space time cube will not align with the output from Optimized Hot Spot Analysis unless the cell size is entered in US Feet. US Feet are slightly larger and have more precision that International Feet. With later versions of the software, **Feet** parameters will automatically be interpreted as US Feet.

    Caution:
    If you want a valid space-time analysis of incident data (like crime events), make sure each bin in the space-time cube is exactly the same size. Selecting **Months** for the **Time Step Interval**, for example, will result in some bins having more days than others (31 days for March, but only 30 days for April). This will bias your analysis because months with more days will likely have more incidents. Use `Days`, `Weeks`, or `Years` instead of `Months`.

    Tip:
    Use the `End time` **Time Step Alignment**. If the incident range of dates doesn't divide evenly into your **Time Step Intervals**, you want the bias to be associated with the first (oldest) time period rather than the last (most recent) time period. For example, suppose your data covers fifteen and a half weeks and you select `1 week` for your **Time Step Interval**. If you select `Start time` for the **Time Step Alignment**, all of the bins will have a full week, except the bins for the last (most recent) time period; it will only have half a week.

    ```{figure} fig-26.png
    ---
    name: fig-26
    ---
    Create Space Time Cube tool parameter settings.
    ```

    The tool will report it completed successfully but will not add new layers to the map.

    ```{admonition} Question 5
    :class: note

    a. In a few sentence, explain NetCDF files and when it is useful? (Hint: google it and try to learn more about NetCDF data.) ***<2 pt>***  
    ```  

4. Find and open the [Emerging Hot Spot Analysis](https://pro.arcgis.com/en/pro-app/latest/tool-reference/space-time-pattern-mining/emerginghotspots.htm) tool.
5. Set the following parameters and run the analysis.
   - Input Space Time Cube: `ViolentCrimeCube.nc`
   - Analysis Variable: `COUNT`
   - Output Features: the name of your output feature class such as `ViolentCrimeTrends`
   - Neighborhood Distance: `0.5 Miles`
   - Neighborhood Time Step: `1`
   - Polygon Analysis Mask: `Analysis Boundary`

    ```{figure} fig-27.png
    ---
    name: fig-27
    ---
    Emerging Hot Spot Analysis tool parameter settings.
    ```

6. Examine the results. The trend categories are defined as follows.

    Pattern Type | Definition
    -------------|--------------------------------------------------
    New Hot Spot | A location that is a statistically significant hot spot for the final time step and has never been a statistically significant hot spot before.
    Consecutive Hot Spot | A location with a single uninterrupted run of statistically significant hot spot bins in the final time-step intervals. The location has never been a statistically significant hot spot prior to the final hot spot run and less than ninety percent of all bins are statistically significant hot spots.
    Intensifying Hot Spot | A location that has been a statistically significant hot spot for ninety percent of the time-step intervals, including the final time step. In addition, the intensity of clustering of high counts in each time step is increasing overall and that increase is statistically significant.
    Persistent Hot Spot | A location that has been a statistically significant hot spot for ninety percent of the time-step intervals with no discernible trend indicating an increase or decrease in the intensity of clustering over time.
    Diminishing Hot Spot | A location that has been a statistically significant hot spot for ninety percent of the time-step intervals, including the final time step. In addition, the intensity of clustering in each time step is decreasing overall and that decrease is statistically significant.
    Sporadic Hot Spot | A location that is an on-again-off-again hot spot. Less than ninety percent of the time-step intervals have been statistically significant hot spots and none of the time-step intervals have been statistically significant cold spots.
    Oscillating Hot Spot | A statistically significant hot spot for the final time-step interval that has a history of also being a statistically significant cold spot during a prior time step. Less than ninety percent of the time-step intervals have been statistically significant hot spots.
    Historical Hot Spot | The most recent time period is not hot, but at least ninety percent of the time-step intervals have been statistically significant hot spots.
    New Cold Spot | A location that is a statistically significant cold spot for the final time step and has never been a statistically significant cold spot before.
    Consecutive Cold Spot | A location with a single uninterrupted run of statistically significant cold spot bins in the final time-step intervals. The location has never been a statistically significant cold spot prior to the final cold spot run and less than ninety percent of all bins are statistically significant cold spots.
    Intensifying Cold Spot | A location that has been a statistically significant cold spot for ninety percent of the time-step intervals, including the final time step. In addition, the intensity of clustering of low counts in each time step is increasing overall and that increase is statistically significant.
    Persistent Cold Spot | A location that has been a statistically significant cold spot for ninety percent of the time-step intervals with no discernible trend, indicating an increase or decrease in the intensity of clustering of counts over time.
    Diminishing Cold Spot | A location that has been a statistically significant cold spot for ninety percent of the time-step intervals, including the final time step. In addition, the intensity of clustering of low counts in each time step is decreasing overall and that decrease is statistically significant.
    Sporadic Cold Spot | A location that is an on-again-off-again cold spot. Less than ninety percent of the time-step intervals have been statistically significant cold spots and none of the time-step intervals have been statistically significant hot spots.
    Oscillating Cold Spot | A statistically significant cold spot for the final time-step interval that has a history of also being a statistically significant hot spot during a prior time step. Less than ninety percent of the time-step intervals have been statistically significant cold spots.
    Historical Cold Spot | The most recent time period is not cold, but at least ninety percent of the time-step intervals have been statistically significant cold spots.
    No Trend Detected | Does not fall into any of the hot or cold spot patterns defined above.

    For your analysis there are no cold spots.

    ```{figure} fig-28.png
    ---
    name: fig-28
    ---
    Violent crime trends.
    ```

### Create a hot spot map of unemployment rates

1. Navigate to `Unemployment.lpk` included with the data package you downloaded. Drag it onto the map.
   Note: The [Enrich Layer](https://pro.arcgis.com/en/pro-app/latest/tool-reference/analysis/enrich-layer.htm) tool always gives you the most current data available. When this workflow was created, the unemployment rate data was for 2015.
2. Open the [Optimized Hot Spot Analysis](https://pro.arcgis.com/en/pro-app/latest/tool-reference/spatial-statistics/optimized-hot-spot-analysis.htm) tool.
3. Set the parameters as follows and run the analysis.
   - Input Features: `Unemployment`
   - Output Features: the name of your output feature class such as `UnemploymentRateHotSpots`
   - Analysis Field: `2015 Unemployment Rate`

    ```{figure} fig-34.png
    ---
    name: fig-34
    ---
    Unemployment rate hot spot map.
    ```

### Overlay the violent crime trend map with the unemployment rate hot spot map to determine areas of overlap

1. Find and open the **Select Layer By Attribute** tool. You will use it once to select intensifying, persistent, and consecutive hot spots (Pattern Type `COUNT` is **Equal** to `Consecutive Hot Spot` Or Pattern Type `COUNT` is **Equal** to `Intensifying Hot Spot` Or Pattern Type `COUNT` is **Equal** to `Persistent Hot Spot`) and a second time to select the most intense unemployment rate hot spots (Gi_Bin Fixed 4556_FDR is equal to 3).

   ```{figure} fig-35.png
    ---
    name: fig-35
    ---
    Select Layer By Attribute tool parameters.
    ```

    Caution:
    Be sure to click the `Add` button after creating the expression, otherwise all the features in the layer will be selected.

2. Next, find and open the **Intersect** tool. Add the violent crime trends and unemployment rate hot spot maps with their active selections, provide a name for the output results such as `iCrimeUnemp`, and run the analysis.

    ```{figure} fig-36.png
    ---
    name: fig-36
    ---
    Intersect tool parameters.
    ```

    ```{figure} fig-37.png
    ---
    name: fig-37
    ---
    Overlap of unemployment hot spots with consecutive, persistent and intensifying violent crime trends.
    ```

### Finally, select the public high schools within a quarter mile of the overlapping areas

1. Find and open the **Select Layer By Location** tool.
2. Set the parameters as follows:
    - Input Feature Layer: `Public High Schools`
    - Relationship: `Within a distance`
    - Selecting Features: `iCrimeUnemp`
    - Search Distance: `0.25 Miles`

    ```{figure} fig-38.png
    ---
    name: fig-38
    ---
    Select high schools near overlap areas.
    ```

3. Use the Copy Features tool to copy the selected high schools to a new feature class (this is optional, but it makes mapping and creating reports a bit easier).
    - Input Features: `Public High Schools`
    - Output Feature Class: the name of your output feature class such as `SelectedHighSchools`

```{admonition} Question 6
:class: note

a. Create your Final Crime Remediation Area with necessary legends and basemap layers. Use proper mapping tools in your map. ***<6 pt>***  
```

## Analyze Crime Patterns in Saint Louis

You will do a similar analysis like the above for Saint Louis Crime patterns. I want you to slowly familirize yourself with Open-source Python solutions for different data processing tasks. Therefore, the data cleaning steps are already done for you in this notebook. You do not have to run the codes in the notebook, but feel free to familirize with the modules and functions used here to understand the general notion of data processing tasks.

### Data for Saint Louis

The data you will need for this portion is already processed as `.shp` files:

1. [Crime Data](../../../labs/lab-2/data/shapes/crime_data.zip)
2. [Liquor Stores](../../../labs/lab-2/data/shapes/liquors.zip)
3. [Median household income](../../../labs/lab-2/data/shapes/income.zip)

The details about where I collected the data and how I processed it, are well documented in the [notebook](https://github.com/souravbhadra/GIS5120/blob/main/labs/lab-2/data-cleaning.ipynb).

Follow the steps to [Create a hot spot map of violent crime densities](#create-a-hot-spot-map-of-violent-crime-densities) using the [Saint Louis crime data](../../../labs/lab-2/data/shapes/crime_data.zip). Do similar tasks for [Liquor Stores](../../../labs/lab-2/data/shapes/liquors.zip) to [Create a hot spot map of liquor vendor densities](#create-a-hot-spot-map-of-liquor-vendor-densities) and [Median household income](../../../labs/lab-2/data/shapes/income.zip) to [Create a hot spot map of poverty](#create-a-hot-spot-map-of-poverty). **Note that for poverty we are using median household income, not the poverty data. So if you take `income` as your variable, hot spots would represent income hot spots. So for representing poverty hot spots, you would want the cold spots of income.** Finally, [Overlay the hot spot maps to determine areas of overlap](#overlay-the-hot-spot-maps-to-determine-areas-of-overlap) and create a map.

### Your task

```{admonition} Question 7
:class: note

a. Create an overlap of crime hot spots, liquor store hot spots and income cold spots. Publish a nice map with necessary attributes and other information. ***<20 pt>***  
```
