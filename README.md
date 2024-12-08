
# Sales Insights Data Analysis Project

### Dashboard Link : https://app.powerbi.com/groups/me/reports/40929d7c-eb0e-43bb-961d-e8ecee9fa0e6?ctid=783ff96b-fe13-406b-b48d-45dc1853cbad&pbi_source=linkShare

## Problem Statement

The purpose of this project is to analyze sales and customer data from a retail business to extract meaningful insights and support data-driven decision-making. Using MySQL and Power BI, the project aims to address the following key challenges:

 - Customer Analysis
 - Market Performance Analysis
 - Revenue Trends
 - Currency Normalization
 - Time-Based Revenue Insights
### Steps followed 

- Step 1:  Download [db_dump.sql]() file to your local computer and import it in MySQL

- Step 2: Perform Data Analysis Using SQL

  Execute queries to retrieve customer records, market-specific transactions, and revenue trends.

  Analyze total revenue, product sales, and transactions based on year and market.
- Step 3: Load Data into Power BI

  Connect Power BI to the MySQL database and load all required tables for analysis.
- Step 4: Clean and Transform Data
  
  Normalize sales amounts with a calculated norm_amount column.
  Handle invalid data and set up relationships between the tables for better  modeling.
- Step 5: Create Performance Insights dashboard view: 
   
   Develop visuals for key metrics:

   Revenue by Market,
   Sales Quantity by Market,
   Top 5 Customers,
   Top 5 Products,
   Revenue by Trend

- Step 6: Create Profit Analysis dashboard view: 
   
   Develop visuals for profit-focused insights:

   Profit Contribution % by Market,
   Revenue Contribution % by Market,
   Profit % by Market,
   Revenue Trend over Time,
   Top 5 Customers with Profit Margin Contribution

- Step 7: Create Performance Insights dashboard view: 

   Develop visuals for Performance-focused insights:

   Revenue Contribution % by Market,
   Top 5 Customers with more insights,
   Revenue Trend over Time with more insights

- Step 8: Address Feedback

   Use comments and suggestions to refine normalized sales amount calculations and insights.
- Step 9: Resolve Dashboard and Data Issues

   Fix errors in data normalization and improve dashboard refresh rates.
- Step 10: Add Profit Margin Contribution Measure

   Implement a custom measure to calculate and display profit margin contributions.
- Step 11: Aggregate Data for Sales Insights

   Summarize data at different levels, such as market and customer categories, for better analysis.

- Step 12: The report was then published to Power BI Service.


# SQL Queries
Show all customer records

          SELECT * FROM customers;

Show total number of customers

          SELECT count(*) FROM customers;

Show transactions for Chennai market (market code for chennai is Mark001

          SELECT * FROM transactions where market_code='Mark001';

Show distrinct product codes that were sold in chennai

          SELECT distinct product_code FROM transactions where market_code='Mark001';

Show transactions where currency is US dollars

          SELECT * from transactions where currency="USD"

Show transactions in 2020 join by date table

          SELECT transactions.*, date.* FROM transactions INNER JOIN date ON transactions.order_date=date.date where date.year=2020;

Show total revenue in year 2020,

          SELECT SUM(transactions.sales_amount) FROM transactions INNER JOIN date ON transactions.order_date=date.date where date.year=2020 and transactions.currency="INR\r" or transactions.currency="USD\r";

Show total revenue in year 2020, January Month,

          SELECT SUM(transactions.sales_amount) FROM transactions INNER JOIN date ON transactions.order_date=date.date where date.year=2020 and and date.month_name="January" and (transactions.currency="INR\r" or transactions.currency="USD\r");

Show total revenue in year 2020 in Chennai

          SELECT SUM(transactions.sales_amount) FROM transactions INNER JOIN date ON transactions.order_date=date.date where date.year=2020 and transactions.market_code="Mark001";

  # Power BI Queries
  Formula to remove -1/0 values and create norm_amount column
    
         = Table.AddColumn(#"Remove -1/0 in sales_amt", "norm_sales_amount", each if [currency] = "USD#(cr)" then [sales_amount]*84.44 else [sales_amount])         

# Snapshot of Dashboard 
## Key Insights

 ![Screenshot 2024-12-08 021821](https://github.com/user-attachments/assets/45bca58f-f0d5-4cd6-83f3-746e30c126a9)
 
 ## Profit Analysis
 
![Screenshot 2024-12-08 062348](https://github.com/user-attachments/assets/ef056887-bc50-42a7-88df-331fba278ae0)

## Performance Insights

![Screenshot 2024-12-08 065039](https://github.com/user-attachments/assets/cf0434ac-0c8c-4a47-aae9-69df23f226cb)

# 
# Insights

A three page report was created on Power BI Desktop & it was then published to Power BI Service.

Following inferences can be drawn from the dashboard;
## Key Insigts 
### Total Revenue = ₹985M 
### [1] Revenue by Market

   Delhi NCR - ₹483M

   Mumbai - ₹65M

   Ahmedabad - ₹99M

   Bhopal - ₹26M

   Nagpur - ₹17M


           thus, highest revenue was generated by Delhi NCR.           
### Total Sales Quantity = 2M
### [2] Sales Quantity by Market

   Delhi NCR - 894k

   Mumbai - 252k

   Kochi - 252k

   Ahmedabad - 142k

   Nagpur - 106k
  
           thus, the highest sales quantity was achieved in Delhi NCR.
  
  ### [3] Top 5 Most Selling Products 
  
   (Blank) - ₹469M

   Prod040 - ₹24M

   Prod159 - ₹18M

   Prod065 - ₹16M 

   Prod018 - ₹16M

   The blank product entry indicates a data provider's side issue and should be addressed by them.
       
          (Blank) was the most selling product   
 ## Profit Analysis
 ### Total Profit Margin = ₹2.1M
 ### [1] Profit Contribution % by Market

1.1) Delhi NCR - 48.5%

1.2) Mumbai - 19.8%

1.3) Ahmedabad - 11.6%

1.4) Bhopal - 9.3%

1.5)  Nagpur- 5.7%

          thus, the highest profit contribution came from Delhi NCR. 
 ### [2] Revenue Contribution % by Market

 2.1) Delhi NCR - 52.8%

 2.2) Mumbai - 15.2%

 2.3) Ahmedabad - 13.4%

 2.4) Bhopal - 6%

 2.5) Nagpur - 5.6%

         thus, the highest revenue contribution came from Delhi NCR.

### [3] Profit % by Market

3.1) Surat - 4.9%

3.2) Patna - 4.1%

3.3) Bhubaneshwar - 4.0%

3.4) Bhopal - 3.9%

3.5) Kochi - 3.7%

         thus, the highest profit % was achieved in Surat.

### [4] Top 5 Customers revenue and profit margin

4.1) Electricalsara Stores - ₹413M (2.3%)

4.2) Electricalytical - ₹49.6M (3.4%)

4.3) Excel Stores - ₹49.1M (1.4%)

4.4) Premium Stores - ₹44M (2.3%)

4.5) Nixon - ₹43M (4.1%)

         thus, the highest revenue was generated by Electricalsara Stores.

### [5] Other Key observations

5.1) Revenue Margin % has dropped to 1.3% in the most recent data

5.2) Revenue dropped to ₹14M in the most recent data, which is the lowest in the entire period.

## Acknowledgements

#### CodeBasics
 - [Youtube](https://www.youtube.com/c/codebasics)
 - [Github](github.com/codebasics)

## Authors

- [@ParthSJ](https://github.com/ParthSJ)
