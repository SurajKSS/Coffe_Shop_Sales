# Coffe_Shop_Sales
This project describes the sales of coffee of a Cafe... 


-- Suraj Kumar Singh



-- Q1 Total Sales Revenue:
-- 
-- What is the total sales revenue for the entire dataset?

create table total_sales_revenue(Revenue INT )

select
	Sum(Transaction_qty * Unit_price)
from
	coffee_sales_table cst 

insert
	into
	total_sales_revenue(Revenue)
values (623586);
-- Suraj Kumar singh
-- Q2 Sales by Store Location
-- How does sales revenue compare across different store locations?
-- create table Sales_revenue_across_different_store()
-- Step 1: Create the new table
create table sales_by_location (
    store_location VARCHAR(255),
    total_sales DECIMAL(10,
2)
);
-- Step 2: Insert data into the new table
insert
	into
	sales_by_location (store_location,
	total_sales)
select
	store_location,
	SUM(transaction_qty * unit_price) as total_sales
from
	coffee_sales_table cst
group by
	store_location
order by
	total_sales desc;







-- Q3 Sales by Product Category:
-- What is the distribution of sales revenue among different product categories?
-- Step 1: Create the new table
create table sales_by_product_category (
    product_category VARCHAR(255),
    total_sales DECIMAL(10,
2)
);
-- Step 2: Insert data into the new table
insert
	into
	sales_by_product_category(product_category ,
	total_sales)
   select
	product_category,
	SUM(transaction_qty * unit_price) as total_sales
from
	coffee_sales_table
group by
	product_category
order by
	total_sales desc;







-- Q4 Product Performance:

-- Which products generate the most revenue and which generate the least?


CREATE TABLE product_performance (
    product_id INT,
    product_detail VARCHAR(255),
    total_sales DECIMAL(10, 2)
);

INSERT INTO product_performance (product_id, product_detail, total_sales)
SELECT 
    product_id,
    product_detail,
    SUM(transaction_qty * unit_price) AS total_sales
FROM 
    coffee_sales_table 
GROUP BY 
    product_id, product_detail
ORDER BY 
    total_sales DESC;
   
   
   
   
   
   
   
   
--    Q5 Peak Sales Hours:
-- 
-- During which hours of the day are sales the highest?
   
   CREATE TABLE peak_performance (
    hour INT,
    total_sales DECIMAL(10, 2))
   
   INSERT INTO peak_performance (hour, total_sales)
SELECT 
    HOUR(transaction_time) AS hour,
    SUM(transaction_qty * unit_price) AS total_sales
FROM 
    coffee_sales_table cst 
GROUP BY 
    hour
ORDER BY 
    total_sales DESC;

   
   
   

-- Question and solution ends here;









