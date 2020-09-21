# Week 1 (Practice Simple Select Queries)
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
Select *
From Artists
Where Name IN ("AC/DC", "Led Zeppelin");
```

Result:</br>
| ArtistId | Name         |
|--- | --- |
|        1 | AC/DC        |
|       22 | Led Zeppelin |

**3. Run Query: Retrieve all data from the invoices table. What is the billing address for customer 31?**

SQL code:</br> 
```SQL
Select CustomerId
,BillingAddress
From Invoices
Where CustomerId == 31
GROUP BY BillingAddress;
```

Result:</br>
| CustomerId | BillingAddress        |
|--- | --- |
|         31 | 194A Chain Lake Drive |

**4. Run Query: Return the playlist id, and name from the playlists table. How many playlists are there?**

SQL code:</br>
```SQL
Select MAX(PlaylistId) AS Count_playlists
From Playlists;
```

Result:</br>
| Count_playlists |
|--- |
|              18 |

**Which would you classify is your favorite from this list?**

SQL code:</br>
```SQL
Select *
From Playlists
GROUP BY Name;
```

| PlaylistId | Name                       |
|--- |--- |
|          5 | 90’s Music                 |
|          6 | Audiobooks                 |
|         11 | Brazilian Music            |
|         12 | Classical                  |
|         13 | Classical 101 - Deep Cuts  |
|         14 | Classical 101 - Next Steps |
|         15 | Classical 101 - The Basics |
|         16 | Grunge                     |
|         17 | Heavy Metal Classic        |
|          7 | Movies                     |
|          8 | Music                      |
|          9 | Music Videos               |
|         18 | On-The-Go 1                |
|         10 | TV Shows                   |


**5. Run Query: Return the Customer Id, Invoice Date, and Billing City from the Invoices table. What city is associated with Customer ID number 42? What was the invoice date for the customer in Santiago?**

SQL code:</br>
```SQL
SELECT CustomerId
,InvoiceDate
,BillingCity 
FROM Invoices
Where CustomerId = 42 or BillingCity LIKE 'Santiago'
GROUP BY BillingCity;
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
Select TrackId
,GenreId
,UnitPrice
From Tracks;
```

Result:</br>
| TrackId | GenreId | UnitPrice |
|--- |--- |--- |
|       1 |       1 |      0.99 |
|       2 |       1 |      0.99 |
|       3 |       1 |      0.99 |
|       4 |       1 |      0.99 |
|       5 |       1 |      0.99 |
|       6 |       1 |      0.99 |
|       7 |       1 |      0.99 |
|       8 |       1 |      0.99 |
|       9 |       1 |      0.99 |
|      10 |       1 |      0.99 |
|      11 |       1 |      0.99 |
|      12 |       1 |      0.99 |
|      13 |       1 |      0.99 |
|      14 |       1 |      0.99 |
|      15 |       1 |      0.99 |
|      16 |       1 |      0.99 |
|      17 |       1 |      0.99 |
|      18 |       1 |      0.99 |
|      19 |       1 |      0.99 |
|      20 |       1 |      0.99 |
|      21 |       1 |      0.99 |
|      22 |       1 |      0.99 |
|      23 |       1 |      0.99 |
|      24 |       1 |      0.99 |
|      25 |       1 |      0.99 |
+---------+---------+-----------+
(Output limit exceeded, 25 of 3503 total rows shown)

**8. Run Query: Select all the columns from the Playlist Track table and limit the results to 10 records. How might this information be used?**

SQL code:</br>
```SQL
Select PlaylistId
,Count(TrackId) AS Contain_tracks 
From Playlist_track 
GROUP BY PlaylistId
ORDER BY PlaylistId ASC
Limit 10;
```

Result:</br>

| PlaylistId | Contain_tracks |
|--- |--- |
|          1 |           3290 |
|          3 |            213 |
|          5 |           1477 |
|          8 |           3290 |
|          9 |              1 |
|         10 |            213 |
|         11 |             39 |
|         12 |             75 |
|         13 |             25 |
|         14 |             25 |

We can determine how many tracks the playlist has

**9. Run Query: Select all the columns from the Media Types table and limit the results to 50 records. What happened when you ran this query? Were you able to get all 50 records?**

SQL code:</br>
```SQL
Select *
From Media_types
Limit 50;
```
Result:</br>
| MediaTypeId | Name                        |
|--- |--- |
|           1 | MPEG audio file             |
|           2 | Protected AAC audio file    |
|           3 | Protected MPEG-4 video file |
|           4 | Purchased AAC audio file    |
|           5 | AAC audio file              |

No couln't, because the table contains less than 50 rows

**10. Run Query: Select all the columns from the Albums table and limit the results to 5 records. How many columns are in the albums table? What is the name of the 9th album in this list?**

SQL code:</br>
```SQL
Select *
From Albums
Where AlbumId = 9;
```

Result:</br>

| AlbumId | Title                          | ArtistId |
|--- |--- |--- |
|       9 | Plays Metallica By Four Cellos |        7 |


*left to [Rubricator](../README.md)*