# Renfe_EDA_Project

# Data Analysis and Preprocessing: Renfe Ticket Prices 🚄

This repository contains a project purely focused on **data cleaning, exploratory data analysis (EDA), and preprocessing**. This is the fundamental and most crucial step before training any Machine Learning algorithm.

## 🎯 Project Objective
The goal is to transform a "raw" dataset (real ticket search data from the Renfe website) into a clean, numerical format, ready to be ingested by a predictive model that attempts to estimate ticket prices.

## 🛠️ Tools & Technologies
- **Language:** Python
- **Data Manipulation:** Pandas, Numpy
- **Visualization:** Matplotlib, Seaborn, Plotly (for interactive maps)

## 🧹 The Data Wrangling Process
Real-world data is never perfect. This project covers the following key phases to ensure data quality:

1. **Handling Nulls and Duplicates:** Removed duplicate rows and records with missing data in key columns (like ticket class or fare type). Null values in the `price` column were imputed (filled) using the statistical mean. Outliers (such as tickets priced at 0€) were detected and removed.

2. **Feature Engineering:** Machines don't understand dates in text format. We extracted the day, month, day of the week, and exact departure time into separate columns. A highly valuable new variable was also calculated: **travel time** (subtracting departure time from arrival time). Finally, the dataset was merged with an external coordinate file (`coordenadas_ciudades.csv`) to add geospatial context.

3. **Categorical Variable Encoding (One-Hot Encoding):** Mathematical algorithms cannot read categorical words like "Tourist" or "Promo". A technique called *One-Hot Encoding* was applied, transforming these categories into new columns of zeros and ones. The dataset went from having 13 raw columns to 58 structured features ready for modeling.

## 💡 EDA Conclusions
During visual exploration and correlation analysis, a crucial finding emerged for the future predictive model. 

**Price depends on categories, not numbers.** No strong correlation (greater than 0.5) was found between the ticket price and purely numerical variables (like travel duration in minutes or city coordinates). This indicates that the future price-predicting algorithm will need to give much more weight to categorical variables, such as `fare_type`, `class`, or `train_type`.
