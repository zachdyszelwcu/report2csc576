# Report 2: Predicting Countries Temperatures
CSC 576
By Zach Dyszel

In Report 1, I explored the relationship between average temperature, forest coverage, and urbanization. For Report 2, I wanted to see if I could predict a country's average annual surface temperature based on its geographic, environmental, and demographic characteristics.

## Data

The datasets used in this project were found on Kaggle and Our World in Data. 

- Kaggle: https://www.kaggle.com/datasets/nelgiriyewithana/countries-of-the-world-2023

- Our World in Data: https://ourworldindata.org/grapher/average-annual-surface-temperature

The temperature dataset was filtered to only include 2023. Both datasets were cleaned and merged based on country name, resulting in 176 rows and 15 columns.

Each row represents one country.

## Features

The following 11 features were used to predict average temperature:

- Absolute latitude
- Longitude
- Forested area (%)
- Agricultural land (%)
- CO2 emissions
- Population density
- Land area
- Birth rate
- Life expectancy
- Population
- Urban population

The target variable is average annual temperature, and it is measured in degrees Celsius.

## Models and Results

The data was split into an 80/20 training and testing split using a random state of 42. There were 140 countries in the training set and 36 countries in the testing set.

The baseline predicts the average temperature of the training set for every country in the testing set.

| Model | MAE (°C) | RMSE (°C) | R² |
|---|---:|---:|---:|
| Baseline | 7.235 | 8.462 | -0.047 |
| Linear Regression | 2.145 | 3.083 | 0.861 |
| Random Forest (100 estimators) | 2.635 | 4.328 | 0.726 |
| Decision Tree (max_depth=6) | 2.895 | 4.562 | 0.696 |

Linear regression performed the best out of the three models, with a mean absolute error of 2.145 °C, and an R² score of 0.861.

Random Forest performed the second best, and has a mean absolute error of 2.635 °C, and a R² score of 0.726.

Decision Tree with a max depth of 6 performed the worse. It had a mean absolute error of 2.895, and a R² score of 0.696

All three models performed better than the baseline.

Latitude was the feature that all three models relied on the most when predicting temperature.

