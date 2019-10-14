---
date: 2019/10/13 
authors: Simon Bumm, Tristan Ballard, Jen Weng, Nutchapol Dendumrongsup
---

# The Data Open - Stanford 2019

### About this Project

#### The Goal

The goal of this project was to prototype a Machin Learning Model that would enable NYC Taxi drivers to make more profitable decisions about which ride requests to accept. The project was submitted to [The Data Open](https://www.citadel.com/careers/the-data-open/) hosted by Citadel at Stanford University in October 2019.
 
The main idea for this project was to estimate the expected fare of a taxi ride happening within the next ten minutes at any given point in time and from any NYC neighborhood. We evaluated the model by simulating Taxi drivers who could either accept a given ride request immediately, or wait for at most ten minutes for a better ride offer to come (i.e. higher fares). The decision rule we used for this simulation is simple: whenever the expected fares estimated by our model were higher than the current offer, we rejected the latter and decided to wait. In **over 83% of all cases** the decision to wait gave Taxi drivers the chance to catch a better-payed trip within the next ten minutes.
 
#### The Model

We used a simple, off-the-shelf Random Forrest Regression Model and fed it with just three predictors (i.e. time-of-day, day-of-week, and ride pick-up location) to estimate the expected value of a Taxi ride request in any given NYC neighborhood (short: [NTA](https://www1.nyc.gov/site/planning/data-maps/open-data/dwn-nynta.page)) at any given time of the day. Our intention behind this simple architecture was to be able to deliver a robust baseline model within the six hours we had during The Data Open.

#### The Data

Our model is based on two different, publically available data sets:

1) A 2014 NYC Green Taxi Data Set ([link]()), containing information (pickup/dropoff location, fares, etc.) for > 1 mio green taxi rides from NYC in 2014.
2) A shapefile provided by NYC City Planning ([link](https://www1.nyc.gov/site/planning/data-maps/open-data/dwn-nynta.page)), which helps to map pickup/dropoff coordinates to higher-order neighborhood districts, called NTAs.

## Running the code yourself

### Cloning the repository

```console
:~ $ git clone https://github.com/bummy93/dataopen2019.git
:~ $ cd dataopen2019 
```

### Installing required python packages

The code for this project is written in Python 3.7.4

```console
:~/dataopen2019 $ pip install -r requirements.txt
```

### Downloading the data sets
Please be aware that it might take a little while for the taxi data set (~3.5 GB) to download. 
```console
:~/dataopen2019 $ wget -O data/green_trips.csv "https://data.cityofnewyork.us/api/views/2np7-5jsg/rows.csv?accessType=DOWNLOAD"
:~/dataopen2019 $ wget -O data/nta.json "http://services5.arcgis.com/GfwWNkhOj9bNBqoJ/arcgis/rest/services/nynta/FeatureServer/0/query?where=1=1&outFields=*&outSR=4326&f=geojson"
```
