## Introduction

This data set contains simulated data that mimics customer behavior on the Starbucks rewards mobile app. Once every few days, Starbucks sends out an offer to users of the mobile app. An offer can be merely an advertisement for a drink or an actual offer such as a discount or BOGO (buy one get one free). Some users might not receive any offer during certain weeks.

Not all users receive the same offer, and that is the challenge to solve with this data set.

The goal of this project is to combine transaction, demographic and offer data to determine which demographic groups respond best to which offer type. This data set is a simplified version of the real Starbucks app because the underlying simulator only has one product whereas Starbucks actually sells dozens of products.

Every offer has a validity period before the offer expires. As an example, a BOGO offer might be valid for only 5 days. You'll see in the data set that informational offers have a validity period even though these ads are merely providing information about a product; for example, if an informational offer has 7 days of validity, you can assume the customer is feeling the influence of the offer for 7 days after receiving the advertisement.

The transactional data shows user purchases made on the app including the timestamp of purchase and the amount of money spent on a purchase. This transactional data also has a record for each offer that a user receives as well as a record for when a user actually views the offer. There are also records for when a user completes an offer.

Note that someone using the app might make a purchase through the app without having received an offer or seen an offer.

## Project Motivation

This is my capestone project for the Data Scientist Nanodegree from Udacity. Therefore, I was very excited to work on it, applying the techniques I have learnt in this course. I am also very excited to share the results with other fellow data scientists / data analysts.

## Installation

Python 3: 

Jupyter Notebook, json, pandas, Numpy, datetime, matplotlib.pyplot, seaborn, sklearn

## File Description

The Jupyter Notebook contains scripts for data wrangling, data exploration, and modeling.

The Visuals folder contains visuals for the project.

## Business Questions

In this project, I will use the Starbucks's data to indentify different user groups and answer these two questions:

1. Which groups of people are most responsive to each type of the three offers, including discount, buy one get one for free (bogo), and informational.


2. How can we best present each type of offer i.e. email, mobile, web, or social, to the users? 

## About the data

The data is contained in three files:

* portfolio.json - containing offer ids and meta data about each offer (duration, type, etc.)
* profile.json - demographic data for each customer
* transcript.json - records for transactions, offers received, offers viewed, and offers completed

Here is the schema and explanation of each variable in the files:

**portfolio.json**
* id (string) - offer id
* offer_type (string) - type of offer ie BOGO, discount, informational
* difficulty (int) - minimum required spend to complete an offer
* reward (int) - reward given for completing an offer
* duration (int) - time for offer to be open, in days
* channels (list of strings)

**profile.json**
* age (int) - age of the customer 
* became_member_on (int) - date when customer created an app account
* gender (str) - gender of the customer (note some entries contain 'O' for other rather than M or F)
* id (str) - customer id
* income (float) - customer's income

**transcript.json**
* event (str) - record description (ie transaction, offer received, offer viewed, etc.)
* person (str) - customer id
* time (int) - time in hours since start of test. The data begins at time t=0
* value - (dict of strings) - either an offer id or transaction amount depending on the record
 
## Some key results

#### Who were more likely to respond?

![Response 1](https://github.com/Kilie/starbucks/blob/master/Visuals/response%20rate%201.png)

Customers' gender, joining year (became_member_on), income, and age all seemed to affect the response rate, although it's notable that the difference in the mean age between the response and non-response groups was only three year old.

Overall, customers who were female, became members during 2015-2017, and had higher income were more likely to respond to the offers than others.

#### Which offer types had the most response?

Overall, discount offers seemed to have higher response rates compared to bogo offers. Informational offers didn't seem to relate to any responses, so I won't discuss this type further with differnt demographic features.  

- **Gender**

Female and 'O' customers had higher response rates than male customers to both bogo and discount offers, and this trend is stronger for bogo offers. 

The reason for this was that female as well as 'O' customers seemed to respond similarly to different offer types, whereas male customers seemed to respond more to discount offers than bogo offers.

- **Joining year**

Bogo offers appeared to have higher response rates from customers who became members during 2015-2017 than those who became member in other years. 

Discount offers, on the other hand, had relatively similar response rates from customers who became members during 2013-2017, with customers from 2018 having the a much lower response rate compared to those from other years.

- **Age and income**

For both bogo and discount offers, responsive customers seemed to have older ages and higher income than their unresponsive counterparts, and the income difference was bigger between responsive and unresponsive groups than the age differnce. 

In addition, the difference between response groups was bigger for bogo offers than for discount offers.

#### Which channels had the most response?

In general, social media and web appeared to have higher response rates (73% and 70%, respectively) than mobile and email channels (66% and 65%, respectively). 

- **Gender** 

Female and 'O' customers seemed to have higher response rates than male customers for all channels, and all three genders responded more to social media offers and web than to mobile and email. 

However, unlike the general trend in which social median had the highest response rate, 'O' customers seemed to have the highest response rate to web offers, indicating a close connection between customers from this gender group and web.

- **Joining year**

For all channels, customers who became members during 2015-2017 appeared to have higher response rates than those who became members in other years. Channels didn't seem to affect this trend among joining years.

- **Age and income**

Similar to offer types, all channels seemed to have older ages and higher income in the responsive group compared to the unresponsive group, and income difference was bigger between responsive and unresponsive groups than the age differnce.  


#### Who were more likely to spend more?

Overall, customers who responded to the offers seemed to spend more money on average (about 17 dollars) than those who didn't respond (about 11 dollars), suggesting that it is indeed important to take measures to improve the response rate.

- **Gender**

Female customers seemed to spend the most, followed by 'O' and male customers. 

- **Joining year**

Customers who became members during 2015-2018 seemed to spend more than thos who bemame members earlier than 2015.

- **Age and income**

Age didn't seem to have a strong correlation with the amount of money spent, although customers between 55 and 65 years old seemed to spend the most and those who were younger than 40 seemed to spend less than others. As for income, the trend seemed to be quite strong that oder peole spent more than younger customers.

- **Offer types**

Customers who received bogo offers seemed to spend more than those who received discount offers, with those who received informational offers spending the least, although the difference was rather small among different offer types.

- **Channels**

Different channels didn't seem to affect the amount of money spent, with customers from all channels having a mean of about 15 dollars. 

