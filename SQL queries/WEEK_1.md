# Practice Simple Select Queries

To prepare for the graded coding quiz, you will be asked to execute a query, read the results, and select the correct answer you found in the results. This question is for you to practice executing queries. I have provided you the script for this query, a simple select statement. Think of this as a sandbox for you to practice. As you practice executing queries, take time to read the results in order to prepare for the quiz and get comfortable writing a basic select statement.

1. Run query: Retrieve all the data from the tracks table. Who is the composer for track 18?

--------SQL code--------
Select TrackId, Composer 
From Tracks
Where trackid = 18;
------------------------
---------Result---------
+---------+----------+
| TrackId | Composer |
+---------+----------+
|      18 | AC/DC    |
+---------+----------+
------------------------

2. Run Query: Retrieve all data from the artists table. Look at the list of artists, how many artists are you familiar with (there is no wrong answer here)?

----------SQL code---------
Select *
From Artists
Where ArtistId IN (1, 22);
---------------------------
-----------Result----------
+----------+--------------+
| ArtistId | Name         |
+----------+--------------+
|        1 | AC/DC        |
|       22 | Led Zeppelin |
+----------+--------------+
---------------------------

3. Run Query: Retrieve all data from the invoices table. What is the billing address for customer 31?

----------------SQL code--------------
Select CustomerId, BillingAddress
From Invoices
Where CustomerId = 31
Limit 1;
--------------------------------------
-----------------Result---------------
+------------+-----------------------+
| CustomerId | BillingAddress        |
+------------+-----------------------+
|         31 | 194A Chain Lake Drive |
+------------+-----------------------+
--------------------------------------

4. Run Query: Return the playlist id, and name from the playlists table. How many playlists are there?

----------------SQL code--------------
Select Count(*) AS Count_playlists
From Playlists
--------------------------------------
-----------------Result---------------
+-----------------+
| Count_playlists |
+-----------------+
|              18 |
+-----------------+
--------------------------------------