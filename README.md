# Demand Forecasting for B2B manufacturers using Machine Learning

This project applies machine learning techniques to build a demand forecasting model tailored for manufacturers operating in the B2B sector. Unlike B2C environments, these manufacturers typically supply products to wholesalers, distributors, or retailers. Our focus was on short-term demand forecasting (6-month horizon) using easily accessible operational data such as historical demand, order backlog, inventory levels across distribution channels, and seasonal indicators.

Accurate demand forecasting remains a key challenge for many manufacturers, even with access to backlog and inventory data. Traditional spreadsheet-based approaches often lead to inconsistencies and inefficiencies. This project demonstrates how machine learning models can provide more reliable forecasts.


## Project Workflow

The project was developed in Jupyter Notebooks and divided into two main phases:
- Data Sourcing, Data Preparation and Exploratory Data Analysis (EDA)
- Model Setup and Implementation


### Data Sourcing, Data Preparation and EDA

For the model development, we used the Historical Product Demand dataset from Kaggle (https://www.kaggle.com/datasets/felixzhao/productdemandforecasting/data).
The dataset included historical product demand volumes between 2011-2017 for a manufacturing company with nearly 2,200 products.
The original dataset included the following columns/attributes:
- Product code,
- Warehouse,
- Product Category (parent attribute of product code),
- Date (when the customer needed the product),
- Order Demand (volume).
For our analysis, we removed the Warehouse attribute and we added the following 3 attributes (we've created synthetic data for these new attributes):
- Channel inventory (levels of inventory of the manufacturer's products in the distribution channel)
- Order backlog
- High-season binary attrubute


### Model Setup and Implementation

We defined Order Demand (volume) as the target variable.
The following input features were used:
- Average of the (i) order demand of the same month last year (reference period month), and order demand from the months (ii) prior to and (iii) following the reference period month
- Order backlog
- High-season binary attrubute
- Channel inventory

The dataset was split into:
- Training set: 2012–2015 data
- Testing set: First half of 2016

We applied the following main techniques 
- Multiple Linear Regression
- Polynomial Regression
- Random Forest Regressor
- XGBoost Regressor
- LSTM Neural Network

In addition, we experimented with ensemble approaches.


### Results

<img width="617" height="506" alt="11" src="https://github.com/user-attachments/assets/1f91f9f6-658d-4c57-b446-86a14bcc5cc5" />


In addition, as the original Dataset was extremely volatile, we created a more normalized version of the dataset (in a separate version of our notebook) by eliminating part of the extreme volatility and we run the same prediction models on this more normalized dataset.
The table below compares the prediction results of the same models between the original (extremely volatile) and more normalized dataset:

<img width="953" height="457" alt="12" src="https://github.com/user-attachments/assets/8c795c95-f360-49b8-b673-21ade17c8edf" />


#### Required Python Packages

- kaggle
- os
- numpy
- pandas
- sklearn
- tensorflow
- GridSearchCV
- statsmodels 
- seaborn 
- matplotlib
- xgboost


#### Acknowledgements

This project was completed as part of the Machine Learning course in the Master of Applied Data Science (MADS) program at the University of North Carolina at Chapel Hill.

The work was a team collaboration by:
- Jason Huang
- Lalsa Pandit
- Attila Zsoter
