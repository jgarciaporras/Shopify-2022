# Shopify-2022
Summer 2022 Data Science Intern Challenge 


Please complete the following questions, and provide your thought process/work. You can attach your work in a text file, link, etc. on the application page. Please ensure answers are easily visible for reviewers!


## Question 1: Given some sample data, write a program to answer the following: click here to access the required data set

On Shopify, we have exactly 100 sneaker shops, and each of these shops sells only one model of shoe. We want to do some analysis of the average order value (AOV). When we look at orders data over a 30 day window, we naively calculate an AOV of $3145.13. Given that we know these shops are selling sneakers, a relatively affordable item, something seems wrong with our analysis. 

a.	Think about what could be going wrong with our calculation. Think about a better way to evaluate this data. 

The issue is that AOV was calculated using the average of total Order_amount. 

b.	What metric would you report for this dataset?

It should be calculated using this formula:
AOV = SUM(Order_amount) / SUM(total_items)

c.	What is its value?

Giving us the AOV of $357.922, which would be the correct AOV.

## Question 2: For this question you’ll need to use SQL. Follow this link to access the data set required for the challenge. Please use queries to answer the following questions. Paste your queries along with your final numerical answers below.

a.	How many orders were shipped by Speedy Express in total?

SELECT count(orderID) as 'Qty of Orders', b.ShipperName  FROM Orders a inner join Shippers  b on a.ShipperID= b.ShipperID
group by  b.ShipperName

Answer:54 

b.	What is the last name of the employee with the most orders?

SELECT count(orderID) 'Qty of Orders', LastName 'Employee LastName'FROM [Orders] a inner join Employees b 
on a.EmployeeID = b.EmployeeID
group by LastName
order by count(orderID) desc

Answer: Peacock

c.	What product was ordered the most by customers in Germany?

SELECT c.ProductId, ProductName, SUM(b.Quantity) 'Product Quantity' FROM Orders a inner join OrderDetails b 
on a.OrderID= b.OrderID
inner join Products c on b.ProductId = c.ProductId
inner join Customers d on a.customerId = d.CustomerID
where Country='Germany'
group by c.ProductId,ProductName
order by SUM(b.Quantity) desc

Answer: 	Boston Crab Meat



