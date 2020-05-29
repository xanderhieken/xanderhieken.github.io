---
title: "Spark Aggregations"
date: 2019-11-03
tags:
 - Python
 - Jupyter Notebook
 - PySpark
excerpt: "How to Join Datasets and Perform Aggregations with Spark"
header:
  overlay_image: "/assets/SparkAggBackground.png"
  overlay_filter: 0.3 # same as adding an opacity of 0.3 to a black background
  teaser: "/assets/SparkAggBackground.png"
  actions:
    - label: "Go to GitHub Repository"
      url: "https://github.com/xanderhieken/SparkAggregations"
---

# Joining Datasets and Performing Aggregations with Spark

**This notebook shows how to join datasets in Spark and perform a variety of aggregations using Spark SQL by completing a series of common tasks.**

## The Data
There are two data files that are used in this notebook (`flights.parquet` and `airport-codes.csv`), which can be found in the data folder of the GitHub repository.

#### File Schema
* **`flights.parquet`** *(3,606,803 total records)*
	* origin_airport_code: string (nullable = true)
	* destination_airport_code: string (nullable = true)
	* origin_city: string (nullable = true)
	* destination_city: string (nullable = true)
	* passengers: long (nullable = true)
	* seats: long (nullable = true)
	* flights: long (nullable = true)
	* distance: double (nullable = true)
	* origin_population: long (nullable = true)
 	* destination_population: long (nullable = true)
	* flight_year: long (nullable = true)
	* flight_month: long (nullable = true)
	* \_\_index_level_0\_\_: long (nullable = true)

* **`airport-codes.csv`** *(54,591 total records)*
	* ident: string (nullable = true)
	* type: string (nullable = true)
	* name: string (nullable = true)
	* elevation_ft: double (nullable = true)
	* continent: string (nullable = true)
	* iso_country: string (nullable = true)
	* iso_region: string (nullable = true)
	* municipality: string (nullable = true)
	* gps_code: string (nullable = true)
	* iata_code: string (nullable = true)
	* local_code: string (nullable = true)
	* coordinates: string (nullable = true)

## Tasks
1. Load the data and print the schema

3. Join the flight data to airport codes data by matching the IATA code of the originating flight to the IATA code in the airport codes file, then print the schema

4. Remove the following columns from the joined DataFrame:
	-   \_\_index_level_0\_\_
	-   ident
	-   local_code
	-   continent
	-   iso_country
	-   iata_code

5. Rename the following columns:
	-   type: origin_airport_type
	-   name: origin_airport_name
	-   elevation_ft: origin_airport_elevation_ft
	-   iso_region: origin_airport_region
	-   municipality: origin_airport_municipality
	-   gps_code: origin_airport_gps_code
	-   coordinates: origin_airport_coordinates

6. Repeat steps 2-4 for destinations:
	* Join the data on destination airport instead of the origin airport
	* Drop the same columns
	* Rename the same columns using the prefix `destination_airport_` instead of `origin_airport_` 
	* Print the schema

7. Create a dataframe using only data from 2008. This dataframe will be a report of the top ten airports by the number of inbound passengers. This dataframe should contain the following fields:
	-   Rank (1-10)
	-   Name
	-   IATA code
	-   Total Inbound Passengers
	-   Total Inbound Flights
	-   Average Daily Passengers
	-   Average Inbound Flights 

8. Create a user-defined function in Python that will convert the string coordinates into numeric coordinates

9. Add new columns for:
	*  destination_airport_longitude
	* destination_airport_latitude
	* origin_airport_longitude
	* origin_airport_latitude 
		* Then, print the schema

### Rather than providing all of the schema printouts here, they can all be found in the [notebook](https://github.com/xanderhieken/SparkAggregations/blob/master/Spark%20Aggregations.ipynb) located in the GitHub repository for this project.

## Author
**Xander Hieken**

