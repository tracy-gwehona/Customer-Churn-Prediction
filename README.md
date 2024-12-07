# Customer Churn Prediction for SyriaTel Telecom

![image](https://github.com/user-attachments/assets/7473cc3f-e6a7-45e5-ae96-c431e7412ff9)

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

## Exploratory Data Analysis
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
![image](https://github.com/user-attachments/assets/25b82bcb-8353-402c-a064-687c1bcbb8f5)
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

## Modeling
I used two models:
1. **Logistic regression model**. Since it is well-suited for binary classification problems like the one we are facing of predicting churn or no churn.
2. **Random forest classifier**.

### Feature Importance Analysis
![image](https://github.com/user-attachments/assets/e9e1101d-9d51-41a9-bb21-57f3f481dcfd)
- **Total day minutes** and **customer service calls** are the strongest indicators of churn. This suggests that high usage during the day and frequent customer service interactions signal potential dissatisfaction or issues.
- **International plan** also contributes significantly, indicating that customers with such plans might have higher churn rates, possibly due to cost or service issues.
- Features like voice mail plan and total international calls have minimal predictive power.

## Evaluation
These models' performance were then be evaluated by use of classification metrics such as roc-auc score, precision, recall and F1 score.
### 1. Classification Report
- **Logistic Regression**: Performs quite well in predicting non-churn customers, but it misses 28% of them (lower recall). While the recall is higher for churn customers (indicating that 73% of actual churn cases are detected), precision is quite low, meaning many of the predicted churn cases are false positives.
- **Random Forest**: Random forest detects all non-churn customers (perfect recall), showing strong performance on this class and has high precision for churn predictions, but it misses 35% of churn cases (lower recall), similar to logistic regression but with slightly better precision.
### 2. Overall Accuracy
- **Logistic Regression**: Accuracy is 0.72, which is lower than the random forest's performance. 
- **Random Forest**: Accuracy is 0.95, reflecting the model’s ability to predict non-churn cases with high recall. While it still misses churn customers, the model’s high precision for both classes boosts its overall performance.
### 3. ROC-AUC Score
- **Logistic Regression ROC-AUC = 0.8052**: The model is able to distinguish between churn and non-churn with reasonable accuracy. This is a good score, but there's room for improvement, especially in terms of improving recall for churn.
- **Random Forest ROC-AUC = 0.9287**: Random forest performs significantly better, with a higher AUC score, indicating that it is better at distinguishing between churn and non-churn cases.
### 4. ROC Curve
![image](https://github.com/user-attachments/assets/6d2e2249-7ab4-41ac-8fc4-272251eb21b5)
- The closer the ROC curve is to the top-left corner, the better the model's performance. The **Random Forest** curve is consistently above the Logistic Regression curve.
- **Random Forest** shows a better trade-off between True Positive Rate (Sensitivity/Recall) and False Positive Rate, making it the superior model for churn prediction.
- **Logistic Regression**, while performing decently, has a lower ability to correctly classify churn cases compared to Random Forest.

## Conclusion
- **Logistic Regression** performs adequately on non-churn cases but struggles with churn detection, as indicated by the low precision and recall for churn. Its performance is acceptable when computational resources are limited, or when simplicity is desired, but it is not ideal for imbalanced datasets.
- **Random Forest**, on the other hand, provides a more balanced performance across both classes, with better handling of class imbalance. It achieves high precision and recall for non-churn and performs significantly better than logistic regression for churn detection, though it still misses some churn cases. Its ROC-AUC score is much higher, indicating superior discrimination power.

## Recommendations
- For **better performance** on both classes, **Random Forest** is the better model, especially if your goal is to achieve a more robust performance for detecting churn while handling class imbalance. The higher ROC-AUC score and overall classification report indicate its suitability for this task.
- If **interpretability and computational efficiency** are key, Logistic Regression might be preferred, but additional techniques (like tuning the model further, or applying SMOTE) could help improve its performance. 

**NOTE**: However, for churn prediction in this case, Random Forest should be prioritized, especially when dealing with imbalanced data.
- As shown in feature importance analysis:
  1. Focus on Daytime Users: Monitor customers with high daytime usage and proactively offer support or incentives.
  2. Improve Customer Service: Address issues related to customer service interactions to reduce churn.
  3. International Plans: Evaluate and improve international plan offerings to reduce dissatisfaction.

