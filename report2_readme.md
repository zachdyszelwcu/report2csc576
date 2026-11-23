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

