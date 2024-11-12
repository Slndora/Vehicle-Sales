# Vehicle-Sales
## Vehicle Sales Insights:A Comprehensive Analysis of Sales, Pricing, and Trends
![alt text]
## Objective
The objective of this project is to analyze a vehicle sales dataset to uncover key trends and factors influencing car prices and demand. By examining variables like make, model, condition, odometer, and sales data, the project aims to provide insights that help optimize pricing, inventory, and market strategies in automotive sales.
## Table of Contents
- [Table of Contents](#table-of-contents)
- [Data Overview](#data-overview)
- [Analysis Goals](#analysis-goals)
- [Methodology](#methodology)
- [Technologies Used](#technologies-used)
- [Importing the data](#importing-the-data)
- [Data Cleaning](#data-cleaning)
- [Data Manipulation](#data-manipulation)
- [SQL for Data Insights](#sQL-for-data-insights)
- [Insights Generated with SQL Queries](#insights-generated-with-sQL-queries)
- [Measures in Power BI](#measures-in-power-bI)
- [Dashboard](#dashboard)
- [Acknowledgments](#acknowledgments)
 
## Data Overview
This dataset provides information on used car sales, including key variables that capture various attributes of the cars,

such as their make, model, year of manufacture, transmission type, odometer reading, and selling price. The dataset also

contains additional details about the condition of the cars, state of sale, and more.

Key columns in the dataset:

1) Year: The year the car was manufactured.

2) Make: The brand of the car.

3) Model: The specific model of the car.

4) Trim: A variant or version of the model with different features.

5) Body: The type or category of the car (e.g., SUV, Sedan).

6) Transmission: Type of transmission (automatic or manual).

7) VIN: Vehicle Identification Number (unique identifier for each car).

8) State: The state where the car is sold.

9) Condition: The condition of the car when sold (e.g., new, used).

10) Odometer: Number of miles the car has been driven.

11) Color: The exterior color of the car.

12) Interior: The interior color/material of the car.

13) Seller: The seller of the car.

14) MMR: Manheim Market Report value (provides a price benchmark for the vehicle).

15) Selling Price: The actual selling price of the car.

16) Sale Date: The date the car was sold.


![Alt text]


## Analysis Goals
Here are key analysis goals for your vehicle sales dataset:

1) Price Determinants: Identify the factors (e.g., make, model, year, condition, odometer) that most significantly influence the selling price of vehicles.
2) Sales Trends: Analyze sales trends over time (e.g., by year, month, or season) to determine peak sales periods and seasonal patterns.
3) Market Segmentation: Segment the market based on attributes like vehicle type (body style), condition (new vs. used), or seller to understand specific market behaviors and preferences.
4) Geographic Analysis: Explore sales performance across different states, identifying regional variations in demand, pricing, and vehicle preferences.
5) Condition and Pricing Relationship: Investigate how vehicle condition (new vs. used) affects pricing, including price depreciation for used vehicles based on mileage and age.
6) Odometer and Price Correlation: Examine how the number of miles a vehicle has been driven (odometer) correlates with its selling price, to understand depreciation patterns.
7) Model and Trim-Level Analysis: Evaluate how specific vehicle models and their trim variations affect sales and pricing, identifying premium vs. base model trends.
8) Seller Performance: Assess how different sellers influence vehicle pricing and sales volume, identifying top-performing sellers and potential pricing strategies.
9) VIN and Unique Vehicle Characteristics: Identify unique characteristics or anomalies related to specific VINs and their impact on sales price or sales volume.
10) Comparison with MMR: Compare actual selling prices with the Manheim Market Report (MMR) values to assess pricing accuracy and market competitiveness.
These goals aim to provide actionable insights for pricing strategies, inventory management, and understanding market dynamics within the automotive sales industry.

## Methodology
- Data Cleaning & Preparation: Ensure data integrity and consistency across all tables.
- Descriptive Analysis: Generate summary statistics and visualizations to identify trends.
- Inferential Analysis: Apply statistical methods to test hypotheses and draw conclusions.
- Data Visualization: Utilize tools like Power BI to create interactive dashboards.

## Technologies Used
1) Python (for Exploratory Data Analysis - EDA): Python was used for conducting thorough exploratory data analysis (EDA) on the vehicle sales dataset. Key libraries such as Pandas were used for data manipulation and cleaning, Matplotlib and Seaborn for data visualization, and NumPy for numerical operations. Python enabled the analysis of relationships between different variables (e.g., price, odometer, condition) and allowed for statistical analysis, trend detection, and data transformation to prepare insights for further visualization.
2) Power BI (for Data Visualization): Power BI was employed to create interactive and insightful visualizations from the processed dataset. The platform's drag-and-drop interface facilitated the creation of dashboards that allow for easy exploration of trends, distributions, and comparisons in the vehicle sales data. Visualizations such as bar charts, scatter plots, line graphs, and geographical maps provided a clear, accessible way to communicate key insights and patterns to stakeholders.

## Importing the data
To begin the analysis, I imported the vehicle sales dataset from a CSV file into Python using the Pandas library. The pd.read_csv() function was used to load the dataset into a DataFrame, which allowed for efficient data manipulation, cleaning, and analysis. This step enabled me to explore and preprocess the dataset before performing any exploratory data analysis (EDA).

```
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
import seaborn as sns
import plotly.express as px
import warnings
warnings.filterwarnings("ignore")
df=pd.read_csv('C:/Users/akash/Downloads/.kaggle/car_prices.csv')
df.head()




