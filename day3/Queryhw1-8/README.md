**use Northwind;**

-- Q1 How many orders in NWDB

**select count(*) from Orders;**

-- Q2 How many order that the Ship City is Rio de Janeiro

**select count(OrderID) from Orders where ShipCity = 'Rio de Janeiro';**

-- Q3 Select all orders that the Ship City is Rio de Janeiro or Reims

**select count(OrderID) from Orders where ShipCity = 'Rio de Janeiro' OR ShipCity = 'Reims';**

-- Q4 Select all of the entries where the Company name has a z or a Z in the table of Customers

**select count(CustomerID) from Customers where CompanyName like '%z%' or CompanyName like '%Z%';**

-- Q5 We need to update all of our FAX information! This Day and age it is a must! 
-- Find me the Name of All of the companies that we do not have their FAX numbers! 
-- I would also like to know with whom I need to speak with, their contact numbers and what city they are base in

**select CompanyName, ContactName, Phone, City, Fax from Suppliers where Fax is null;**

-- Q6 Ahh there you are! My prize SPARTANTS! MY MARES AND MY STALLIONS! 
-- We need to re-target all of our Customers in Paris! Get me information on these clients

**select * from Customers where City = 'Paris';**

-- Q7 Can you find out, from these clients from Paris, whom orders the most by quantity? Who are our top 5 clients

**SELECT * from Orders
SELECT * from Customers

select top 5 count(Orders.OrderID) as 'Quantity of Orders', Customers.CompanyName
from Customers
left join Orders on Customers.CustomerID = Orders.CustomerID
where Customers.City = 'Paris'
group by Customers.CompanyName
order by count(Orders.OrderID) DESC;

SELECT TOP 5 COUNT(Orders.OrderID) AS 'quantity Of Orders', Customers.CompanyName, Customers.CustomerID
from Orders
RIGHT JOIN Customers ON Customers.CustomerID = Orders.CustomerID
WHERE Customers.City = 'Paris'
GROUP by Customers.CustomerID, 
         Customers.CompanyName
Order By count(Orders.OrderID)DESC;**

-- Q8 Can you find out which ones their deliveries took longer than 10 days? 
-- Display the Business/client name, contact name, all their contact details (don't forget the fax!), as well as the number of deliveries that where overdue! 
-- Just add a column named: 'Number overdue orders'! simple, thank you

**SELECT TOP 5
    Customers.CustomerID,
    Customers.CompanyName,
    Customers.ContactName,
    Customers.Phone,
    Customers.Fax,
    count(Orders.OrderID) as 'Overdue Orders'
    from Customers
inner join Orders on Customers.CustomerID = Orders.CustomerID
where Orders.ShippedDate - Orders.RequiredDate > 10
group by
    Customers.CustomerID,
    Customers.CompanyName,
    Customers.ContactName,
    Customers.Phone,
    Customers.Fax
order by count(Orders.OrderID) DESC;**
