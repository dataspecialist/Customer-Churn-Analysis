# Customer-Churn-Analysis

## 📌Project Objective:-
To analyze customer attrition data, identify high-risk segments, and provide actionable retention strategies for the business. The goal is to reduce the churn rate by understanding the correlation between service features, contract types, and customer technical issues.

## 📂 Dataset description :
* **Source:** <a href="https://www.google.com">Click here</a>
* **Volume:** 8000 Records.
* **Key Attributes:**
* 
## 🧹 Data Preparation & Semantic Layer:
Completed the Data transformation in Power Query and the dataset loaded into Microsoft Power BI Desktop for modeling.
Customer Churn dataset is give table named:
-Customer churn dataset which has 23 columns and 7043 rows of observation
Data Cleaning for the dataset was done in the power query editor as follows:

-Replaced the value is SeniorCitizen N coverted No and Y converted Yes
In the new table, one additional conditional columns were added using M-formula:

-loyalty = SWITCH(TRUE(),'01 Churn-Dataset'[tenure]<=12,"< 1 year",'01 Churn-Dataset'[tenure]<=24,"< 2 years",'01 Churn-Dataset'[tenure]<=36,"< 3 years",'01 Churn-Dataset'[tenure]<=48,"< 4 years", '01 Churn-Dataset'[tenure]<=60,"< 5 years",'01 Churn-Dataset'[tenure]<=72,"< 6 years")

-Removed Unnecessary columns

-Removed Unnecessary rows

-Each of the columns in the table were validated to have the correct data type.
