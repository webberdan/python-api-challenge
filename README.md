# python-api-challenge

In this challenge the goal was to leverage the OpenWeather API along with the Google Maps and Places API to determine favorable suggestions for a vacation. We randomized this by generating latitude and Longitude pairs and using the CitPy library to locate the nearest city to that pair. 

#Part 1- Weather Data Aggregation
## Step 1- Create Cities List

By generating the Lats and Longs and finding the nearest city, we generated a sample set of 617 cities to research. 

We cretaed a list for the purpose of iterating through them in the OpenWeather API.

## Step 2- Perform API Call to OpenWeather

We then performed an API call to collect the weather data needed. First set variables for a record counter and a set counter, so we could batch the results into groups of 50. We enumerated through the list and created variables to be stored in a list for: lat, lon, max temp, humidity, cloudiness, wind speed, country, and date stamp. We also used the sleep function forom the  time library to ensure we did not compromise the api key.

## Step 3 - Data Cleaning

We created a dataframe the results, and removed errouneous results where humidity was reported to be >100% (no results found). Then the .describe function was used to gather statistical data on the results.

##Step 4- Plotting the Values
The plots were sperated into two groupings for the Northern and Southern hemispheres. scatter plots were created for Latitude vs. Temp, Latitude vs. Humidity, and Latitude vs. Wind Speed. Then Linear Regression Models were built for the following: Max Temp vs. Latitude, Humidity (%) vs. Latitude, Cloudiness (%) vs. Latitude and Wind Speed (mph) vs. Latitude. 

## Part 1 Findings
The stongest coorelation was that temp and humidity were higher as you get closer to the equator. 

# Part 2- Google Places Data and Mapping

## Step 1- Calling the data for charting
By calling the .csv file created from the weather research above, we established a sample set to query from the Google places API and to map using the maps API.

## Stes 2- Mapping Humidity
By using the humidity data from our intitial research a heat map was created to show the humidity levels. This was done by created a heat_map layer and imposing it on the map as shown.

## Step 3- Data Grooming
Pre-defined weather conditions were established to groom the data to desirable conditions. From the original 617 locations found in the intital data aggregation, only 13 remained after these conditions were imposed. This was handled by using the .dropna() function. 

## Step 4- Hotel Mapping
Now that we have our desirable locations from a weather conditions standpoint, the task is to create a map with map points on it with hotel info. To handle this, the Googl Places API is leveraged and the nearby call is imposed to find a "lodging" location within 5000 meters. It was determined that three locations that had desirable weather did not have a hotel in the database that met this criteria, therefor they were dropped from final mapping. The marker layer was then created by using JavaScipt to show the hotel name, city, and country info.

