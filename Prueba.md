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

