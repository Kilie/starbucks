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

#### Distribution of demographic features

![Distribution](https://github.com/Kilie/starbucks/blob/master/Visuals/Distribution.png)

Most of the customers were between 35 to 75 years old, the main income range of the customers was within 40k-75k dollars, and the majority of the customers in this experiment became members after 2015.

Note that there were the most customers who became members in 2017 followed by 2016, possibly due to the expansion of the business into new markets or some other factors such as new marketing strategies which caused an increase in the number of members in these two years.

#### Who were more likely to respond?

![Response rate 1](https://github.com/Kilie/starbucks/blob/master/Visuals/response%20rate%201.png)

![Response rate 2](https://github.com/Kilie/starbucks/blob/master/Visuals/response%20rate%202.png)

Customers' gender, joining year (became_member_on), income, and age all seemed to affect the response rate, although it's notable that the difference in the mean age between the response and non-response groups was only three year old.

Overall, customers who were female, became members during 2015-2017, and had higher income were more likely to respond to the offers than others.

#### Which offer types had the most response?

![Offer type 1](https://github.com/Kilie/starbucks/blob/master/Visuals/offer%20type%201.png)

Overall, discount offers seemed to have higher response rates compared to bogo offers. Informational offers didn't seem to relate to any responses, so I won't discuss this type further with differnt demographic features.  

- **Gender**

Female and 'O' customers had higher response rates than male customers to both bogo and discount offers, and this trend is stronger for bogo offers. 

The reason for this was that female as well as 'O' customers seemed to respond similarly to different offer types, whereas male customers seemed to respond more to discount offers than bogo offers.

- **Joining year**

Bogo offers appeared to have higher response rates from customers who became members during 2015-2017 than those who became member in other years. 

Discount offers, on the other hand, had relatively similar response rates from customers who became members during 2013-2017, with customers from 2018 having the a much lower response rate compared to those from other years.

![Offer type 2](https://github.com/Kilie/starbucks/blob/master/Visuals/offer%20type%202.png)

- **Age and income**

For both bogo and discount offers, responsive customers seemed to have older ages and higher income than their unresponsive counterparts, and the income difference was bigger between responsive and unresponsive groups than the age differnce. 

In addition, the difference between response groups was bigger for bogo offers than for discount offers.

#### Which channels had the most response?

![Channel 1](https://github.com/Kilie/starbucks/blob/master/Visuals/channel%201.png)

In general, social media and web appeared to have higher response rates (73% and 70%, respectively) than mobile and email channels (66% and 65%, respectively). 

- **Gender** 

Female and 'O' customers seemed to have higher response rates than male customers for all channels, and all three genders responded more to social media offers and web than to mobile and email. 

However, unlike the general trend in which social median had the highest response rate, 'O' customers seemed to have the highest response rate to web offers, indicating a close connection between customers from this gender group and web.

- **Joining year**

For all channels, customers who became members during 2015-2017 appeared to have higher response rates than those who became members in other years. Channels didn't seem to affect this trend among joining years.

![Channel 2](https://github.com/Kilie/starbucks/blob/master/Visuals/channel%202.png)

- **Age and income**

Similar to offer types, all channels seemed to have older ages and higher income in the responsive group compared to the unresponsive group, and income difference was bigger between responsive and unresponsive groups than the age differnce.  


#### Who were more likely to spend more?

![Amount 1](https://github.com/Kilie/starbucks/blob/master/Visuals/amount%201.png)

Overall, customers who responded to the offers seemed to spend more money on average (about 17 dollars) than those who didn't respond (about 11 dollars), suggesting that it is indeed important to take measures to improve the response rate.

![Amount 2](https://github.com/Kilie/starbucks/blob/master/Visuals/amount%202.png)

- **Gender**

Female customers seemed to spend the most, followed by 'O' and male customers. 

- **Joining year**

Customers who became members during 2015-2018 seemed to spend more than thos who bemame members earlier than 2015.

- **Offer types**

Customers who received bogo offers seemed to spend more than those who received discount offers, with those who received informational offers spending the least, although the difference was rather small among different offer types.

- **Channels**

Different channels didn't seem to affect the amount of money spent, with customers from all channels having a mean of about 15 dollars. 

![Amount 3](https://github.com/Kilie/starbucks/blob/master/Visuals/amount%203.png)

- **Age and income**

Age didn't seem to have a strong correlation with the amount of money spent, although customers between 55 and 65 years old seemed to spend the most and those who were younger than 40 seemed to spend less than others. As for income, the trend seemed to be quite strong that oder peole spent more than younger customers.

## Modeling and Evaluation

![pipeline 1](https://miro.medium.com/max/721/1*ZvwqTOGLMhFSj7R93Yndgw.png)

![Grid search 1](https://miro.medium.com/max/595/1*yJ94PuvbX3ud0r565KTsnw.png)

Using grid search slightly increased the weighted average precision of the model from 0.58 to 0.59, which is not really a whole lot better.

There are a few possible ways to improve the performance of the model, including trying other algorithms and add more features. I will try the LogisticRegression algorithm and see if it can improve the performance or not.

![pipeline 2](https://miro.medium.com/max/781/1*I4cRJAMIwlaw6Xs7UsyJ1g.png)

![Grid search 2](https://miro.medium.com/max/620/1*acdLTO9VUqL5M1-CbDtdmw.png)

By using LogisticRegression, the performance of the model increased and the weighted average precision increased from 0.59 to 0.84. I will use GridSearchCV to try to further improve the performance of the model.

By using LogisticRegression combined with GridSearchCV, the precision of the model increased from 0.58 to 0.86, which is quite an improvement. This shows how important it is to select proper algorithms in modeling.

## Conclusions

In order to increase revenues, it makes sense for the company to promote the response rate, because people who responded to the offers indeed seemed to spend more than those who didn’t respond.

Particularly, the response rate could be improved through two aspects, including (1) identify customers with certain demographic features and (2) customize offers for different demographic groups by adjusting offer types and channels to deliver the offers.

### Demographic features
The company might want to primarily focus on female customers and people with higher income. They are more responsive to offers and they also spend more than others.

Age didn’t seem to be a good indicator for either the response rate or amount of money spent according to the data, although the company might want to consider that people around 55–65 spend more on average when constructing strategies.

Finally, people who became members during 2015–2017 responded more and spent more than those who became member in other years, suggesting that the company might want to investigate into what made these three years different from other years: were there new markets developed or were there any strategies applied during these years? Understanding the reason behind this would be helpful for the company to improve its offer response rates and possibly develop more members.

### Offer strategies

In general, sending discount offers through social media seem to be the most promising way for the company to get a higher response rate. This is especially important for male customers, because they tend to respond more to the discounts while other genders don’t have such a big different response rate to BOGOs and discounts.

It’s worth mentioning that although discounts and social media had higher response rates in my analysis, people who received BOGOs actually spent slightly more than those who received discount and informational offers, and the amount of money spent by people from different channels was similar. This suggests that when trying to achieve a higher response rate, it is also important to factor in the cost of making these offers.

## Acknowledgements 

Special thanks goes to my mentor Nicolas Essipova for this Udacity course and the reviewer(s) who helped me through the course. The instructors have greatly helped me build up understandings about important data science concepts and tools. I have learnt a whole lot through this journey. 

Without these great people's help I wouldn't have accomplished the project. I will keep going along this path with the knowledge I have gained from here.

## Contribution

Any contribution to this project is very welcome. 
