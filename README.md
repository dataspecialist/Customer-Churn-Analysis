# Customer-Churn-Analysis

## 📌Project Objective:-
To analyze customer attrition data, identify high-risk segments, and provide actionable retention strategies for the business. The goal is to reduce the churn rate by understanding the correlation between service features, contract types, and customer technical issues.

## 📂 Dataset description :
* **Source:** <a href="https://github.com/dataspecialist/Customer-Churn-Analysis/blob/219894bf430725df3dcb41136f5f3cc8ea1b324d/Sample%20dataset.xlsx">Click here</a>
* **Volume:** 7000+ Records.
  
## 🧹 Data Preparation & Semantic Layer:
Completed the Data transformation in Power Query and the dataset loaded into Microsoft Power BI Desktop for modeling.

Customer Churn dataset is give table named:

- `Customer churn dataset` which has `23 columns and 7043 rows` of observation

Data Cleaning for the dataset was done in the power query editor as follows:

- Replaced  the value is `SeniorCitizen` N coverted No and Y converted Yes

In the new table, one additional conditional columns were added using M-formula:

- loyalty = `SWITCH(TRUE(),'01 Churn-Dataset'[tenure]<=12,"< 1 year",'01 Churn-Dataset'[tenure]<=24,"< 2 years",'01 Churn-Dataset'[tenure]<=36,"< 3 years",'01 Churn-Dataset'[tenure]<=48,"< 4 years", '01 Churn-Dataset'[tenure]<=60,"< 5 years",'01 Churn-Dataset'[tenure]<=72,"< 6 years")`

- Removed Unnecessary columns 
- Removed Unnecessary rows
- Each of the columns in the table were validated to have the correct data type

## Data Modeling:

And then dataset was cleaned and transformed, it was ready to the data modeled.

- The `customer churn` tables as show below:

