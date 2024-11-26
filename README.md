# Credit_Card_Financial_Dashboard_PowerBI_Project

The Credit Card Financial Dashboard is a data analysis project focused on understanding credit card transaction patterns and customer demographics. Created in Power BI, this dashboard provides insights into transaction volume, revenue distribution, customer profiles, and financial performance by expenditure types, card categories, and more. The workflow includes importing CSV files into SQL for preprocessing and leveraging DAX in Power BI for advanced calculations and categorizations.

## Problem Statement
The project aims to analyze and visualize credit card transaction data to answer key questions:
- Which expenditure types contribute the most to total revenue?
- How do customer demographics like age, income, and job type impact credit card usage?
- Which card categories yield the highest transaction volumes and revenue?
- How do transaction trends vary over time and across different regions?

## Data Sources and Workflow
### Data Sources
- Transaction Data: Includes transaction volume, total amounts, revenue generated, and card type.
- Customer Demographics: Age, gender, income, marital status, job type, and education level.
- Expenditure Data: Details spending categories like groceries, entertainment, fuel, etc.

### Workflow
1. Importing CSV to SQL:
- Raw CSV data was imported into a SQL database.
- Data cleaning, validation, and transformation were performed in SQL for efficient querying.

2. Importing SQL Data to Power BI:
- The cleaned data from SQL was imported into Power BI for analysis and visualization.
- SQL queries and views were used to streamline data preparation for the dashboard.

3. Implementing DAX in Power BI:
- Custom DAX formulas were applied to calculate key metrics and create dynamic categorizations.

## Key DAX Formulas
- 1. Revenue Calculation:
DAX
Revenue = 'public cc_detail'[annual_fees] + 
          'public cc_detail'[total_trans_amt] + 
          'public cc_detail'[interest_earned]

- 2. Week Number:
DAX
Week_num2 = WEEKNUM('public cc_detail'[week_start_date])
Age Group Categorization:

- 3. Age_group = SWITCH(
    TRUE(),
    'public cust_detail'[customer_age] < 30, "20-30",
    'public cust_detail'[customer_age] >= 30 && 'public cust_detail'[customer_age] < 40, "30-40",
    'public cust_detail'[customer_age] >= 40 && 'public cust_detail'[customer_age] < 50, "40-50",
    'public cust_detail'[customer_age] >= 50 && 'public cust_detail'[customer_age] < 60, "50-60",
    'public cust_detail'[customer_age] >= 60, "60+",
    "unknown"
)

- 4. Income Group Categorization:
Income_group = SWITCH(
    TRUE(),
    'public cust_detail'[income] < 35000, "Low_income",
    'public cust_detail'[income] >= 35000 && 'public cust_detail'[income] < 70000, "Mid_income",
    'public cust_detail'[income] >= 70000, "High_income",
    "unknown"
)

## Key Sections and Metrics in the Dashboard
1. Revenue and Transaction Count by Quarter
- Objective: Visualize total revenue and transaction count across each quarter (Q1 to Q4).
- Insights: Identifies seasonal performance trends, helping to optimize marketing strategies.

2. Revenue by Expenditure Type
- Objective: Show revenue contributions by expenditure categories such as bills, groceries, and entertainment.
- Insights: Helps identify high-value spending categories for targeted campaigns.

3. Revenue by Customer Demographics
- Education Level: Analyzes revenue by education levels (Graduate, High School, etc.).
- Job Type: Highlights revenue contributions by job types (Businessman, White-collar, etc.).
- Age Group: Breaks down revenue by age ranges (20-30, 30-40, etc.) for demographic insights.

4. Revenue by Card Category
- Objective: Shows revenue contributions by card types (Blue, Silver, Gold, Platinum).
- Insights: Identifies high-performing and premium card categories.

5. Revenue by Transaction Mode
- Objective: Displays revenue distribution by transaction modes (Swipe, Chip, Online).
- Insights: Provides insights into customer preferences for transaction methods.

## Insights and Solutions
1. Expenditure Type and Revenue Contribution
- Insight: Categories like Bills and Entertainment contribute the most revenue.
- Solution: Focus campaigns on high-revenue categories to drive growth.

2. Customer Demographic Segmentation
- Insight: High-income, educated professionals are the most engaged demographic.
- Solution: Design tailored offers for high-income customers to enhance loyalty.

3. Card Category Performance
- Insight: Blue cards have the highest usage, while Platinum cards yield the highest revenue per transaction.
- Solution: Promote premium cards to high-spending customers for increased profitability.

4. Transaction Mode Preferences
- Insight: Most transactions are Swipes, while Online transactions are underutilized.
- Solution: Promote incentives for online transactions to boost digital engagement.

## Future Improvements
- Additional Metrics: Add insights on customer lifetime value and churn rates.
- Advanced Segmentation: Introduce clustering for granular customer segmentation.
- Predictive Analytics: Implement forecasting for future revenue trends.
