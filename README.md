# Task 1 - An Analysis of Porejimo Supply Chain Disruptions
## Jeff Wagg (February 22, 2024)

## Background

The Republic of Porejimo faces significant challenges with the diversion of humanitarian supplies, which hinders the provision of timely and quality aid to vulnerable populations. Diversions can relate to different sections of the supply chain for bringing humanitarian supplies to intended aid recipients. One of the key reasons known for the diversions is the loss of stock due to a growing black market for the packaging materials the aid materials are transported in.

Recently, there has been a notable increase in the prices for specialized packaging materials. This has raised concerns that inventories are being diverted from loading warehouses before getting to the distribution points to be sold in the black market where they attract high prices.

Using the five datasets provided, the Country Office of the Republic of Porejimo would like to make a prudent decision about a potential intervention to address the issue. They have requested data science expertise to help address the following questions:

- Are the market prices for the packaging materials explaining the diversion of humanitarian supplies?

- What other factors might be explaining the diversion of humanitarian supplies?

- What else should the Country Office think about to understand the situation (for example, any reason to suspect the data quality)?

Data analysis and results are presented in the accompanying Python Jupyter notebook: 'Task1_Porejimo_JFW.ipynb'. 

## Data and Cleaning

The five datasets provided include prices for two differents types of packaging, market prices for three types of humanitarian supplies, mass of quantities for the three different supplies delivered to both the loading warehouse and the distribution points, and daily information on the weather conditions. We begin by importing these datasets into Python DataFrames in our Jupyter notebook and performing some initial cleaning and formatting. Specifically, we convert the 'date' column of each dataset into datetime format for ease of future comparison. 

When examining the data, it was also found that one of the date entries in the 'weather.csv' file required editting, which we corrected in our code. We also noted a number of missing data points, which we have replaced with the mean value of the column in which these data are found. 

In order to further clean our data and prepare it for modelling, we have concatenated all of the datasets into one DataFrame using the date time column. This leaves us with a dataset containing 62 entries. 

## Feature Engineering

We have been given the information that some supplies are possibly being diverted from the loading warehouse before reaching the distribution sites. It is therefore useful to create three new features which are the 'losses' (in kg) that have occurred for each of the three supplies on a given date. We assume that the supplies are transported between the loading warehouse and distribution point on the same day, which would allow us to calulate a difference between the mass of the supply item at the two locations. 

## Machine Learning Models

At this stage, we want to develop a machine learning model with the existing data that can be used to predict the cost of the packaging material. The goal is to see whether there are features in the data which are correlated with the cost of packaging (e.g. mass loss of supply item A, B, or C). We assume that packaging materials A and B might be used to package any of supply items A, B, or C, and that supply item A is not necessarily packaged using material A.   

We begin by developing a simple multi-target linear regression model. The two target variables are the prices of the packaging material (px_matA and px_matB), while for model features we use the prices of the three supplies, the reduction in mass of each supply item between loading and distribution points, and the weather data. The training and testing datasets are created with an 80:20 split, in order to ensure sufficient data exist for model fitting.  

In spite of the small dataset, our linear reggression model does a very good job of predicting the packaging material prices on a given day with a mean-squared error of 0.084 USD. We then examine the correlation coefficients of the model fits to determine which feature is more important when predicting package price. The results are shown in Figures 1 and 2 for the feature importance in the models used to predict the price of packaging materials A and B, respectively. In both cases, we find that the price of supply item C is most strongly correlated with the price of packaging material. This would suggest that external economic factors are driving the prices of these items (rather than theft of packaging). 

## Correlations Between Features

In order to further explore these results, we plot the correlation matrix between all features in our data (Figure 3). We confirm the correlation between the price of supply item C and the prices of the packaging material, while also making a fascinating discovery. From the matrix we see that the amount of supply material lost exhibits a strong inverse correlation with the temperature of a given day. This may provide clues as to the origin of the losses. 

## Conclusions and Recommendations

In conclusion, our analysis suggests that any loss (or theft) of material is not responsible for the rise in costs of packaging material. 

## Appendix - Figures

![image](https://github.com/waggjeff/UNICEF/assets/33003589/f75ef78b-8ad4-4df2-9f73-88c75ea8830a)

Figure 1: Model correlation coefficients for each of the features used in our linear regression model when predicting the price of packaging material A. It appears that the price of supply item C is the most important factor when predicting packaging price. 

![image](https://github.com/waggjeff/UNICEF/assets/33003589/a19f679b-6870-4576-8167-0a09f729644d)

Figure 2: Model correlation coefficients for each of the features used in our linear regression model when predicting the price of packaging material B. It appears that the price of supply item C is once again the most important factor when predicting packaging price. 

![image](https://github.com/waggjeff/UNICEF/assets/33003589/404e1968-66cf-434b-87f6-bdae552386ba)

Figure 3: Correlation matrix for the features in our analysis. It is worth noting that the daily temperature appears to be anti-correlated with the amount of supplies lost between the loading warehouse and the distribution point. 
