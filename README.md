# Credit_Card_Financial_Dashboard_PowerBI_Project
Credit Card Financial Dashboard
Overview
This Power BI dashboard provides a comprehensive analysis of credit card transaction data, enabling insights into revenue distribution, customer demographics, and spending patterns.

Problem Statement
The primary goal is to answer key questions about credit card usage:

Which expenditure types contribute the most to total revenue?
How do customer demographics impact credit card usage?
Which card categories yield the highest transaction volumes and revenue?
How do transaction trends vary over time and across different regions?
Data Sources and Workflow

Data Sources:
Transaction Data: Includes transaction volume, total amounts, revenue generated, and card type.
Customer Demographics: Age, gender, income, marital status, job type, and education level.
Expenditure Data: Details spending categories like groceries, entertainment, fuel, etc.
Workflow:
Data Import and Cleaning:
CSV data is imported into a SQL database.
Data is cleaned, validated, and transformed in SQL.
Power BI Integration:
Cleaned data is imported into Power BI.
SQL queries and views are used to streamline data preparation.
DAX Implementation:
Custom DAX formulas are applied for advanced calculations and categorizations.
Key DAX Formulas

Revenue Calculation:
Code snippet
Revenue = 'public cc_detail'[annual_fees] + 
          'public cc_detail'[total_trans_amt] + 
          'public cc_detail'[interest_earned]
Use code with caution.

Week Number:
Code snippet
Week_num2 = WEEKNUM('public cc_detail'[week_start_date])
Use code with caution.

Age Group Categorization:
Code snippet
Age_group = SWITCH(
    TRUE(),
    'public cust_detail'[customer_age] < 30, "20-30",
    'public cust_detail'[customer_age] >= 30 && 'public cust_detail'[customer_age] < 40, "30-40",
    'public cust_detail'[customer_age] >= 40 && 'public cust_detail'[customer_age] < 50, "40-50",
    'public cust_detail'[customer_age] >= 50 && 'public cust_detail'[customer_age] < 60, "50-60",
    'public cust_detail'[customer_age] >= 60, "60+",
    "unknown"
)
Use code with caution.

Income Group Categorization:
Code snippet
Income_group = SWITCH(
    TRUE(),
    'public cust_detail'[income] < 35000, "Low_income",
    'public cust_detail'[income] >= 35000 && 'public cust_detail'[income] < 70000, "Mid_income",
    'public cust_detail'[income] >= 70000, "High_income",
    "unknown"
)
Use code with caution.

Key Dashboard Sections and Metrics

Revenue and Transaction Count by Quarter
Revenue by Expenditure Type
Revenue by Customer Demographics
Education Level
Job Type
Age Group
Revenue by Card Category
Revenue by Transaction Mode
Insights and Solutions

Expenditure Type and Revenue Contribution:
Insight: Categories like Bills and Entertainment contribute the most revenue.
Solution: Focus campaigns on high-revenue categories.
Customer Demographic Segmentation:
Insight: High-income, educated professionals are the most engaged demographic.
Solution: Design tailored offers for high-income customers.
Card Category Performance:
Insight: Blue cards have the highest usage, while Platinum cards yield the highest revenue per transaction.
Solution: Promote premium cards to high-spending customers.
Transaction Mode Preferences:
Insight: Most transactions are Swipes, while Online transactions are underutilized.
Solution: Promote incentives for online transactions.
Future Improvements

Add metrics on customer lifetime value and churn rates.
Introduce clustering for granular customer segmentation.
Implement forecasting for future revenue trends.
