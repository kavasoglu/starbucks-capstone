# Udacity Starbucks Capstone project

## About The Project
In this project we are going to build a ML project to choose specific offers for individual customers.  
There are three types of promotional offers that can influence purchasing decisions of customers: buy-one-get-one (BOGO), discount, and informational. In a BOGO offer, a user needs to spend a certain amount to get a reward equal to that threshold amount. In a discount, a user gains a reward equal to a fraction of the amount spent. In an informational offer, there is no reward, but neither is there a requisite amount that the user is expected to spend.

## Requirements & How to Run
- Python 3
- Jupyter notebook

Run `jupyter notebook` in the project folder to access `Starbucks_Capstone_notebook.ipynb` on your web browser, then execute and check notebook cells.

## Dataset overview
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
