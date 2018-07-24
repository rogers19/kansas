# kansas
Cleaned data for doing an analysis of districting plans in Kansas. 

## Source
I used Harvard Dataverse data from [here](https://dataverse.harvard.edu/dataset.xhtml?persistentId=hdl:1902.1/16698). It claims to use “2010 Census voting district files” which correspond to the 2012 VTD tigerline from [here](https://www.census.gov/cgi-bin/geo/shapefiles/index.php). 

## Data Cleaning
The tigerline file does not have the district assignment of VTDs. At first I thought that the Dataverse file took care of this problem as it has a “CONGRESSIO” column filled with numbers 1-4, however I realized that 489 of the 3907 VTDs in the shapefile had “NA” listed as their congressional district. I fixed this problem by doing a land attribute join by location in QGIS (Vector → Data Management Tools → Join attributes by location) using the highest resolution cartographic boundary file (500k) from [here](https://www.census.gov/geo/maps-data/data/cbf/cbf_cds.html). 

## Variable Names
* STATEFP10: '20' for every feature
* COUNTYFP10: 3-digit county fip from census, unique for each county
* VTDST10: 6-character VTD identification code (numbers and letters) from census, unique for each VTD
* GEOID10: 11-character GEOID from census, unique for each VTD made up of '20'+COUNTYFP10+VTDST10
* VTDI10: voting code from census
* NAME10: voting district name identifier
* LSAD10: Census legal/statistical area description code
* MTFCC10: MAF/TIGER feature class code
* FUNCSTAT10: Census functional status
* ALAND10: Census land area
* AWATER10: Census water area
* INTPTLAT10: Census latitude of the internal point
* INTPTLON10: Census longitude of the internal point
* POP: full population from Census FTP, voting district level
* USS_D_08: U.S. Senate 2008, Democratic votes   
* USS_R_08: U.S. Senate 2008, Republican votes   
* CD: Congressional district number (1-4) for 4 congressional districts in Kansas
