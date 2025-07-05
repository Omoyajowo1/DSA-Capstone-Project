Kultra Mega Stores Inventory 
A capstone project for my sql data analysis class with DSA incubator Hub 

As a data anlyst using my skills to solve these case scenarios
![case 1](https://github.com/user-attachments/assets/15057fb9-685f-4b5e-813c-302e5f21424d)
![case 2](https://github.com/user-attachments/assets/10a78258-4f47-4abe-a9e2-5152eca4d15e)

_______________________________________________________________________________________________________
Project overview 
I'm to support  the Abuja division of KMS as a Business Intelligence Analyst 
The Business Manager has shared an Excel file containing order data from 2009 to 
2012 and has requested that I analyze the data and present your key insights and findings. 
________________________________________________________________________________________________________
Tools Used :

Microsoft Sql server management studio was used for: 
1. Data importing
2. Assign the right data type for each column
3. Assigning the primary key to the Row_ID
4. Joining of two tables together
5. Analysisng every case scenario

At each stage of analysis the data Sales and profit is the main focus for the business 
By so all analysis is meant to find those things costing the business more with no little or no profit 

_______________________________________________________________________________________________________________________
Data analysis 
1. The most performing category in terms of sales is technology
2. The top 3 performing region in terms of sales are Alantic, Quebec,Prarie
3. The 3 under performing region in term of sales are West, West, Yukon
4. the total sales of appliances in Ontario was 202346.84







_____________________________________________________________________________________________________________________________________________________________________________
QUARIES FOR EACH BUSINESS CASE SCENARIO

select * from [dbo].[KMS Sql Case Study (1)]

-------Question 1
select top 1*from (
select Product_Category, Sales from [KMS Sql Case Study (1)]) as HighestSales 
order by Sales desc

------ Question 2
select top 3* from (
select Region, Sales from [KMS Sql Case Study (1)]) as Top3_Region
order by sales desc

select top 3* from (
select Region, Sales from [KMS Sql Case Study (1)]) as Bottom3_Region
order by sales asc

alter table [dbo].[KMS Sql Case Study (1)]
alter column region

-
----Question 3
select Region, Product_Sub_Category, Sales, SUM (Sales) as [Total Sales]
from [KMS Sql Case Study (1)]
where Region in ('Ontario') and product_sub_category in ('appliances')
group by Sales, Region, Product_Sub_Category
order by [Total Sales]
------correct answer to Q3
select Region, product_sub_category, sum (sales) as [Total Sales]
from [KMS Sql Case Study (1)]
where Region= 'ontario' and product_sub_category = 'appliances'
group by product_sub_category, Region

----Question 4 
select top 10 * from(
select customer_name, order_quantity, sales, shipping_cost, Profit from [KMS Sql Case Study (1)]) as Revenue
order by profit asc

-----question 5
select ship_mode, sum (shipping_cost) as [Total Shipping Cost]
from [KMS Sql Case Study (1)]  
group by ship_mode
order by [Total Shipping Cost] desc


--------Q6
select top 10 * from  (
select customer_name, product_sub_category, sales, profit from [KMS Sql Case Study (1)]) as [Total Revenue]
order by Profit desc

--------Q7
select top 1 Customer_Name, Customer_Segment, sum (sales) as [Total Sales]
from [KMS Sql Case Study (1)]
where Customer_Segment in ('small business')
group by Customer_Name, Customer_Segment
order by [Total Sales] desc

--------Q8
select top 1 Customer_Name, Customer_segment, sum (order_quantity) as [Total Order]
from [KMS Sql Case Study (1)]
where Customer_Segment in ('corporate') and Order_date between '2009-01-01' and '2012-12-31'
group by Customer_Name, Customer_Segment
order by [Total Order]desc

------Q9
select top 1 customer_name, customer_segment, sum (profit) as [Most Profitable]
from [KMS Sql Case Study (1)]
where Customer_Segment in ('Consumer')
group by Customer_Name, Customer_Segment
order by [Most Profitable] desc


---------Q10
select * from [dbo].[KMS Sql Case Study (1)]
select * from [dbo].[Order_Status]

select kms.Customer_name, 
	kms.customer_segment, 
	kms.Product_Category,
	d.order_Id,
	d.status
from [KMS Sql Case Study (1)] kms
join Order_Status d
on Kms.row_id = d.Order_ID

--------Q11
Select order_priority, ship_mode,shipping_cost
from [KMS Sql Case Study (1)]
where Ship_Mode in ('delivery truck', 'express air')
group by Order_Priority, Ship_Mode, Shipping_Cost
order by Shipping_Cost desc
________________________________________________________________________________________________________________________________________________________________________


















