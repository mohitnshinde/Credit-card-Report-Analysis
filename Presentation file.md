# Credit-card-Report-Analysis

Here we have tried creating the Credit card report and lateer also had done the analysis on the same

# Steps to be followed for the Analysis
1. Data from SQL
2. Data processing & DAX
3. Dashboard & insights
4. Export & share project

#1. Import data to SQL database
A. Prepare csv file 
B. Create tables in SQL
C. import csv file into SQL

#2 DAX Queries
A, AgeGroup = SWITCH(
 TRUE(),
 'public cust_detail'[customer_age] < 30, "20-30",
 'public cust_detail'[customer_age] >= 30 && 'public cust_detail'[customer_age] < 40, "30-40",
 'public cust_detail'[customer_age] >= 40 && 'public cust_detail'[customer_age] < 50, "40-50",
 'public cust_detail'[customer_age] >= 50 && 'public cust_detail'[customer_age] < 60, "50-60",
 'public cust_detail'[customer_age] >= 60, "60+",
 "unknown"
 )
 
B, IncomeGroup = SWITCH(
 TRUE(),
 'public cust_detail'[income] < 35000, "Low",
 'public cust_detail'[income] >= 35000 && 'public cust_detail'[income] <70000, "Med",
 'public cust_detail'[income] >= 70000, "High",
 "unknown"
)

C, week_num2 = WEEKNUM('public cc_detail'[week_start_date])
Revenue = 'public cc_detail'[annual_fees] + 'public cc_detail'[total_trans_amt] + 'public cc_detail'[interest_earned]
Current_week_Reveneue = CALCULATE(
 SUM('public cc_detail'[Revenue]),
 FILTER(
 ALL('public cc_detail'),
 'public cc_detail'[week_num2] = MAX('public cc_detail'[week_num2]))) 
Previous_week_Reveneue = CALCULATE(
 SUM('public cc_detail'[Revenue]),
 FILTER(
 ALL('public cc_detail'),
 'public cc_detail'[week_num2] = MAX('public cc_detail'[week_num2])-1))

3. Dashboard and Insights:
   Here I have also attached the dashboard pdfs for refernece ane the insights would be provided here

# Insights: 
WoW change: 
• Revenue increased by 28.8%, 
• Total Transaction Amt & Count increased by xx% & xx%
• Customer count increased by xx%
Overview YTD:
• Overall revenue is 57M
• Total interest is 8M
• Total transaction amount is 46M
• Male customers are contributing more in revenue 31M, female 26M
• Blue & Silver credit card are contributing to 93% of overall 
transactions
• TX, NY & CA is contributing to 68%
• Overall Activation rate is 57.5%
• Overall Delinquent rate is 6.06%

4. The powerbi dashboard reprort is exported and also is attached in the same github.
