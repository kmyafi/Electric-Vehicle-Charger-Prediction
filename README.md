# Forecasting the Number of Electric Vehicles in Washington State Using ARIMA Time Series Analysis

> **Credits :**
> 1. Diki Wahyudi
> 2. Jefta Adriel Heryadi
> 3. Kamal Muftie Yafi

## Introduction
In this modern era, technology is developing more and more rapidly. The emergence of electric vehicles adds another "choice" to society in choosing the type of vehicle to buy/use. Therefore, it is important to know the trends in the use of electric vehicles. In this project, we will use Electric Vehicle Title and Registration Activity data to model the number of electric vehicles in Washington state.

## Data
We used Washington State's [dataset of electric vehicle title and registration activity](https://catalog.data.gov/dataset/electric-vehicle-title-and-registration-activity) [accessed on August 24, 2023] which included a total of 781,713 transactions.

## Methods
After accessing the dataset, we did several preprocessing steps for the data as well as looking up into the internet to gain more insight regarding the domain knowledge of EV businesses. We then dropped several columns that aren't insightful, filtered the data to only keep the "Original Title" or "Transfer Title" in order to focus on the "real" puchase of EV (not registration renewal), created a new feature from "DOL Transactionn Date" to reflect the only month and year of the transaction date. 

We then filtered the data to keep only the last transaction that happened on every specific car's ID, dropped the missing values because the amount is less than 1% and impute some of them to "Unknown", filtered the data to only keep the Washington "State of Residence", and finally standardized the name of the cars model.

Using this preprocessed dataset, we proceed to worked on the Exploratory Data Analysis (EDA) and created visualizations. Then we moved to the modeling.

The modelling process was the same for each county, which consisted of 2 parts. The first part is by using all of the data in that county, and then used seasonal decomposition to see the trend, seasonality and stationarity assumption, split the data into training and testing (80%:20%), used auto.arima() to create the SARIMAX model, evaluated the model (to see whether the model holds the assumption that are needed), used the model to predict the dataset and see the Mean Absolute Percentage Error (MAPE), Root Mean Squared Error (RMSE), and R-Squared.

The second part process process is by using the data in that county that are only from 2020. After that we split the data into training and testing (80%:20%), used auto.arima() to create the SARIMAX model, evaluated the model (to see whether the model holds the assumption that are needed), used the model to predict the dataset and see the Mean Absolute Percentage Error (MAPE), Root Mean Squared Error (RMSE), and R-Squared, compared this model to the first part model, and then choosed the model that minimizes MAPE and RMSE, and maximize R-Squared.

The model that were chosen from each county then were used to predict the total number of EV for their respective county from August 2023 to July 2026.
