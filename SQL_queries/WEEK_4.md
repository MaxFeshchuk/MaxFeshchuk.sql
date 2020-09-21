# Week 4 (Module 4 Coding Questions)

*left to [Rubricator](../README.md)*

## Practice Quiz

All of the questions in this quiz refer to the open source Chinook Database. Please familiarize yourself with the ER diagram in order to familiarize yourself with the table and column names in order to write accurate queries and get the appropriate answers.

![ER diagram](images/ChinookDatabaseSchema.png)

**1. Pull a list of customer ids with the customer’s full name, and address, along with combining their city and country together. Be sure to make a space in between these two and make it UPPER CASE. (e.g. LOS ANGELES USA)**</br>
**What is the city and country result for CustomerID 16?**

SQL code:</br> 
```SQL
SELECT CustomerId
,FirstName
,LastName
,UPPER(City ||" "|| Country) AS Address
FROM customers
WHERE CustomerId = 16;
```

Result:</br>
| CustomerId | FirstName | LastName | Address           |
|--- |--- |--- |--- |
|         16 | Frank     | Harris   | MOUNTAIN VIEW USA |

**2. Create a new employee user id by combining the first 4 letters of the employee’s first name with the first 2 letters of the employee’s last name. Make the new field lower case and pull each individual step to show your work.**</br>
**What is the final result for Robert King?**

SQL code:</br> 
```SQL
SELECT employeeid
,FirstName
,LastName
,SUBSTR(FirstName, 1, 4) AS First_Step
,SUBSTR(LastName, 1, 2) AS Second_Step
,LOWER(SUBSTR(FirstName, 1, 4)||SUBSTR(LastName, 1, 2)) AS UserId
FROM employees
WHERE FirstName = 'Robert' AND LastName = 'King'
```

Result:</br>
| EmployeeId | FirstName | LastName | First_Step | Second_Step | UserId |
|--- |--- |--- |--- |--- |--- |
|          7 | Robert    | King     | Robe       | Ki          | robeki |

**3. Show a list of employees who have worked for the company for 15 or more years using the current date function. Sort by lastname ascending.**</br>
**What is the lastname of the last person on the list returned?**

SQL code:</br> 
```SQL
SELECT FirstName
,LastName
,STRFTIME('%Y','now')-STRFTIME('%Y',HireDate) AS ExperienceWork
FROM employees
ORDER BY LastName ASC
```

Result:</br>
| FirstName | LastName | ExperienceWork |
|--- |--- |--- |
| Andrew    | Adams    |             18 |
| Laura     | Callahan |             16 |
| Nancy     | Edwards  |             18 |
| Steve     | Johnson  |             17 |
| Robert    | King     |             16 |
| Michael   | Mitchell |             17 |
| Margaret  | Park     |             17 |
| Jane      | Peacock  |             18 |

**4. Profiling the Customers table, answer the following question.**</br>
**Are there any columns with null values?**

SQL code:</br> 
```SQL
SELECT COUNT(*)
,a.Chek
FROM(
  SELECT FirstName
  ,Phone
  ,Address
  ,PostalCode
  ,Company
  ,Fax
  ,Case 
    WHEN FirstName is NULL THEN 'Ok'
    WHEN Phone is NULL THEN 'Phone is NULL'
    WHEN Address is NULL THEN 'Address is NULL'
    WHEN PostalCode is NULL THEN 'PostalCode is NULL'
    WHEN Company is NULL THEN 'Company is NULL'
    WHEN Fax is NULL THEN 'Fax is NULL'
  END Chek 
  FROM Customers) AS a
GROUP BY a.chek
```

Result:</br>
| COUNT()   |           a.Chek |
|--- |--- |
|       10 |               None |
|       44 |    Company is NULL |
|        1 |      Phone is NULL |
|        4 | PostalCode is NULL |

**5. Find the cities with the most customers and rank in descending order.**</br>
**Which of the following cities indicate having 2 customers?**

SQL code:</br> 
```SQL
SELECT COUNT(*) AS Result, City
FROM Customers
GROUP BY City
ORDER BY Result DESC 
Limit 6;
```

Result:</br>
| Result | City          |
|--- |--- |
|      2 | Berlin        |
|      2 | London        |
|      2 | Mountain View |
|      2 | Paris         |
|      2 | Prague        |
|      2 | São Paulo     |

**6. Create a new customer invoice id by combining a customer’s invoice id with their first and last name while ordering your query in the following order: firstname, lastname, and invoiceID.**</br>
**Select all of the correct "AstridGruber" entries that are returned in your results.**

SQL code:</br> 
```SQL
SELECT c.FirstName
,c.LastName
,i.InvoiceId
,c.FirstName ||c.LastName|| i.InvoiceId AS NewId
FROM  invoices AS i LEFT JOIN   customers AS c
ON c.customerId=i.customerid
WHERE NewId LIKE 'AstridGruber%'
```

Result:</br>
| FirstName | LastName | InvoiceId | NewId           |
|--- |--- |--- |--- |
| Astrid    | Gruber   |        78 | AstridGruber78  |
| Astrid    | Gruber   |        89 | AstridGruber89  |
| Astrid    | Gruber   |       144 | AstridGruber144 |
| Astrid    | Gruber   |       273 | AstridGruber273 |
| Astrid    | Gruber   |       296 | AstridGruber296 |
| Astrid    | Gruber   |       318 | AstridGruber318 |
| Astrid    | Gruber   |       370 | AstridGruber370 |

*left to [Rubricator](../README.md)*