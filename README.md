# Introduction

This data set contains simulated data that mimics customer behavior on the Starbucks rewards mobile app. Once every few days, Starbucks sends out an offer to users of the mobile app. An offer can be merely an advertisement for a drink or an actual offer such as a discount or BOGO (buy one get one free). Some users might not receive any offer during certain weeks.

Not all users receive the same offer, and that is the challenge to solve with this data set.

The goal of this project is to combine transaction, demographic and offer data to determine which demographic groups respond best to which offer type. This data set is a simplified version of the real Starbucks app because the underlying simulator only has one product whereas Starbucks actually sells dozens of products.

Every offer has a validity period before the offer expires. As an example, a BOGO offer might be valid for only 5 days. You'll see in the data set that informational offers have a validity period even though these ads are merely providing information about a product; for example, if an informational offer has 7 days of validity, you can assume the customer is feeling the influence of the offer for 7 days after receiving the advertisement.

The transactional data shows user purchases made on the app including the timestamp of purchase and the amount of money spent on a purchase. This transactional data also has a record for each offer that a user receives as well as a record for when a user actually views the offer. There are also records for when a user completes an offer.

Note that someone using the app might make a purchase through the app without having received an offer or seen an offer.

# Installation

Python 3: 

Jupyter Notebook, json, pandas, Numpy, datetime, matplotlib.pyplot, seaborn, sklearn

# File Description

The Jupyter Notebook contains scripts for data wrangling, data exploration, and modeling.

The Visuals folder contains visuals for the project.

# Project Motivation

This is my capestone project for the Data Scientist Nanodegree from Udacity. Therefore, I was very excited to work on it, applying the techniques I have learnt in this course. I am also very excited to share the results with fellow data scientists / data analysts. 
