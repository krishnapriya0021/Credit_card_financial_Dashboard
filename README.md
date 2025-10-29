**Credit Card Transaction and Customer Dashboard using Power BI
**
• Developed an interactive dashboard using
transaction and customer data from a SQL database,
to provide real-time insights.
• Streamlined data processing & analysis to monitor
key performance metrics and trends.
• Shared actionable insights with stakeholders based
on dashboard findings to support decision-making
processes.
======================
Project Objective
=====================
To develop a comprehensive credit card weekly dashboard that provides real-time insights into key 
performance metrics and trends,enabling stakeholders to monitorand analyze credit card operations
effectively.

============================
Import data to SQL database
============================
1. Prepare csv file
2. Create tables in SQL
3. import csv file into SQL

=======================
DAX Queries
=======================
AgeGroup = SWITCH(
TRUE(),
'public cust_detail'[customer_age] < 30, "20-30",
'public cust_detail'[customer_age] >= 30 && 'public cust_detail'[customer_age] < 40, "30-40",
'public cust_detail'[customer_age] >= 40 && 'public cust_detail'[customer_age] < 50, "40-50",
'public cust_detail'[customer_age] >= 50 && 'public cust_detail'[customer_age] < 60, "50-60",
'public cust_detail'[customer_age] >= 60, "60+",
"unknown"
)

IncomeGroup = SWITCH(
TRUE(),
'public cust_detail'[income] < 35000, "Low",
'public cust_detail'[income] >= 35000 && 'public cust_detail'[income] <70000, "Med",
'public cust_detail'[income] >= 70000, "High",
"unknown"
)

week_num2 = WEEKNUM('public cc_detail'[week_start_date])
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

Project Insights – Week 53 (31st Dec)
====================================
Week-over-Week (WoW) Highlights:

Revenue increased by 28.8%

Total Transaction Amount and Transaction Count rose by xx% and xx%, respectively

Customer Count grew by xx%

📈 Year-to-Date (YTD) Overview:
===================================
Total Revenue: $57M

Total Interest Earned: $8M

Total Transaction Volume: $46M

Revenue by Gender: Male – $31M | Female – $26M

Top Performing Credit Cards: Blue & Silver cards account for 93% of all transactions

Top Contributing States: TX, NY, and CA represent 68% of total performance

Activation Rate: 57.5%

Delinquency Rate: 6.06%

