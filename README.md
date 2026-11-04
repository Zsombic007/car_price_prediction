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

This repo doesn't include the dataset, because i have no inframtion about if it can be shared.  

## Preprocessing

Every step is included in the notebook about processing the data for traning and testing
- Droped the `Unnamed: 0` column
- Split the `car_name` into two different column one is `manufacturer` and the other is nammed `model`
- Cleaned text-formatted numbers: removed the `kms` from `kms_driven`, `cc` from `engine`, ` Seats` from `Seats` and kept only the digit from `ownership` (1st owner -> 1...).
- Converted prices from `Lakh` / `Crore` text (×100,000 / ×10,000,000) into numbers, then to US dollars at a fixed rate of 0.012 USD per rupee.
- Label-encoded `manufacturer`, `model`, `fuel_type`, and `transmission`
- Dropped rows with missing values.

**Features (9):** manufacturer, model, year of manufacture, kilmoeters driven, engine size, fuel type, tranmission, seats, ownership.

**Target:** price in USD

**Split:** 80 % train / 20 % test (`random_state=42`) -> 4,311 training and 1,078 test samples.

## Models
| Model | Configuration |
| --- | --- |
| `DummyRegressor` | `strategy="median"` |
| `RandomForestRegressor` | `n_estimators=1500`, `max_depth=50`, `random_state=42` |
| Neural network (Keras `Sequential`) | `Dense(64, relu)`->`Dense(32, relu)`->`Dense(1)`;<br> 2,753 parameters; Adam optimizer, MSE loss, 25 epochs, batch size 1|

##Results

Evaluated on the held-out test set (prices in USD):

| Model | RMSE | MAE | R² |
|---|---|---|---|
| DummyRegressor (median) | 24,853 | 9,807 | -0.095 | 
| RandomForestRegressor | **6,841** | **2,5555** | **0.917** | 
| Neural network | 22,749 | - | - |

- The Random Forest clearly beats the baseline and explains about 92% of the variance in test prices
- Its R² on the training set is 0.981, so it fits the trainig dara noticeably better than unseen data (some overfitting).
- The neural network is only slightly better the median baseline in this setup (see ides below).
  
![alt text]("https://github.com/Zsombic007/car_price_prediction/blob/main/images/rmse.png?raw=true")
