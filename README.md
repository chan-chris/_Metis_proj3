# Metis_proj3

Readme.txt

Date: 02/11/2021

Project Title: Predicting the next hit song using Classification methods

Description: The purpose of the project is to predict whether a song will make it to the Billboard Hot 100 Charts

Data:
The data I used was publicly avaialble based on a previous research project. A link to the data: http://cs229.stanford.edu/proj2018/report/16.pdf
The data is based on ~14000 songs with a mix of billboard 100 songs and random songs from the Million Song Dataset: http://millionsongdataset.com/

I supplemented the data using Spotify's API with other Artist/Song attributes that were not originally provided - genre, track popularity,
time signature, release year. I uploaded the data to a postgressql server and retreived for analysis.

Features and Target Variables: 
The target variable is the song was on the Billboard Hot 100 between 1990-2018
Features are mostly audio feature scores pulled from Spotify's API

Programs:
There are several programs for different models, however I focused mostly on logistic regression, random forest and xgb after the intial 
base model runs (00_base_models).
I select 07_xgb_mod_h100.ipynb as my primary model and program. I output a new analytic file with predictions and predicted probabilities
to analyze the hits and misses. The program to analyze my predictions is in 99_investigations.

. data_extract_bb_features.ipynb: this program uses song id info for billboard 100 songs and extracts features from Spotify's API
. data_extract_sb_features.ipynb:  this program uses song id info for non billboard 100 songs and extracts features from Spotify's API

. 01_create_postgressql.ipynb: Create the postgressql DB to house song data
. 02_data_clean.ipynb: Simple data frame cleaning
. 02b_eda.ipynb: EDA and graph production
. 02c_base_models.ipynb: run baseline models for all models prior to further exploration
. 03_lr_mod_h100.ipynb: logistic regression modeling + tuning
. 04_dt_mod_h100.ipynb: decision tree modeling
. 05_rf_mod_h100.ipynb: random forest modeling + tuning
. 06_knn_mod_h100.ipynb: knn modeling
. 07_xgb_mod_h100.ipynb: XGb modeling + tuning
. 08_nb_mod_h100.ipynb: naive bayes modeling
. 99_investigations.ipynb: final analysis of test data and predictions

Summary:
Based on EDA, model scores and evaluation metrics, I narrowed my focus on LR, RF and XGb models. 
XGB performed slightly better when looking at precision and recall and 
eventually decided to tune further.
Having raised my probability threshold to 0.65 to capture more precision, I ended up with a model with a precision of 0.84 and recall of 0.80.
The investigations program reviewed some positive, negative and edge cases of my predictions.
The model can be improved to incorporate more artist profile info vs. just audio features.
We may also benefit by looking at F1 beta scores vs. simply precision.