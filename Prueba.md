#### 1. What programming language would you use to automatize the task?

R language

#### 2. What particular libraries would be part of your workflow?

- RpostgreSQL to connect with db
- tidyverse to data manipulation
- sf to spatial data manipulation
- terra to spatial analysis
- climate package to obtain climatological data from stations
- landsadt, ndvits or MODISTools to obtain band values or NDVI values directly

#### 3. How would you ensure that your workflow is fully reproducible five years from now?

I would include a script which would install packages directly from the online source, I would correctly comment my code to make it reproducible for others and if some function is going to be deprecated or even the package is going to change, as now "raster" package for example. System informs you about the change some time before it happens to let you change what is necessary to carry on being reproducible.

#### 4. What data sources would you use? Please, identify them with the proper URLs, dataset names, and spatial or temporal resolution.

I think some packages described above as climate or those suggested to obtain ndvi values allow user to directly work with the data sources which are given in his description. In the case of soil, even it could be done with a package, I will use:

- https://data.isric.org/geonetwork/srv/ger/catalog.search#/metadata/a351682c-330a-4995-a5a1-57ad160e621c for soil attribute data vectorial which profiles are until 2012

- or https://data.isric.org/geonetwork/srv/spa/catalog.search#/metadata/bda461b1-2f35-4d0c-bb16-44297068e10d for Harmonized World Soil Database which is a raster with aprox 8km of spatial resolution and data until 2012. It also includes a db with attribute data for each cell


#### 5. What is the NDVI, and what statistical descriptors of the NDVI time series would you use?

The NDVI is the Normalized Difference Vegetation Index which is given by the formula NDVI = (NIR — RED)/(NIR + RED) and used as indicator of the plant growth. As statistical descriptor for a 6 months before I will use mean and standart desviation for sure, and maybe min and max.

#### 6. What steps would this workflow require?
1) Install and loading packages
2) Previous data manipulation as for example create new column for season taken in account sample_date and coordinates making a division N/S hemisphere and working with proper solstice and equinox dates for each, create new column "clima_date" 15 days before of sample_date or other named "NDVI_date" 6 months before to have the periods of time to analyze later.
3) Obtain climatic data which includes find the nearest feature from the climatological stations to our coordinates, then obtain mean temperatures from "clima_date" to "sample_date", make the mean and the standard desviation in new columns.
4) Obtain soil composition from the soil sources. If we work with pedon profiles in vectorial will be neccesary again use nearest functions to find which pedons represent each of our sample_id and if we work with raster format from HWSD will be necessary find those cells (8x8km) that include our sample_id and then explore associated db to obtain composition attributes for these given cells.
5) Obtain NDVI time series from the products given by the packages cited above it will be done with the support of the "NDVI_date" and as a result a new column with the porposed statistical descriptors.

#### 7. What steps do you think are going to be more problematic and why?

At the moment I think that next issues could be problematic:

1) Geographically: the data interpolation from nearest point is always problematic. It could introduce uncertainity in areas with strong orography, so maybe we could obtain the altitude of our sample_id and use a function to include gradient (+-100m=+-1ºC) in our data. Other option is using products previously harmonized in raster format as those from soils were the assumptions are done by the providers.
2) Programmatically: I think that the NDVI part will take the longest time for me because even I have theoretical knowledge and working experience with these products before it  was always done in desktop SIG softwares. Anyway, once I got familiarized with the given package and the method I will be able to overcome this problem.

#### 8. How long would it take to implement this workflow and prepare the data required by the PD Team?

I think that this workflow as I have planned in my mind will take 10-15 hours.

