# Demand Forecasting for B2B manufacturers using Machine Learning

This repository contains  a machine learning-based demand forecasting model tailored for manufacturers operating within the B2B environment. These manufacturers typically supply products to consumer goods companies, wholesalers, or retailers, rather than directly to end consumers. Our model was focused on short-term demand forecasting (a 6-month horizon) using readily accessible operational data, such as historical demand, order backlog levels, inventory levels across the distribution channel, and seasonal indicators. 

Manufacturing companies often struggle with demand forecasting despite having access to order backlog and inventory data. Traditional approaches rely on spreadsheets with inconsistencies and redundancies.


## Methods and Results

We structured the project in our Jupiter Notebook (Python notebook) into the following phases:
- Data Sourcing, Data Preparation and Exploratory Data Analysis (EDA)
- Model Setup and Implementation


### Data Sourcing, Data Preparation and Exploratory Data Analysis (EDA)

For the model development, we used the Historical Product Demand dataset from Kaggle (https://www.kaggle.com/datasets/felixzhao/productdemandforecasting/data).
The dataset included historical product demand volumes between 2011-2017 for a manufacturing company with nearly 2,200 products.
The dataset included the following columns/attributes: (i) Product code, (ii) Warehouse, (iii) Product Category (parent attribute of product code), (iv) Date (when the customer needed the product), and (v) Order Demand (volume). We removed the Warehouse attribute and we added the following 3 attributes (we've created synthetic data for these new attributes):
- Channel inventory (levels of inventory of the manufacturer's products in th distribution channel)
- Order backlog
- High-season binary attrubute


### Model Setup and Implementation

We used the following input variables for the models:
- Average of the (i) order demand of the same month last year (reference period month), and order demand from the months (ii) prior to and (iii) following the reference period month
- Order backlog
- High-season binary attrubute
- Channel inventory

And our target (dependent) variable was order demand (volume) - this is what we tried to predict with the models.

We split our dataset into training data (2012-2015 data) and testing data (H1 2016 data)

We used the following main techniques 
- Multiple Linear Regression
- Polynomial Regression
- Random Forest Regressor
- XGBoost Regressor
- LSTM Neural Network

In addition, we also applied ensemble techniques.

### Results

<img width="617" alt="image" src="https://github.com/user-attachments/assets/92092d6e-e541-4c10-b692-242f2036d4a5" />

In addition, as the original Dataset was extremely volatile, we created a more normalized version of the dataset (in a separate version of our notebook) by eliminating part of the extreme volatility and we run the same prediction models on this more normalized dataset.
The table below compares the prediction results of the same models between the original (extremely volatile) and more normalized dataset:

<img width="952" alt="image" src="https://github.com/user-attachments/assets/b698b6e9-44c5-4d5d-bc9e-2de038d23def" />



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
