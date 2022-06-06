# Auto_Insurance_Fraud_Project
---

## Overview 
According to Verisk Analytics, auto insurance fraud is a $29 billion problem, according to the FBI this number may be closer to $40 Billion, there are even some sources who say that insurance fraud costs the U.S. roughly $80 Billion .

This is partially a result of omitted or misrepresented underwriting information and criminally inflated claims, leading to inadequate insurance and higher rates. But there is no such thing as a free lunch. 

Whilst insurance companies are on the hook for 30-80 billion dollars annually, these costs are being transferred down to consumers. And before you think that these numbers are getting smaller as data analytics gets better. This number is continuing to rise. See this infographic from the "Coalition Against Insurance Fraud":

![Insurance Fraud Infographic](/Images/insurance_fraud.jpg)

According to FBI statistics the average American family spends an extra $400 to $700 on insurance premiums every year because of insurance fraud. These costs are not absorbed by insurance companies  but are instead passed down to the consumers. 

We ([John Bruemmer](https://www.linkedin.com/in/john-bruemmer-407a58a4/) and [Bryan Keating](%28https://www.linkedin.com/in/Bryan-keating)) believe that using predictive modeling could help a major insurance company and therefore their consumers. 

For the purposes of this project, Bryan is the technical lead while John was the GitHub and Presentation lead.

---


## Business Understanding  

The stakeholder for this project is a major insurance company (think All-State, StateFarm, Geico, etc.). This project will showcase some of the techniques an insurance company can use to help identify fraudulent claims. By using data analytics and machine learning, companies may be able to flag suspicious claims and no longer pass these costs to their customers. 

Chicago was used as the test case for our modeling. Chicago is a huge market in the United Sates and we were given comprehensive police reporting data there. This data is likely applicable to a larger market but would need to be tested before implementation. Chicago Police Crash data was used in this case to see if any finding could be reached in a limited time span. Three large data frames were used from the Chicago Police that had information on the following: 

1)The crash itself 

2)The people involved 

3)The vehicles involved 

---


## Data Understanding and Preparation
All the data used was gathered from the city of Chicago's ["Chicago Data Portal"](https://data.cityofchicago.org/Transportation/Traffic-Crashes-Crashes/85ca-t3if). Data from January 2017 to December of 2021 was used for the purpose of our analyses. From that we gathered three dataframes: 

1 "Traffic Crashes - Crashes"   
2) "Traffic Crashes - People"   
3) "Traffic Crashes - Cars"

#### Raw Data:

**Traffic Crashes** - Crashes: 617,346 rows × 49 features

**Traffic Crashes** - People: 777,348 rows × 11 features

**Traffic Crashes** - Cars:  1,266,486 rows × 72 features

Refined and merged data, before 'OneHotEncoding':  616067 rows × 41 columns

Our target variable comes from the "Traffic Crashes - Crashes dataset". It was originally called "DAMAGE", and contained information on the cost of damages to the car, which could be one of three categories: "Under 500 dollars"(12 percent), "500-1500 dollars"(28 percent), and "Over 1500 dollars(59.77 percent)". 

In order to make our target binary and more balanced we combined the first two categories, making our new target: "Under 1500 dollars"(40 percent), "Over 1500 dollars"(59.77percent). 

![Distribution of Accident Damage](/Images/Accident_Damage_Distribution.png)

---

## Data Preparation



Reasonable assumptions were made to replace certain null values such as in the waterfront column. Because 'unknown' was already a column in most columns, it was used whenever appropriate. This caused problems for our 'onehotencoder' but was sufficient for this analysis. 

In addition there were some duplicates that were dropped from the data. After removing duplicates and dropping null values, the different data frames were combined on the "Crash ID' column. After removing categories that would have no impact on the our Damage sustained to the vehicle. 

This left us with a final data set of 481,373 rows and 28 columns. 

In order to use the vast number of categorical features in our dataset, 'OneHotEncoding' was used to convert those features into numeric columns. This resulted in a much larger data frame including over 200 columns. 

---

## Modeling


Different models and modelling techniques were used for our analysis. 

Logistic regression was the primary model used for this project. It was decided to be the best model due to it being faster than other models and it would provide us with better predictive estimates for predictors. Because this is only the beginning of a long processes to fight insurance fraud, we wanted to see what features of police reporting data would be most useful moving forward. 

