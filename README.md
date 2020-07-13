# Microsoft NorthWind modified

Below are links for a modified version of Microsoft NorthWind database with 
- Better primary keys
- Entities split up e.g. country string to country identifier
- No spaces in table names

### Create a populate
Use the [following link](https://gist.github.com/karenpayneoregon/9bdf1a7d5310ac1d562b2326d79d6038) for the script to create the database and populate tables best done in SSMS (SQL-Server Management Studio).

### Sample SELECT statements
- [Customers](https://gist.github.com/karenpayneoregon/55cfa05ac21809ffed6146089fd7649d) 
- [Employees](https://gist.github.com/karenpayneoregon/d7a287a9ebb18b4d9e1363f92812d447)
- [Products by category](https://gist.github.com/karenpayneoregon/18df5808020872215895192c50fcd482)
- [Order by order identifier](https://gist.github.com/karenpayneoregon/bc8329737eee80dfd2f9df0f9d3dbc63)
- [Order details by order identifier](https://gist.github.com/karenpayneoregon/2711f4edeaa9f374f6cafef479d265fc)
 
```sql
SELECT Cust.CustomerIdentifier, 
       Cust.CompanyName, 
       Cust.ContactId, 
       CT.ContactTitle, 
       C.FirstName, 
       C.LastName, 
       Cust.Street, 
       Cust.City, 
       Cust.Region, 
       Cust.PostalCode, 
       Countries.[Name] AS CountryName, 
       Cust.CountryIdentifier, 
       Cust.Phone, 
       Cust.Fax, 
       Cust.ContactTypeIdentifier, 
       Cust.ModifiedDate
FROM Customers AS Cust
     INNER JOIN Contacts AS C ON Cust.ContactId = C.ContactId
     INNER JOIN ContactType AS CT ON Cust.ContactTypeIdentifier = CT.ContactTypeIdentifier
     INNER JOIN Countries ON Cust.CountryIdentifier = Countries.CountryIdentifier;
```
# Advance evolving version
The following repository is a work in progress using Microsoft Entity Framework Core 3x

[Microsoft NorthWind database 2020 Part 1](https://github.com/karenpayneoregon/NorthWind-2020)
