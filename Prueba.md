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