Another way we found the most predictive variables was using a Decision Tree Classifier. This is useful at the beginning of a project in order to key in on important variables. Although useful for feature selection, it had less predictive power than our logistic regression model. 

Parameters were also changed within our logistic regression model in order to find the best settings to run our model at. The parameters we changed were the regularization strength, penalty, the maximum number of iterations, and the specific regularization penalty. Additionally, we applied a standard scaler to our data, so all of our parameters were on the same scale. 

---

## Evaluation/Validation

As mentioned above, a model with no predictive power would have an accuracy of 59.77%. 

Accuracy was chosen as the best evaluation metric over F1 Score, Recall, or Precision. 

The reason we chose accuracy is because we deemed False Positive and False Negatives to be equally important given our business understanding. False Positives in this case would mean that a car crash was deemed to be high damage when it was a low damage accident. This would result in an insurance agent potentially paying out more. A False Negative would mean that a car crash was deemed to be low damage when it was a high damage accident. This may result in resources being spent to investigate the accident which would also cost our Stakeholder money. 

Through the iterations of our model we were able to improve the accuracy by 6%. Although this is a disappointing number, it speaks to the complexity of the problem we are looking to solve. Going into this project, the team wished to see a 10 % improvement, and believes with some feature selection and engineering that goal is within reach. 

---

## Recommendations

We cannot give concrete recommendations based off our model evaluations right now. However, we can say that it we are confident given enough time and resources we could build a model to help detect this form of fraud for car insurance companies. 

One of the things this group has learned, is that though this type of modeling may be expensive for companies, it can make a huge difference to stakeholders. Insurance companies with smaller premiums (due to decreased fraud charges) will be able to advertise a lower rate. This will benefit both a companies stakeholders and their consumers. 

Using a model similar to ours will allow companies to send out independent investigators to affirm/deny insurance claims with differing price discrepancies. It is unrealistic to expect Insurance companies to meticulously investigate every claim. However, if a more accurate model could be made it would benefit both the corporation and consumer. 

## Further Analysis

There are many ways to improve this model whilst continuing to only use the data we have gathered. Much of a repair cost is dependent on where the car is hit. Although there is some indication of this within the data, work can be done to improve the primary cause category to better identify where a car has been impacted. 

In addition, our model was unable to effectively use any information about the vehicle other than the year it was made. Using Kelly Blue Book Value data or a similar appraiser would allow our model to incorporate this data more effectively. 

Before the model can be implemented, it needs to be tested outside of Chicago to ensure there are no inherent biases within our data. 

## In Depth Analysis
If you would like to see more in depth analysis please see either the *[Jupyter Notebook](https://github.com/Jbruemmer/Auto_Insurance_Fraud_Project/blob/main/Fraudulent_%20Auto_Insurance_Claim_Detection_Model%20.ipynb)* or the *[Slide Deck](https://github.com/Jbruemmer/Auto_Insurance_Fraud_Project/blob/main/Presentation_%20Combatting_Insurance_Fraud.pdf)*.

### Contact Information:
#### John Bruemmer:
Github :[https://github.com/Jbruemmer](https://github.com/Jbruemmer)
Email: [Johnnybruemmer@gmail.com](mailto:Johnnybruemmer@gmail.com)]
LinkedIn : [John Bruemmer | LinkedIn](https://www.linkedin.com/in/john-bruemmer-407a58a4/)

#### Bryan Keating:
Github: [https://github.com/BryanKeating](https://github.com/BryanKeating)
Email: [BryanKeating7@gmail.com](mailto:BryanKeating7@gmail.com)]
LinkedIn: [Bryan Keating | LinkedIn](https://www.linkedin.com/in/Bryan-keating)

## Thank You
We would like to personally thank anyone who has gotten to this point. We have had amazing instructors who have empowered both of us to get here. These instructors are Lindsey Berlin, Mark Barbour, and Jelly 'Angelica' Spratley. 

This project has been a challenge, it was completed in the span of three days and we both wish we had more time to tackle this problem. It has been incredibly humbling. Both John and Bryan wish to continue this type of work. More specifically we wish to use data to improve the world we live in.

## Repository Structure
```
├── Images
├── .gitignore
├── Fraudulent_ Auto_Insurance_Claim_Detection_Model.ipynb
├── Fraudulent_ Auto_Insurance_Claim_Detection_Notebook.pdf
├── Presentation_ Combatting_Insurance_Fraud.pdf
└── README.md
