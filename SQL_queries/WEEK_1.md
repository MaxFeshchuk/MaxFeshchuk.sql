# Practice Simple Select Queries
*left to [Rubricator](../README.md)*

To prepare for the graded coding quiz, you will be asked to execute a query, read the results, and select the correct answer you found in the results. This question is for you to practice executing queries. I have provided you the script for this query, a simple select statement. Think of this as a sandbox for you to practice. As you practice executing queries, take time to read the results in order to prepare for the quiz and get comfortable writing a basic select statement.

1. Run query: Retrieve all the data from the tracks table. Who is the composer for track 18?

SQL code:</br> 
```SQL
Select TrackId, Composer 
From Tracks
Where trackid = 18;
```

Result:</br> 

|TrackId|Composer|
|18|AC/DC|

Markdown | не такой | красивый
--- | --- | ---
*Но выводится* | `так же` | **клево**
1 | 2 | 3

2. Run Query: Retrieve all data from the artists table. Look at the list of artists, how many artists are you familiar with (there is no wrong answer here)?

SQL code:</br> 
```SQL
Select *
From Artists
Where ArtistId IN (1, 22);
```

Result:</br>
| ArtistId | Name         |
|        1 | AC/DC        |
|       22 | Led Zeppelin |

3. Run Query: Retrieve all data from the invoices table. What is the billing address for customer 31?

SQL code:</br> 
```SQL
Select CustomerId, BillingAddress
From Invoices
Where CustomerId = 31
Limit 1;
```

Result:</br>

| CustomerId | BillingAddress        |
|         31 | 194A Chain Lake Drive |

4. Run Query: Return the playlist id, and name from the playlists table. How many playlists are there?

SQL code:</br> 
```SQL
Select Count(*) AS Count_playlists
From Playlists
```
Result:</br>
| Count_playlists |
|              18 |