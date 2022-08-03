## Time to put some of the SQL Work into Practice!

Head on over to the [SQL Practice Site](https://www.w3schools.com/sql/trysql.asp?filename=trysql_desc). This site has prebuilt tables that will work out quite nicely for what we want to do.

Rather than have you try to hop back and forth, here's an overview of each of the tables:

| CUSTOMERS  |              |             |         |      |            |         |
| ---------- | ------------ | ----------- | ------- | ---- | ---------- | ------- |
| CustomerID | CustomerName | ContactName | Address | City | PostalCode | Country |

| CATEGORIES |              |             |
| ---------- | ------------ | ----------- |
| CategoryID | CategoryName | Description |

| EMPLOYEES  |          |           |           |       |       |
| ---------- | -------- | --------- | --------- | ----- | ----- |
| EmployeeID | LastName | FirstName | BirthDate | Photo | Notes |

| ORDERDETAILS  |         |           |          |
| ------------- | ------- | --------- | -------- |
| OrderDetailID | OrderID | ProductID | Quantity |

| ORDERS  |            |            |           |           |
| ------- | ---------- | ---------- | --------- | --------- |
| OrderID | CustomerID | EmployeeID | OrderDate | ShipperID |

| PRODUCTS  |             |            |            |      |       |
| --------- | ----------- | ---------- | ---------- | ---- | ----- |
| ProductID | ProductName | SupplierID | CategoryID | Unit | Price |

| SHIPPERS  |             |       |
| --------- | ----------- | ----- |
| ShipperID | ShipperName | Phone |

| SUPPLIERS  |              |         |      |            |         |     |
| ---------- | ------------ | ------- | ---- | ---------- | ------- | --- |
| SupplierID | SupplierName | Address | City | PostalCode | Country |

## Now that we know our Schema, let's do the following (making sure that the table returns all useful data, not just the bare minimum):

1. Find all Customers in the USA or Mexico ordered Alphabetically by Contact Name
2. Find all Products that cost more than 40
   SELECT \* FROM Products WHERE Products.Price > 40

3. Find all Employees born before 1960.

SELECT \* FROM Employees WHERE Employes.Birthdate < "1960-01-01"

4. Find all Products that are Beverages
   SELECT \* FROM Products WHERE CategoryID = 1
   Avoid this.
   SELECT \* FROM Categories
   JOIN Products ON Categories.CategoryID = Products.CategoryID
   WHERE

5. Find all Employees Who have ordered something that shipped to Spain
   -Grab things
   -Join things
   -Then filter
   When you want to connect things, look for what info you need and what
   Select from Customers

6. Find all Orders with a total price over 2000 sorted from most expensive to least expensive.

(Solution will be pushed up in the Repo.)

## Additional Practice

For additional practice, check out [SQL Murder Mystery](https://mystery.knightlab.com/)
