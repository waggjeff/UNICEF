# Task 1 - An Analysis of Porejimo Supply Chain Disruptions
## Jeff Wagg (February 22, 2024)

## Background

The Republic of Porejimo faces significant challenges with the diversion of humanitarian supplies, which hinders the provision of timely and quality aid to vulnerable populations. Diversions can relate to different sections of the supply chain for bringing humanitarian supplies to intended aid recipients. One of the key reasons known for the diversions is the loss of stock due to a growing black market for the packaging materials the aid materials are transported in.

Recently, there has been a notable increase in the prices for specialized packaging materials. This has raised concerns that inventories are being diverted from loading warehouses before getting to the distribution points to be sold in the black market where they attract high prices.

Using the five datasets provided, the Country Office of the Republic of Porejimo would like to make a prudent decision about a potential intervention to address the issue. They would have requested science expertise to help address the following questions:

- Are the market prices for the packaging materials explaining the diversion of humanitarian supplies?

- What other factors might be explaining the diversion of humanitarian supplies?

- What else should the Country Office think about to understand the situation (for example, any reason to suspect the data quality)?

Data analysis and results are presented in the accompanying Python Jupyter notebook: 'Task1_Porejimo_JFW.ipynb'. 

## Data and Cleaning

The five datasets provided include prices for two differents types of packaging, market prices for three types of humanitarian supplies, mass of quantities for the three different supplies delivered to both the loading warehouse and the distribution points, and daily information on the weather conditions. We begin by importing these datasets into Python DataFrames in our Jupyter notebook and performing some initial cleaning and formatting. In particular, we convert the 'data' column of each dataset into datetime format for ease of future comparison. 

When examining the data, it was also found that one of the date entries in the 'weather.csv' file required editting, which we corrected in our code. We also noted a number of missing data points, which we have replaced with the mean value of the column in which these data are found. 

In order to further clean our data and prepare it for modelling, we have concatenated all of the datasets into one DataFrame, using the date time column. This leaves us with a dataset containing 62 entries. 

## Feature Engineering

## Machine Learning Models

## Correlations Between Features

## Conclusions and Recommendations

## Appendix - Figures

![image](https://github.com/waggjeff/UNICEF/assets/33003589/f75ef78b-8ad4-4df2-9f73-88c75ea8830a)

![image](https://github.com/waggjeff/UNICEF/assets/33003589/a19f679b-6870-4576-8167-0a09f729644d)

![image](https://github.com/waggjeff/UNICEF/assets/33003589/404e1968-66cf-434b-87f6-bdae552386ba)
