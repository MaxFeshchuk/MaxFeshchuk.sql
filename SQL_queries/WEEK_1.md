# Practice Simple Select Queries
*left to [Rubricator](../README.md)*

To prepare for the graded coding quiz, you will be asked to execute a query, read the results, and select the correct answer you found in the results. This question is for you to practice executing queries. I have provided you the script for this query, a simple select statement. Think of this as a sandbox for you to practice. As you practice executing queries, take time to read the results in order to prepare for the quiz and get comfortable writing a basic select statement.

**1. Run query: Retrieve all the data from the tracks table. Who is the composer for track 18?**

SQL code:</br> 
```SQL
SELECT TrackId
,Composer 
FROM Tracks
WHERE trackid = 18;
```

Result:</br> 
| TrackId | Composer|
|--- | --- |
| 18 | AC/DC |

**2. Run Query: Retrieve all data from the artists table. Look at the list of artists, how many artists are you familiar with (there is no wrong answer here)?**

SQL code:</br> 
```SQL
SELECT *
FROM Artists
WHERE ArtistId IN (1, 22);
```

Result:</br>
| ArtistId | Name         |
|--- | --- |
|        1 | AC/DC        |
|       22 | Led Zeppelin |

**3. Run Query: Retrieve all data from the invoices table. What is the billing address for customer 31?**

SQL code:</br> 
```SQL
SELECT CustomerId
,BillingAddress
FROM Invoices
WHERE CustomerId = 31
LIMIT 1;
```

Result:</br>
| CustomerId | BillingAddress        |
|--- | --- |
|         31 | 194A Chain Lake Drive |

**4. Run Query: Return the playlist id, and name from the playlists table. How many playlists are there?**

SQL code:</br>
```SQL
SELECT Count(*) AS Count_playlists
FROM Playlists
```

Result:</br>
| Count_playlists |
|--- |
|              18 |

**5. Run Query: Return the Customer Id, Invoice Date, and Billing City from the Invoices table. What city is associated with Customer ID number 42? What was the invoice date for the customer in Santiago?**

SQL code:</br>
```SQL
SELECT CustomerId
,InvoiceDate
,BillingCity 
FROM Invoices
Where CustomerId = 42 or BillingCity LIKE 'Santiago'
GROUP BY BillingCity
```

Result:</br>
| CustomerId | InvoiceDate         | BillingCity |
|--- |--- |--- |
|         42 | 2013-11-03 00:00:00 | Bordeaux    |
|         57 | 2012-10-14 00:00:00 | Santiago    |

**6. Run Query: Return the First Name, Last Name, Email, and Phone, from the Customers table. What is the telephone number for Jennifer Peterson?**

SQL code:</br>
```SQL
SELECT FirstName, 
LastName, 
Email, 
Phone
FROM Customers
WHERE FirstName = 'Jennifer' AND LastName = 'Peterson';
```
Result:</br>
| FirstName | LastName | Email               | Phone             |
|--- |--- |--- |--- |
| Jennifer  | Peterson | jenniferp@rogers.ca | +1 (604) 688-2255 |

**7. Run Query: Return the Track Id, Genre Id, Composer, Unit Price from the Tracks table. How much do these tracks cost?**

SQL code:</br>
```SQL
SELECT --TrackId, 
--GenreId, 
--Composer, 
UnitPrice
,Count(UnitPrice) AS Count_Price
--, Sum(UnitPrice) As TotalPrice
FROM Tracks
GROUP BY UnitPrice;
```

Result:</br>
| UnitPrice | Count_Price |
|--- |--- |
|      0.99 |        3290 |
|      1.99 |         213 |

**8. Run Query: Select all the columns from the Playlist Track table and limit the results to 10 records. How might this information be used?**

SQL code:</br>
```SQL
SELECT *
FROM Playlist_track 
LIMIT 10;
```

Result:</br>
| PlaylistId | TrackId |
|--- |--- |
|          1 |    3402 |
|          1 |    3389 |
|          1 |    3390 |
|          1 |    3391 |
|          1 |    3392 |
|          1 |    3393 |
|          1 |    3394 |
|          1 |    3395 |
|          1 |    3396 |
|          1 |    3397 |

**9. Run Query: Select all the columns from the Media Types table and limit the results to 50 records. What happened when you ran this query? Were you able to get all 50 records?**

SQL code:</br>
```SQL
Select *
From Playlist_track 
Limit 10;
```
Result:</br>
| PlaylistId | TrackId |
|--- |--- |
|          1 |    3402 |
|          1 |    3389 |
|          1 |    3390 |
|          1 |    3391 |
|          1 |    3392 |
|          1 |    3393 |
|          1 |    3394 |
|          1 |    3395 |
|          1 |    3396 |
|          1 |    3397 |

**10. Run Query: Select all the columns from the Albums table and limit the results to 5 records. How many columns are in the albums table? What is the name of the 9th album in this list?**

SQL code:</br>

```SQL
SELECT *
FROM Albums
--Where AlbumId = 9
LIMIT 5;
```
Result:</br>

| AlbumId | Title                                 | ArtistId |
|--- |--- |--- |
|       1 | For Those About To Rock We Salute You |        1 |
|       2 | Balls to the Wall                     |        2 |
|       3 | Restless and Wild                     |        2 |
|       4 | Let There Be Rock                     |        1 |
|       5 | Big Ones                              |        3 |
|       6 | Jagged Little Pill                    |        4 |
|       7 | Facelift                              |        5 |
|       8 | Warner 25 Anos                        |        6 |
|       9 | Plays Metallica By Four Cellos        |        7 |

*left to [Rubricator](../README.md)*