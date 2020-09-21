# Week 3
- [Practice Quiz](#practice-quiz)

*left to [Rubricator](../README.md)*

## Practice Quiz

**All of the questions in this quiz pull from the open source Chinook Database. Please refer to the ER Diagram below and familiarize yourself with the table and column names to write accurate queries and get the appropriate answers.**

**1. How many albums does the artist Led Zeppelin have?**

SQL code:</br> 
```SQL
SELECT COUNT(*) AS Count_albums
FROM (SELECT ar.name
		,al.title
      FROM artists ar LEFT JOIN al
      ON ar.artistid = al.artistid)
WHERE Name = 'Led Zeppelin'
```

Result:</br> 
| Extended_Step |
|--- |
| 0             |
| 11            |
| 6             |
| 2             |