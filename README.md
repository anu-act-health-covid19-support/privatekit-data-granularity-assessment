# Assessment of how granular the data generated from Privacy Kit is 

## Purpose 

The purpose of this repo is to assess how granular the data captured by the Privacy Kit mobile application is. This will be used to determine if the granularity is suitable for epidemiological, statistical and tracking purposes. 

## Method 

Person: Kathy Reid, 25th March 2020, 1200hrs 

* Exported data from the Private Kit application on mobile phone
* this is held in this repo in [this file](https://github.com/ACT-COVID-19-TRACKER/privatekit-data-granularity-assessment/blob/master/1585096669577.null)
* Examination of the data structure showed it was well-formed `JSON`, but _not_ `GeoJSON`. 
* Wrote a Python script to convert `JSON` to `GeoJSON`
* Imported `GeoJSON` into MapBox (which is not open source, but this was a quick test) 

https://api.mapbox.com/styles/v1/kathyreid/ck86m0rum0bf51inxk3hc7ogx.html?fresh=true&title=view&access_token=pk.eyJ1Ijoia2F0aHlyZWlkIiwiYSI6Ik9Dbl9JeDAifQ.ujJagjjsojv4iIEzpRQCfA#15.43/-35.278955/149.119538/0

It's more work to show location over time, but this is a quick test. 

## Findings 

* The datapoints are stored in the following format; 

```
{"latitude":-35.2801205,"longitude":149.1120968,"time":1584685015006}
```

That is, just lat, long and a Unix-epoch formatted timestamp. 

So yes, we can show travel over time with this data. 

The granularity is to within a few metres - it is likely that this would be affected by each individual user's mobile phone GPS, wireless and mobile internet access settings. 

The datapoints are taken at 5 minute intervals, so this granularity may not be effective if a person is cycling or travelling by bus, light rail or car. 

_The granularity of datapoint recording cannot be changed within the app itself - it would need to be recompiled, then pushed to the various app stores. 

## Questions arising from this test 

* Is the data fine-grained enough for the purposes of the broader initiative here - ie Contact Tracing, statistics and so on? 


