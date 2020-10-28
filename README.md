
''' SQL

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
Order By count(Orders.OrderID)DESC;

-- Q7


SELECT TOP 5
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
order by count(Orders.OrderID) DESC;

--Q8

