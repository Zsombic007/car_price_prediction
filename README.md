# Car Price Prediction 🚘🚗💸💵

Predicting used car price based on basic parameters of a car. (Like brand, model, type of engine, fuel type, kms driven, previous owners etc...)

I have done this project on three differenct approaches.

    1. RandomForestReggressor
    2. DummyRegressor
    3. small Neural Network

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/drive/1NRkQoXENJTx3TqrdhVQFmgVReBohDtha?usp=sharing)

## Contents
1. [Dadataset](#dataset)
2. [Preprocessing](#preprocessing)
3. [Models](#models)
4. [Results](#results)
5. [How to run](#how-to-run)
6. [Limitations and ides](#limitations-and-ideas)
7. [Credits](#credits)

## Dataset
- File: `car_price.csv` used car listing the prices are orignially in Indian rupees
- Source: from Kaggle sadly i can't put the link to the dataset. It came with a pretty good tutarial too
- Original size: 5512 rows x 10 columns
- After droping the rows one with missing values it gor reduced to 5389 rows
- Columns: car_name, car_prices_in_rupee, kms_drive, fuel_type, transmission, ownership, manufacture, enige, Seats
- 
