# Gale
Excel workbook to show optimal bike touring routes with the wind at your back.

This Excel workbook was created to help bicycle tourists experience the best kind of adventure, the kind with the wind at your back!

Adapting the NOAA's climate data from 1930-1996 (https://www.ncdc.noaa.gov/sites/default/files/attachments/wind1996.pdf), this text data was transfered to a spreadsheet and cleansed.

GALE DASH:
This page acts as the user's dashboard. User inputs starting location for travels, the time of year, and distance estimates.

WIND DATA: 
This worksheet contains the cleansed wind directions based on location from the NOAA's report. These directions based on time of year are dynamically refered to throughout the file.

GEODATA:
This worksheet incorporates latitude and longitude attributes for the known locations. While refering to the user's starting location, it finds the nearest cities with the following process:
  1: In B5 and B6, uses INDEX-MATCH function to dynamically pull in the coordinates of starting city
  2: In column M, calculates distance between start coordinates and all other city coordinates with ACOS-COS-RADIANS-SIN function to            triangulate hypotenuse
  3:In B5-D5->, finds closest cities with SMALL function in reference to city coordinates

OPTIMAL CITIES:
We found the closest cities, great! This worksheet further refines optimal routes by incorporating wind data so the wind is at your back. 
  1: A1:B5 dynamically refers to your starting location and wind direction
  2: A7:C7-> brings in closest cities from GeoData worksheet. D:E-> finds directional coordinate differences using GeoData's data
  3: H:O-> use IF-OR-AND statements based on wind direction and time of year to apply a boolean value (1 if wind is at back, 0 if not).        This is output into column P.
  4: Q:R-> dynamically reveal optimat cities if boolean value = 1.
  
There you have it. How to find the best cycle touring directions on average relative to the time of year.
