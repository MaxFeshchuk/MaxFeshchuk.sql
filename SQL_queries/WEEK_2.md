# Practice Quiz

*left to [Rubricator](../README.md)*

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