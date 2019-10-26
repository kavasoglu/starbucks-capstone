# Udacity Starbucks Capstone project

## About The Project

In this project we are going to build a machine learning(ML) project to figure out effective offers for individual customers.  

There are three types of promotional offers that can influence purchasing decisions of customers: buy-one-get-one (BOGO), discount, and informational. In a BOGO offer, a user needs to spend a certain amount to get a reward equal to that threshold amount. In a discount, a user gains a reward equal to a fraction of the amount spent. In an informational offer, there is no reward, but neither is there a requisite amount that the user is expected to spend.

## Project Scope

A supervised learning model is built in this project to identify if an offer is going to be completed by a customer or not. To achieve this, user actions need to be understood.  
Action data is stored in the `transcript` dataset. There are 4 types of events like `offer received`, `offer viewed`, `offer completed` and `transaction`.  

An effective offer is the completed one after it is viewed by the relevant customer. Merely completing an offer does not mean if that was the effective offer or not, because the offer can be naturally completed by the routine customer behavior. So, expected user action series follow `offer viewed` -> `transaction` ->  `offer completed` pattern.  

`offer received` is not a user action and, it can be treated as like a system log. So, we can filter out these events from our ML input dataset.  

We made an assumption based on user behavior such that we treated transactions within a valid offer period are affected by that offer. We can't say this for sure, a transaction  might be just related to usual user habit, but it can be because of the offer as well. So, we made that assumption and calculated the total transaction amount during the valid offer period. Even if a transaction is not affected by an offer, this assumption can still be valuable since it provides financial info to the model.    

### Dataset overview

There are 3 different datasets:

**profile.json**: Rewards program users (17000 users x 5 fields)
gender: (categorical) M, F, O, or null
age: (numeric) missing value encoded as 118
id: (string/hash)
became_member_on: (date) format YYYYMMDD
income: (numeric)
portfolio.json
Offers sent during 30-day test period (10 offers x 6 fields)

**portfolio.json**: Offers sent during 30-day test period (10 offers x 6 fields)
reward: (numeric) money awarded for the amount spent
channels: (list) web, email, mobile, social
difficulty: (numeric) money required to be spent to receive reward
duration: (numeric) time for offer to be open, in days
offer_type: (string) bogo, discount, informational
id: (string/hash)
transcript.json

**transcript.json**: Event log (306648 events x 4 fields)
person: (string/hash)
event: (string) offer received, offer viewed, transaction, offer completed
value: (dictionary) different values depending on event type
offer id: (string/hash) not associated with any "transaction"
amount: (numeric) money spent in "transaction"
reward: (numeric) money gained from "offer completed"
time: (numeric) hours after start of test

### Data Preprocessing

These 3 datasets are cleaned and pre-processing operations are done on each of them to create a unified view of the data to obtain the input dataset for a ML model.  

The ML input data fields:
completed: (binary) shows if an offer is completed by a user
difficulty, duration, offer_id(id), reward, type(offer_type): these fields come from *portfolio.json*
social, email, mobile, web: these fields are encoded by extracting `channels` in *portfolio.json*
start_time: offer start time
transaction_amount: total transaction amount during a valid offer
age, gender, income:  these fields come from *profile.json*
became_member_diff: number of days beginning from a user became a member till `2018-01-01`. (1)  

(1) '2018-08-01' is a magical datetime which is a rounded value of the max value for `became_member_on` in *profile.json*. When this dataset is actually generated is unknown so, elapsed time is calculated till that date.  

## Requirements & How to Run
- Python 3
- Jupyter notebook

Run `jupyter notebook` in the project folder to access `Starbucks_Capstone_notebook.ipynb` on your web browser, then execute and check notebook cells.  
