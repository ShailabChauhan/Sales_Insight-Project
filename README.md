** Sales Insights Data Analysis Project

1. SQL database dump is in db_dump.sql file above. 

** Data Analysis Using SQL

1. Showing all customer records

    `SELECT * FROM customers;`

1. Showing total number of customers

    `SELECT count(*) FROM customers;`

1. Showing transactions for Chennai market (market code for chennai is Mark001

    `SELECT * FROM transactions where market_code='Mark001';`

1. Showing distrinct product codes that were sold in chennai

    `SELECT distinct product_code FROM transactions where market_code='Mark001';`

1. Showing transactions where currency is US dollars

    `SELECT * from transactions where currency="USD"`

1. Showing transactions in 2020 join by date table

    `SELECT transactions., date. FROM transactions INNER JOIN date ON transactions.order_date=date.date where date.year=2020;`

1. Showing total revenue in year 2020,

    `SELECT SUM(transactions.sales_amount) FROM transactions INNER JOIN date ON transactions.order_date=date.date where date.year=2020 and transactions.currency="INR\r" or transactions.currency="USD\r";`
	
1. Showing total revenue in year 2020, January Month,

    `SELECT SUM(transactions.sales_amount) FROM transactions INNER JOIN date ON transactions.order_date=date.date where date.year=2020 and and date.month_name="January" and (transactions.currency="INR\r" or transactions.currency="USD\r");`

1. Showing total revenue in year 2020 in Chennai

    `SELECT SUM(transactions.sales_amount) FROM transactions INNER JOIN date ON transactions.order_date=date.date where date.year=2020
and transactions.market_code="Mark001";`


Data Analysis Using Power BI and removing all the unwanted data like sales amount<=0 etc. 

1. Formula to create norm_amount column

`= Table.AddColumn(#"Filtered Rows", "norm_amount", each if [currency] = "USD" or [currency] ="USD#(cr)" then [sales_amount]*82 else [sales_amount], type any)`
