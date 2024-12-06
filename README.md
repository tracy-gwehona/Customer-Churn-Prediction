# Customer Churn Prediction for SyriaTel Telecom

![image](https://github.com/user-attachments/assets/6933b62f-4087-44bf-b578-18d235a52d78)

Author: [Tracy Gwehona](tracy.gwehona@gmail.com)

## Overview
Customer churn (or the loss of customers) is one of the biggest challenges for telecommunications companies such as SyriaTel because acquiring new customers can be much more expensive than keeping them. High churn rates affect profitability, market share, and long-term expansion. I aim to use  historical customer information to anticipate who is destined to exit. If the company knows the churn pattern, it will be able to apply proactive measures to increase retention and customer satisfaction and keep up with the competition.

## Business Understanding
### Stakeholders
SyriaTel Telecommunications Company.

### Business problem
SyriaTel is having customer churn and that is directly impacting revenue and profit. For that, the company must know what causes the customer to be dissatisfied with it. SyriaTel can’t develop retention plans without understanding churn and high-risk customers, , leading to continued customer loss and a decline in market share.

To address this, I aim to:
1. Identify key factors influencing customer churn.
2. Predict customer churn.
3. Provide actionable insights to enable SyriaTel to implement targeted interventions.

## Data Understanding
The dataset in use was obtained from [kaggle](https://www.kaggle.com/datasets/becksddf/churn-in-telecoms-dataset?resource=download). It contains SyriaTel telecom customers' information such as:
1. Account length.
2. International plan.
3. Voicemail plan.
4. Number of voicemail messages.
5. Total day, evening and night calls, charges and minutes.
6. Customer service calls.
7. Churn. Whether a customer left or not.

This dataset  is a historical record of SyriaTel customer base with features that describe customer behaviour, service usage and interactions with the company.
It includes both behavioural and service attributes directly associated with satisfaction and retention which allows you to find trends that cause churn.

## Data Analysis
### a) Distribution of international and voicemail plans by churn
![image](https://github.com/user-attachments/assets/2f4493a3-9886-41ce-9335-a39c85f70920)
**Insights:**
1. **International plan by churn**
- Majority of customers do not have an international plan, and among these, churn is relatively low. 
- A higher proportion of customers with an international plan have churned. This suggests that having an international plan may be associated with an increased likelihood of churn.
2. **Voice mail plan by churn**
- The majority of customers do not have a voice mail plan, and most of them did not churn. However, the number of customers who churned is significant among those without the plan.
- Fewer customers have a voice mail plan, and among them, the churn rate is relatively low compared to those without the plan. This indicates that customers with a voice mail plan are less likely to churn.
### b) Relationship between churn and columns with numerical data
![image](https://github.com/user-attachments/assets/63d91499-8ac1-4e78-be77-0b21fa491116)
**Insights:**
1. **Account length vs churn**
- Both churned and non-churned customers show similar distributions for account length, with no major differences. Account length might not be a significant factor in predicting churn.
2. **Number of Voicemail Messages vs churn**
- The majority of customers have a low number of voicemail messages. There are many outliers at the upper end, suggesting some customers have significantly higher voicemail messages than the rest.
3. **Total Minutes vs churn**
- Non-churn customers' total minutes appear to be centered around a slightly lower range and churned customers have a wider range of total minutes, with a higher median.
- Customers with higher total usage might be more likely to churn, potentially due to high costs.
4. **Total Calls vs churn**
- Both churned and non-churned customers show similar distributions for total calls, with no major differences.
- Total calls might not be a significant factor in predicting churn.
5. **Total Charge vs churn**
- Non-churn customers' charges are lower and have a narrower spread and churned customers' charges are higher and exhibit a wider spread.
- Higher total charges are associated with churn, suggesting dissatisfaction with billing or costs.
6. **Customer Service Calls vs churn**
- Non-churn customers have fewer customer service calls, with most data concentrated at the lower range and churned customers have more customer service calls, with some extreme outliers.
- High interaction with customer service is associated with churn, possibly indicating unresolved issues or dissatisfaction.
### c) Correlation Analysis
![image](https://github.com/user-attachments/assets/ac07a5b9-2b76-482c-a249-078324c623c4)

**Insights:**
- Strongly correlated variables (e.g., total day minutes and total day charge) might provide redundant information.
- Variables showing significant differences in correlations (positive or negative) with the target (churn) might be more predictive.
- Features with minimal correlation (close to 0) might have limited relevance to predictive modeling unless their relationship with the target (churn) is non-linear.



