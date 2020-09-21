# Week 3
- [Practice Quiz](#practice-quiz)

*left to [Rubricator](../README.md)*

## Practice Quiz

**All of the questions in this quiz pull from the open source Chinook Database. Please refer to the ER Diagram below and familiarize yourself with the table and column names to write accurate queries and get the appropriate answers.**

![Database](SQL_queries/images/Chinook_Database.png)

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
| Count_albums |
|--- |
|           14 |

**2. Create a list of album titles and the unit prices for the artist "Audioslave".**

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
| Count_albums |
|--- |
|           14 |
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
| Count_albums |
|--- |
|           14 |
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
| Count_albums |
|--- |
|           14 |

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
| Count_albums |
|--- |
|           14 |

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
| Count_albums |
|--- |
|           14 |

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
| Count_albums |
|--- |
|           14 |

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
| Count_albums |
|--- |
|           14 |