![Screenshot (39)](https://user-images.githubusercontent.com/118357991/227792100-51216842-8e72-4e48-b740-aab5d2f97541.png)

## Data Analysis (DAX):

Measures used in  all visualization are:

- **Average MonthlyCharges** = `AVERAGE('01 Churn-Dataset'[MonthlyCharges])`

- **Average TotalCharges** = `AVERAGE('01 Churn-Dataset'[TotalCharges])`

- **churn count** = `CALCULATE(COUNT('01 Churn-Dataset'[Churn]), ALLSELECTED('01 Churn-Dataset'[Churn]),'01 Churn-Dataset'[Churn] = "Yes")`

- **churn rate %** = `DIVIDE(CALCULATE(COUNT('01 Churn-Dataset'[Churn]), '01 Churn-Dataset'[Churn] = "yes" ), COUNT('01 Churn-Dataset'[Churn]), 0)`

- **Dependent in %** = `DIVIDE(CALCULATE(COUNT('01 Churn-Dataset'[Dependents]), '01 Churn-Dataset'[Dependents]="Yes",'01 Churn-Dataset'[Churn]="Yes"), CALCULATE(COUNT('01 Churn-Dataset'[Dependents]),'01 Churn-Dataset'[Churn]="Yes"), 0)`

- **Device protection in %** = `DIVIDE(CALCULATE(COUNT('01 Churn-Dataset'[DeviceProtection]), '01 Churn-Dataset'[DeviceProtection] ="Yes", '01 Churn-Dataset'[Churn]="Yes"),CALCULATE(COUNT('01 Churn-Dataset'[DeviceProtection]),'01 Churn-Dataset'[Churn]="Yes"),0)`

- **Online backup in %** = `DIVIDE(CALCULATE(COUNT('01 Churn-Dataset'[OnlineBackup]), '01 Churn-Dataset'[OnlineBackup] ="Yes", '01 Churn-Dataset'[Churn]="Yes"),CALCULATE(COUNT('01 Churn-Dataset'[OnlineBackup]),'01 Churn-Dataset'[Churn]="Yes"),0)`

- **Online security in %** =`DIVIDE(CALCULATE(COUNT('01 Churn-Dataset'[OnlineSecurity]), '01 Churn-Dataset'[OnlineSecurity] ="Yes", '01 Churn-Dataset'[Churn]="Yes"),CALCULATE(COUNT('01 Churn-Dataset'[OnlineSecurity]),'01 Churn-Dataset'[Churn]="Yes"),0)`

- **Partner in %** = `DIVIDE(CALCULATE(COUNT('01 Churn-Dataset'[Partner]),'01 Churn-Dataset'[Partner]="Yes",'01 Churn-Dataset'[Churn]="Yes"), CALCULATE(COUNT('01 Churn-Dataset'[Partner]), '01 Churn-Dataset'[Churn]="Yes"), 0)`

- **Phone service in %** =`DIVIDE(CALCULATE(COUNT('01 Churn-Dataset'[PhoneService]), '01 Churn-Dataset'[PhoneService] ="Yes", '01 Churn-Dataset'[Churn]="Yes"),CALCULATE(COUNT('01 Churn-Dataset'[PhoneService]),'01 Churn-Dataset'[Churn]="Yes"),0)`

- **SenioCitizen in %** = `DIVIDE(CALCULATE(COUNT('01 Churn-Dataset'[SeniorCitizen]),'01 Churn-Dataset'[SeniorCitizen]=1,'01 Churn-Dataset'[Churn]="Yes"), CALCULATE(COUNT('01 Churn-Dataset'[SeniorCitizen]),'01 Churn-Dataset'[Churn]="Yes"), 0)`

- **Streaming Movies in %** =`DIVIDE(CALCULATE(COUNT('01 Churn-Dataset'[StreamingMovies]), '01 Churn-Dataset'[StreamingMovies] ="Yes", '01 Churn-Dataset'[Churn]="Yes"),CALCULATE(COUNT('01 Churn-Dataset'[StreamingMovies]),'01 Churn-Dataset'[Churn]="Yes"),0)`

- **Streaming TV in %** =`DIVIDE(CALCULATE(COUNT('01 Churn-Dataset'[StreamingTV]), '01 Churn-Dataset'[StreamingTV] ="Yes", '01 Churn-Dataset'[Churn]="Yes"),CALCULATE(COUNT('01 Churn-Dataset'[StreamingTV]),'01 Churn-Dataset'[Churn]="Yes"),0)`

- **Tech Support in %** =`DIVIDE(CALCULATE(COUNT('01 Churn-Dataset'[TechSupport]), '01 Churn-Dataset'[TechSupport] ="Yes", '01 Churn-Dataset'[Churn]="Yes"),CALCULATE(COUNT('01 Churn-Dataset'[TechSupport]),'01 Churn-Dataset'[Churn]="Yes"),0)`

## 📊KPIs & Key Insights
Based on the deep-dive analysis of the dataset:

- The "Month-to-Month" Trap: The overall churn rate is 26.5%, but for customers on "Month-to-Month" contracts, it spikes to 42.7%. In contrast, "Two-Year" contract churn is negligible (<3%).

- Fiber Optic Dissatisfaction: Customers with Fiber Optic internet have a significantly higher churn rate (41.9%) compared to DSL users (19%), suggesting potential pricing or technical stability issues with the Fiber product.

- The Tech Support Signal: There is a strong correlation between technical tickets and churn. Customers who churned averaged 1.16 tech tickets, whereas loyal customers averaged only 0.15. Multiple tech complaints are a direct precursor to leaving.

- Tenure Risk Zone: The highest attrition occurs within the first 12 months (Loyalty group "< 1 Year"). If a customer survives the first year, their likelihood of churning drops by over 50%.

## 💡Decisions & Actions (The "So What?"):
Based on the data, the following strategic actions are recommended:

| **Observation** | **Recommended Action** | **Owner** | **Expected Impact** |
| :--- | :--- | :--- | :--- |
High Churn in Month-to-Month Contracts (42%)|Launch a "Loyalty Upgrade" campaign offering a 10% discount for switching to a 1-year contract.|	Marketing Team	|Reduce short-term churn by ~15% by locking in tenure.
Fiber Optic Churn is 2x DSL Churn	|Audit Fiber Optic reliability and price-to-value ratio. |Competitor benchmarking required.|	Product Manager	|Identify if the issue is Price or Quality.
High Tech Tickets Precede Churn|	Implement an automated "Customer Success" alert: If a user logs >2 tickets in a month, a senior agent must call them.|	Customer Support Head|	Intervene before the customer decides to cancel.
Electronic Check Payers Churn Higher	|Incentivize "Auto-Pay" (Credit Card/Bank Transfer) setup to reduce friction in manual payments.	|Billing Dept	|Increase retention by removing the monthly "payment decision" point.

## 🎖️Bonus:-
This project framework is scalable and can be directly applied to the following industries:

- **Telecommunications (Primary):**

Use Case: Predicting subscriber cancellations for mobile, internet, and cable services.

Key Metric: Average Revenue Per User (ARPU) vs. Customer Lifetime Value (CLV).

- **SaaS (Software as a Service):**

Use Case: Companies like Netflix, Spotify, or Salesforce use this exact logic to track monthly recurring revenue (MRR) churn.

Transferable Skill: The "Contract Type" analysis in this project mirrors SaaS "Annual vs. Monthly" subscription models.

- **BFSI (Banking, Financial Services, & Insurance):**

Use Case: Predicting credit card attrition or insurance policy lapses.

Transferable Skill: The "Tech Support" variable in this dataset is analogous to "Customer Service Complaints" in banking.

- **E-Commerce (Subscription Models):**

Use Case: Retention for subscription boxes (e.g., HelloFresh) or loyalty memberships (e.g., Amazon Prime).

Key Insight: Analyzing "Tenure Bins" helps identify the "drop-off cliff" where most subscribers cancel.

