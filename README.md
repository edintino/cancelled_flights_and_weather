# cancelled_flights_and_weather

## Data and preprocessing

Two dataset was used for this project, one contained the [flight data] and the other one the [weather data]. I put the datasets into a data folder and renamed the weather dataset file to "2015_usa_weather.csv" (unfortunately does not contain wind or precipitation, which would be the most important). My idea was to create a classification model to decide whether a flight will be cancelled or not using the columns (- and the reasoning):

+ Origin/Destination airport - ground handling problems or similar,
+ Distance - weather condition might change dramatically for longer journeys  (the basic dataset contained the distance, but I wanted to challenge myself to calculate it),
+ Average/Minimum/Maximum temperature - this supposed to cover the weather conditions, a big difference in max and min, might indicate a storm, but as I said earlier a wind and/or precipitation would be better as weather directly does not influence cancellation.

Improvements could be done with: wind, precipitation, airline (crew out of time) or plane type (mechanical issues).

First I defined a function to calculate the distance between two points on a sphere using the Haversine formula from the latitude and longitude input. Took only the parts of the dataset, which I wanted to use. Than found the closest weather staition to all the airports and calculated the distances between the required airports. Finally merged the dataframes with appropriate labels and saved the dataframe in a pickle file, 'flights_dataframe.p' (unfortunately too large, so could not upload it here).

[flight data]:https://www.kaggle.com/usdot/flight-delays
[weather data]:https://data.world/mattwinter225/2015-usa-weather-avg-max-min

## Classification model

First I tried using a linear classifier of tensroflow, the accuracy was surprisingly good, so I did further checks and it turned out that it produced only no cancellation as the event of a flight cancellation is relatively rare the model got high accuracy. Secondly I tried a dense neural network classifier, unfortunaltely with no imporvement.

## Conclusion

Probably more relevant data would be required for cancellation prediction as it depends on many factors or maybe different models should be used. Another approach could be to make the task of the model easier and classify whether there will be a delay due to weather conditions, this might be a future project.
