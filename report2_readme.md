# Report 2: Predicting Temperature
## By Zach Dyszel

# Data

The datasets were found on Kaggle and Our World in Data. 

Kaggle: https://www.kaggle.com/datasets/nelgiriyewithana/countries-of-the-world-2023

Our World in Data: https://ourworldindata.org/grapher/average-annual-surface-temperature

## Cleaning

First I imported both datasets using pandas and saved them as wdf and tdf. After loading the datasets, I first removed any columns I did not think would be fit for the training.

The columns I dropped were:

    Abbreviation, Armed Forces size, Calling Code, CPI, CPI Change (%),
    Capital/Major City, Currency-Code, Gasoline Price,
    GDP, Gross primary education enrollment (%),
    Gross tertiary education enrollment (%),
    Infant mortality, Largest city, Maternal mortality ratio,
    Minimum wage, Official language,
    Out of pocket health expenditure, Physicians per thousand,
    Population: Labor force participation (%), Tax revenue (%),
    Total tax rate, Unemployment rate

After dropping the columns I had to rename some countries in order to ensure when merging the datasets they would match

After renaming the countries in the temperature dataset, I then merged the two datasets on country name.

After combining the data, I created a list of all of the numeric data

    Latitude, Longitude, Forested Area (%),
    Agricultural Land (%), Co2-Emissions, Density(P/Km2),
    Land Area(Km2), Birth Rate, Fertility Rate,
    Life expectancy, Population, Urban_population

I then replaced any missing data based on mean of the countries in the same column

# Training

I first created a list of features

    Latitude, Longitude, Forested Area (%),
    Agricultural Land (%), Co2-Emissions, 
    Density(P/Km2), Land Area(Km2), Birth Rate, 
    Life expectancy, Population, Urban_population

Next I made the Latitude values absolute, to ensure that there is no negatives messing up the model.

Then I dropped the average temperature in the test subset

Next, I split the data with an 80/20 split and a random state of 42.

First I wanted to test the linear regression model.

First I fit the training data to the model.

Then I predicted the values in y_pred


Next I save this data to a txt file regression_data.txt

this file contains the mean absolute error, mean squared error and the r2 score

then I loaded the results into a dataframe

using these results I created a plot to display the actual average vs the prediction

results:

The linear regression model did fairly well. 

    MAE: 2.1463484170506333
    RMSE: 3.0851874652490556
    R²: 0.8608534320542258


I did the same thing for the random forest but I added 100 estimators, and set the random_state to 42.

tbe random forest did okay but not as good as the linear regression model.

    MAE: 2.6359688326944433
    RMSE: 4.322140974371513
    R²: 0.7269090937579046


Lastly I trained a decision tree model. This model was by far the worse at predicting the temperature.

    MAE: 2.8949816303505282
    RMSE: 4.562328763277123
    R²: 0.6957136032235482

the model was trained with a max depth of 6 and a random state of 42


# Results

Overall the models were not able to get a really good prediction for the temperature. 

Out of all three the linear regression performed the best.

Its top 3 features were

Latitude, Forested Area, and surprisingly birth rate.

The next best performing one was the random forest.

this models top 3 features was latitude, density, and longitude.

The worst model was the decision tree regressor.

Its top features were also latitude density and longitude

