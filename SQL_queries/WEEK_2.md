# Week 2
- [Practice Quiz](#practice-quiz)
- [Module 2 Coding Assignment](#module-2-coding-assignment)

*left to [Rubricator](../README.md)*

## Practice Quiz

**1. Find the distinct values for the extended step. The code has been started for you, but you will need to program the third line yourself before running the query.**

SQL code:</br> 
```SQL
SELECT DISTINCT Extended_step
FROM salary_range_by_job_classification;
```

Result:</br> 
| Extended_Step |
|--- |
| 0             |
| 11            |
| 6             |
| 2             |

**2. Excluding $0.00, what is the minimum bi-weekly high rate of pay (please include the dollar sign and decimal point in your answer)? The code has been started for you, but you will need to add onto the last line of code to get the correct answer.**

SQL code:</br> 
```SQL
SELECT MIN(Biweekly_high_Rate)
FROM salary_range_by_job_classification
WHERE Biweekly_high_Rate <> '$0.00';
```

Result:</br> 
| min(Biweekly_high_Rate) |
|--- |
| $100.00                 |

**3. What is the maximum biweekly high rate of pay (please include the dollar sign and decimal point in your answer)? The code has been started for you, but you will need to add onto the last line of code to get the correct answer.**

SQL code:</br> 
```SQL
SELECT MAX(Biweekly_high_Rate) 
FROM salary_range_by_job_classification;
```

Result:</br> 
| Max(Biweekly_high_Rate) |
|--- |
| $9726.38                |


**4. What is the pay type for all the job codes that start with '03'? The code has been started for you, but you will need to program the fourth and fifth lines yourself before running the query.**

SQL code:</br> 
```SQL
SELECT job_code
,pay_type
FROM salary_range_by_job_classification
WHERE Job_Code LIKE '03%';
```

Result:</br> 
| Job_Code | Pay_Type |
|--- |--- |
| 0380     | B        |
| 0381     | B        |
| 0382     | B        |
| 0390     | B        |
| 0395     | B        |
| 0380     | B        |
| 0381     | B        |
| 0382     | B        |

**5. Run a query to find the Effective Date (eff_date) or Salary End Date (sal_end_date) for grade Q90H0? The code has been started for you, but you will need to program the third through the sixth lines yourself before running the query.**

SQL code:</br> 
```SQL
SELECT eff_date, sal_end_date, grade
FROM salary_range_by_job_classification
WHERE grade = 'Q90H0';
```

Result:</br> 
| Eff_Date               | Sal_End_Date           | Grade |
|--- |--- |--- |
| 12/26/2009 12:00:00 AM | 06/30/2010 12:00:00 AM | Q90H0 |

**6. Sort the Biweekly low rate in ascending order. There is no starter code, as you need to write and run the query on your own. Hint: there are 4 lines to run this query.**

SQL code:</br> 
```SQL
SELECT Biweekly_Low_Rate
FROM salary_range_by_job_classification
ORDER BY Biweekly_Low_Rate ASC
LIMIT 7;
```

Result:</br> 
| Biweekly_Low_Rate |
|--- |
| $0.00             |
| $0.00             |
| $0.00             |
| $0.00             |
| $100.00           |
| $100.00           |
| $10059.00         |

**7. Write and run a query, with no starter code to answer this question: What Step are Job Codes 0110-0400? Hint: there are 6 lines to run this query.**

SQL code:</br> 
```SQL
SELECT Job_Code, Step
FROM salary_range_by_job_classification
WHERE Job_Code BETWEEN '0110' AND '0400';
```

Result:</br> 
| Job_Code | Step |
|--- |--- |
| 0110     | 1    |
| 0111     | 1    |
| 0112     | 1    |
| 0114     | 1    |
| 0115     | 1    |
| 0116     | 1    |
| 0118     | 1    |
| 0119     | 1    |
| 0140     | 1    |
| 0150     | 1    |
| 0170     | 1    |
| 0180     | 1    |
| 0190     | 1    |
| 0380     | 1    |
| 0381     | 1    |
| 0382     | 1    |
| 0390     | 1    |
| 0395     | 1    |
| 0400     | 1    |
| 0140     | 1    |
| 0150     | 1    |
| 0380     | 1    |
| 0381     | 1    |
| 0382     | 1    |

**8. Find the distinct values for the extended step. The code has been started for you, but you will need to program the third line yourself before running the query.**

SQL code:</br> 
```SQL
SELECT Biweekly_High_Rate,
Biweekly_Low_Rate, 
(Biweekly_High_Rate-Biweekly_Low_Rate) AS Result 
FROM salary_range_by_job_classification
WHERE Job_Code='0170';
```

Result:</br> 
| Biweekly_High_Rate | Biweekly_Low_Rate | Result |
|--- |--- |--- |
| $4142.00           | $4142.00          |      0 |

**9. Write and run a query, with no starter code or hints to answer this question: What is the Extended Step for Pay Types M, H, and D?**

SQL code:</br> 
```SQL
SELECT Extended_Step, Pay_Type
FROM salary_range_by_job_classification
WHERE Pay_Type = 'M' OR
      Pay_Type = 'H' OR
      Pay_Type = 'D';
```

Result:</br> 
| Extended_Step | Pay_Type |
|--- |--- |
| 0             | D        |
| 0             | D        |
| 0             | D        |
| 0             | M        |
| 0             | D        |
| 0             | D        |
| 0             | M        |
| 0             | H        |
| 0             | H        |
| 0             | H        |
| 0             | H        |
| 0             | H        |
| 0             | H        |
| 0             | H        |
| 0             | H        |

**10. Write and run a query, with no starter code or hints to answer this question: What is the step for Union Code 990 and a Set ID of SFMTA or COMMN?**

SQL code:</br> 
```SQL
SELECT Step
,Union_Code
,SetID
FROM salary_range_by_job_classification
WHERE Union_Code = '990' AND (SetID = 'SFMTA' OR SetID = 'COMMN');
```

Result:</br> 
| Step | Union_Code | SetID |
|--- |--- |--- |
| 1    | 990        | COMMN |

*left to [Rubricator](../README.md)*

## Module 2 Coding Assignment

All of the questions in this quiz refer to the open source Chinook Database. Please familiarize yourself with the ER diagram to familiarize yourself with the table and column names to write accurate queries and get the appropriate answers.

**1. Run Query: Find all the tracks that have a length of 5,000,000 milliseconds or more.**

SQL code:</br> 
```SQL
SELECT TrackId, Name, UnitPrice 
FROM tracks
WHERE milliseconds >= 5000000;
```

Result:</br> 
| TrackId | Name                    | UnitPrice |
|--- |--- |--- |
|    2820 | Occupation / Precipice  |      1.99 |
|    3224 | Through a Looking Glass |      1.99 |

**2. Run Query: Find all the invoices whose total is between $5 and $15 dollars.**

SQL code:</br> 
```SQL
SELECT Count(total) AS Total_Records
FROM invoices
WHERE total BETWEEN 5 AND 15
```

Result:</br> 
| Total_Records |
|--- |
|           168 |

**3. Run Query: Find all the customers from the following States: RJ, DF, AB, BC, CA, WA, NY.**

SQL code:</br> 
```SQL
SELECT Company
FROM customers
WHERE State IN ('RJ', 'DF', 'AB', 'BC', 'CA', 'WA', 'NY') 
	AND FirstName = 'Jack' 
	AND LastName = 'Smith';
```

Result:</br> 
| Company               |
|--- |
| Microsoft Corporation |

**4. Run Query: Find all the invoices for customer 56 and 58 where the total was between $1.00 and $5.00.**</br>
**What was the invoice date for invoice ID 315?**

SQL code:</br> 
```SQL
SELECT InvoiceId
,CustomerId
,InvoiceDate
,total
FROM invoices
WHERE CustomerId BETWEEN 56 AND 58 
      AND total BETWEEN 1.00 AND 5.00 
      AND InvoiceId = 315;
```

Result:</br> 
| InvoiceId | CustomerId | InvoiceDate         | Total |
|--- |--- |--- |--- |
|       315 |         58 | 2012-10-27 00:00:00 |  1.98 |

**5. Run Query: Find all the tracks whose name starts with 'All'.**

SQL code:</br> 
```SQL
SELECT TrackId
,Name
FROM tracks
WHERE Name LIKE 'All%'
```

Result:</br> 
| TrackId | Name                                   |
|--- |--- |
|      38 | All I Really Want                      |
|     134 | All For You                            |
|     385 | All Star                               |
|    1009 | All My Life                            |
|    1608 | All My Love                            |
|    1892 | All Within My Hands                    |
|    2192 | All or None                            |
|    2274 | All Dead, All Dead                     |
|    2888 | All the Best Cowboys Have Daddy Issues |
|    2969 | All Because Of You                     |</br>
(Output limit exceeded, 10 of 15 total rows shown)

**6. Run Query: Find all the customer emails that start with "J" and are from gmail.com.**

SQL code:</br> 
```SQL
SELECT FirstName
,LastName
,Email
FROM customers
WHERE Email LIKE 'j%@gmail.com';
```

Result:</br> 
| FirstName | LastName | Email               |
|--- |--- |--- |
| Julia     | Barnett  | jubarnett@gmail.com |

**7. Run Query: Find all the invoices from the billing city Brasília, Edmonton, and Vancouver and sort in descending order by invoice ID.**</br>
**What is the total invoice amount of the first record returned?**

SQL code:</br> 
```SQL
SELECT InvoiceId
,Total
FROM invoices
WHERE BillingCity IN ('Brasília', 'Edmonton', 'Vancouver')
ORDER BY InvoiceId DESC
LIMIT 5;
```

Result:</br> 
| InvoiceId | Total |
|--- |--- |
|       362 | 13.86 |
|       351 |  1.98 |
|       328 |  0.99 |
|       319 |  8.91 |
|       276 |  5.94 |

**8. Run Query: Show the number of orders placed by each customer (hint: this is found in the invoices table) and sort the result by the number of orders in descending order.**
**What is the number of items placed for the 8th person on this list?** 

SQL code:</br> 
```SQL
SELECT CustomerId
,COUNT(*) AS Orders
FROM invoices
Group by CustomerId
ORDER BY Orders DESC
LIMIT 7;
```

Result:</br> 
| CustomerId | Orders |
|--- |--- |
|          1 |      7 |
|          2 |      7 |
|          3 |      7 |
|          4 |      7 |
|          5 |      7 |
|          6 |      7 |
|          7 |      7 |</br>
(Output limit exceeded, 10 of 59 total rows shown)

**9. Run Query: Find the albums with 12 or more tracks.**
**While the number of records returned is limited to 10, the query, if run correctly, will indicate how many total records there are.**

SQL code:</br> 
```SQL
SELECT AlbumId
,COUNT(*) AS Ntracks
FROM Tracks
GROUP BY AlbumId
HAVING COUNT (*) >= 12;
```

Result:</br> 
| AlbumId | Ntracks |
|--- |--- |
|       5 |      15 |
|       6 |      13 |
|       7 |      12 |
|       8 |      14 |
|      10 |      14 |
|      11 |      12 |
|      12 |      12 |
|      14 |      13 |
|      18 |      17 |
|      21 |      18 |</br>
(Output limit exceeded, 10 of 158 total rows shown)

*left to [Rubricator](../README.md)*