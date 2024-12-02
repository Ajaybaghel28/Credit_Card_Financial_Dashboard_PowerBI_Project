# Credit_Card_Transaction_and_Customer_Analysis_PowerBI_Project
The Credit Card Transaction and Customer Analysis project offers comprehensive insights into credit card usage patterns, revenue contributions, and customer demographics. Built using Power BI, the project visualizes key financial metrics and customer behaviors, enabling data-driven decisions for optimizing credit card services and marketing strategies.

## Problem Statement
The project aims to analyze credit card transaction data to answer critical business questions:
- Which expenditure types generate the most revenue?
- How do customer demographics (e.g., age, income, job type) influence credit card usage?
- Which card categories and transaction modes contribute the highest revenue?
- What are the transaction trends across quarters and different customer segments?

## Data Sources and Workflow
### Data Sources:
#### Transaction Data:
- Metrics: Transaction count, total transaction amount, and revenue.
- Transaction modes: Swipe, Chip, and Online.
#### Customer Demographics:
- Attributes: Age, gender, income, education, job type, and marital status.
Expenditure Data:
- Categories: Bills, Entertainment, Fuel, Groceries, Food, Travel.
  
### Workflow:
#### Data Preparation:
- Raw CSV files were imported into SQL.
- Data cleaning and transformation performed in SQL.
#### Power BI Integration:
- Cleaned SQL data imported into Power BI for visualization.
- Custom DAX formulas applied for advanced calculations and categorizations.
  
## Key DAX Formulas
- 1. Revenue Calculation:
Revenue = 'public cc_detail'[annual_fees] + 
          'public cc_detail'[total_trans_amt] + 
          'public cc_detail'[interest_earned]
  
- 2. Week Number Calculation:
Week_num2 = WEEKNUM('public cc_detail'[week_start_date])

- 3. Age Group Categorization:
Age_group = SWITCH(
    TRUE(),
    'public cust_detail'[customer_age] < 30, "20-30",
    'public cust_detail'[customer_age] >= 30 && 'public cust_detail'[customer_age] < 40, "30-40",
    'public cust_detail'[customer_age] >= 40 && 'public cust_detail'[customer_age] < 50, "40-50",
    'public cust_detail'[customer_age] >= 50 && 'public cust_detail'[customer_age] < 60, "50-60",
    'public cust_detail'[customer_age] >= 60, "60+",
    "Unknown"
)

- 4. Income Group Categorization:
Income_group = SWITCH(
    TRUE(),
    'public cust_detail'[income] < 35000, "Low_income",
    'public cust_detail'[income] >= 35000 && 'public cust_detail'[income] < 70000, "Mid_income",
    'public cust_detail'[income] >= 70000, "High_income",
    "Unknown"
)

## Dashboard Overview
### 1. Credit Card Transaction Report:
#### Key Metrics:
- Total Revenue: 56.52M
- Total Transaction Amount: 46M
- Total Interest Earned: 7.98M
- Total Transaction Count: 667K
  
#### Visuals:
- Revenue by Expenditure Type: Top categories include Bills, Entertainment, and Fuel.
- Revenue by Customer Job: Businessmen and White-collar employees contribute the most revenue.
- Quarter-wise Trends: Q4 shows the highest revenue and transaction count.
- Revenue by Card Category: Blue cards dominate in usage and revenue generation.
  
### 2. Credit Card Customer Report:
#### Key Metrics:
- Total Income: 588M
- Total Interest Earned: 7.98M
- Customer Satisfaction Score (CSS): 3.19

#### Visuals:
- Revenue by Age Group: Customers aged 40-50 contribute the highest revenue.
- Top-5 States by Revenue: TX, NY, and CA lead in credit card revenue.
- Revenue by Marital Status: Married customers contribute 27M, while singles contribute 22M.
- Weekly Revenue Trends: Visualizes revenue fluctuations by gender over time.
  
## Insights and Solutions
### Expenditure Analysis:
- Insight: Bills and Entertainment generate the highest revenue.
- Solution: Target high-value categories with special offers to boost usage.

### Customer Segmentation:
- Insight: High-income, educated, and middle-aged (40-50) customers are the most engaged.
- Solution: Develop tailored campaigns for these segments to enhance loyalty.

### Card Performance:
- Insight: Blue cards see the highest transaction volume and revenue.
- Solution: Introduce rewards programs for Blue card users to retain their loyalty.
  
### Regional and Weekly Trends:
- Insight: Revenue peaks in Q4, and states like TX, NY, and CA perform better.
- Solution: Allocate marketing budgets strategically across high-performing regions and quarters.
  
## Future Improvements
- Predictive Analytics: Implement forecasting models for revenue and transaction trends.
- Customer Retention Analysis: Identify churn risks and propose retention strategies.
- Advanced Segmentation: Introduce clustering for more granular customer insights.
