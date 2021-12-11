# DS3000 Final Project: Domestic Arrival Trends at Logan Airport

George Bikhazi, Ryan Dombroski, Tim Wang

## Overview

In this project, we explore factors that contribute to domestic commercial flight delays at Boston Logan International Airport. Factors explored include carrier, originating airport, meteorological conditions, and timetable information (scheduled flight date and time, etc). Using US DoT statistical data and open-source weather data, we used standard data wrangling, information visualization, and applied machine learning techniques to determine if there were any relationships between the factors we identified and flight delays.

Our prediction algorithms made use of regression models, as opposed to classification models, because we wanted to predict flight delay as a numerical value. To this end, we tested Linear, Ridge, and Lasso regression models, and made use of feature selection and hyperparameter tuning in the form of a grid search algorithm to optimize each model's prediction algorithm. Ultimately, our analysis suggests that the factors we identified do not play a particularly significant role in predicting domestic flight delays at Logan Airport. However, we note that this may be due to limitations in our methodology and data.

See the [notebook](/DS3000_FP4_Group31.ipynb) for further information.

## Data

All data is available in CSV form in the [data directory](https://github.com/timaeusx/ds3000-logan-arrival-trends/tree/main/data) of this project's GitHub repository.

### Logan Airport Domestic Arrival Data, 2019
Domestic arrival data for Logan International Airport was obtained from the [United States Department of Transportation’s Bureau of Transportation Statistics](https://transtats.bts.gov/ONTIME/Arrivals.aspx). We chose to use data from 2019 so as to avoid impacts on air travel relating to the COVID-19 pandemic. The raw dataset includes information about the flight (carrier, flight number, date, etc) and the timetable (scheduled arrival time, elapsed time, taxi time, etc). Our model makes use of the following variables from this dataset:

| Variable [Original Name]               | Description                                             | Feature/Outcome |
|----------------------------------------|---------------------------------------------------------|-----------------|
| carrier [Carrier]                      | Airline the flight was operated by                      | Feature         |
| date [Date (MM/DD/YYYY)]               | Flight date                                             | Feature         |
| origin [Origin Airport]                | Airport the flight originated from                      | Feature         |
| sat [Scheduled Arrival Time]           | Scheduled arrival time                                  | Feature         |
| aat [Actual Arrival Time]              | Actual arrival time                                     | Feature         |
| set [Scheduled Elapsed Time (Minutes)] | Scheduled elapsed time (min)                            | Feature         |
| aet [Actual Elapsed Time (Minutes)]    | Actual elapsed time (min)                               | Feature         |
| delay [Arrival Delay (Minutes)]        | Time ahead of (-) or behind (+) scheduled arrival (min) | Outcome         |
| wot [Wheels-on Time]                   | Wheels-on time; time at flight touchdown                | Feature         |
| taxi [Taxi-In Time (Minutes)]          | Time between touchdown and recorded arrival time        | Feature         |

### Logan Airport Weather Data, 2019
Weather data was obtained from [OpenWeatherMap’s historical data API](https://openweathermap.org/history-bulk). The raw dataset contains meteorological (precipitation, wind strength and direction, conditions), as well as geographical (city, latitude, longitude) data per hour. Our model makes use of the following variables from this dataset:

| Variable [Original Name]               | Description                                             | Feature/Outcome |
|----------------------------------------|---------------------------------------------------------|-----------------|
| wind [wind_speed]                      | Wind speed at arrival (mph)                             | Feature         |
| rain [rain_1h]                         | Total rainfall during arrival hour (in)                 | Feature         |
| clouds [clouds_all]                    | Cloud cover percentage during arrival hour (%)          | Feature         |
| weather [weather_description]          | Weather conditions during arrival hour                  | Feature         |
