# Credit_Card_Financial_Dashboard (MS POWER BI)

# Import data to SQL database
  -Prepare csv file  
  -Create tables in SQL  
  -Import csv file into SQL  

# DAX Queries
AgeGroup = SWITCH(  
TRUE(),  
'public cust_detail'[customer_age] <= 30, "20-30",  
'public cust_detail'[customer_age] >= 31 && 'public cust_detail'[customer_age] <= 40, "31-40",  
'public cust_detail'[customer_age] >= 41 && 'public cust_detail'[customer_age] <= 50, "41-50",  
'public cust_detail'[customer_age] >= 51 && 'public cust_detail'[customer_age] <= 60, "51-60",  
'public cust_detail'[customer_age] > 60, "60+",  
"unknown"  
)  
IncomeGroup = SWITCH(  
TRUE(),  
'public cust_detail'[income] <= 35000, "Low",  
'public cust_detail'[income] > 35000 && 'public cust_detail'[income] <=70000, "Med",  
'public cust_detail'[income] > 70000, "High",  
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

# Project Insights-   
WoW changes:  
• Revenue increased by 28,8%,  
• Total Transaction Amt & Count increased by 35% & 3,4%  
Overview YTD:  
• Overall revenue is 57M  
• Total interest is 8M  
• Total transaction amount is 46M  
• Male customers are contributing more in revenue 31M, female 26M  
• Blue & Silver credit card are contributing most of the overall  
transactions
• TX, NY & CA are the top 3 contributing states  
• Overall Activation rate withing 30 days is 57.5%  
• Overall Delinquent rate is 6.06%
