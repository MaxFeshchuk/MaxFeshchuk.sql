# Final work 

*left to [Rubricator](../README.md)*

Chapters:
[Data Scientist Role Play: Profiling and Analyzing the Yelp Dataset](Final_work.md#data-scientist-role-play-profiling-and-analyzing-the-yelp-dataset)
- [Part 1: Yelp Dataset Profiling and Understanding](Final_work.md#part-1-yelp-dataset-profiling-and-understanding)
- [Part 2: Inferences and Analysis](Final_work.md#part-2-inferences-and-analysis)

## Data Scientist Role Play: Profiling and Analyzing the Yelp Dataset

This is a 2-part assignment. In the first part, you are asked a series of questions 
that will help you profile and understand the data just like a data scientist would. 
For this first part of the assignment, you will be assessed both on the correctness 
of your findings, as well as the code you used to arrive at your answer. You will 
be graded on how easy your code is to read, so remember to use proper formatting 
and comments where necessary.

In the second part of the assignment, you are asked to come up with your own 
inferences and analysis of the data for a particular research question you want to 
answer. You will be required to prepare the dataset for the analysis you choose to 
do. As with the first part, you will be graded, in part, on how easy your code is 
to read, so use proper formatting and comments to illustrate and communicate your 
intent as required.

For both parts of this assignment, use this "worksheet." It provides all the 
questions you are being asked, and your job will be to transfer your answers and 
SQL coding where indicated into this worksheet so that your peers can review your 
work. You should be able to use any Text Editor (Windows Notepad, Apple TextEdit, 
Notepad ++, Sublime Text, etc.) to copy and paste your answers. If you are going 
to use Word or some other page layout application, just be careful to make sure 
your answers and code are lined appropriately.
In this case, you may want to save as a PDF to ensure your formatting remains 
intact for you reviewer.

## Part 1: Yelp Dataset Profiling and Understanding

**1. Profile the data by finding the total number of records for each of the tables 
below:**

	1. Attribute table = 10000;
	2. Business table = 10000;
	3. Category table = 10000;
	4. Checkin table = 10000;
	5. elite_years table = 10000;
	6. friend table = 10000;
	7. hours table = 10000;
	8. photo table = 10000;
	9. review table = 10000;
	10. tip table = 10000;
	11. user table = 10000.

SQL code:</br> 
```SQL
SELECT COUNT(*) AS Total_Number
FROM [Name of table];
```

**2. Find the total distinct records by either the foreign key or primary key for 
each table. If two foreign keys are listed in the table, please specify which 
foreign key.**

	1. Business = id: 10000;
	2. Hours = business_id: 1562;
	3. Category = business_id: 2643;
	4. Attribute = business_id: 1115;
	5. Review = id: 10000, business_id: 8090, user_id: 9581;
	6. Checkin = business_id: 493;
	7. Photo = id: 10000, business_id: 6493;
	8. Tip = user_id: 537, business_id: 3979;
	9. User = id: 10000;
	10. Friend = user_id: 11;
	11. Elite_years = user_id: 2780.

Note: Primary Keys are denoted in the ER-Diagram with a yellow key icon.

SQL code:</br> 
```SQL
SELECT COUNT(DISTINCT [Name of Key]) AS Total_Dis_Records
FROM [Name of table];
```

**3. Are there any columns with null values in the Users table? Indicate "yes," 
or "no."**

Answer: no

SQL code:</br> 
```SQL
SELECT *
FROM User
WHERE id is NULL
	OR name is NULL
	OR review_count is NULL
	OR yelping_since is NULL 
	OR useful is NULL
	OR funny is NULL
	OR cool is NULL
	OR fans is NULL
	OR average_stars is NULL
	OR compliment_hot is NULL
	OR compliment_more is NULL
	OR compliment_profile is NULL
	OR compliment_cute is NULL
	OR compliment_list is NULL
	OR compliment_note is NULL
	OR compliment_plain is NULL
	OR compliment_cool is NULL
	OR compliment_funny is NULL
	OR compliment_writer is NULL
	OR compliment_photos is NULL;
```

**4. For each table and column listed below, display the smallest (minimum), 
largest (maximum), and average (mean) value for the following fields:**

1. Table: Review, Column: Stars

| min | max | avg    |
|---  |---  |---     |
| 1   | 5   | 3.7082 | 
	
2. Table: Business, Column: Stars

| min | max | avg    |
|---  |---  |---     |
| 1.0   | 5.0   | 3.6549 | 

3. Table: Tip, Column: Likes

| min | max | avg    |
|---  |---  |---     |
| 0   | 2  | 0.0144 | 	
	
4. Table: Checkin, Column: Count

| min | max | avg    |
|---  |---  |---     |
| 1   | 53  | 1.9414 |	
	
5. Table: User, Column: Review_count

| min | max | avg    |
|---  |---  |---     |
| 0   | 2000  | 24.2995 |	

SQL code:</br> 
```SQL
SELECT MIN([Name of column]) AS Smallest_Value
,MAX([Name of column]) AS Largest_Value 
,AVG([Name of column]) AS Mean_Value
FROM [Name Of Table];
```

**5. List the cities with the most reviews in descending order:**

SQL code:</br> 
```SQL
SELECT city
,SUM(review_count) AS Count_Review
FROM business
GROUP BY city
ORDER BY Count_Review DESC;
```

Result:</br>
| city            | Count_Review |
|---              |---           |
| Las Vegas       |        82854 |
| Phoenix         |        34503 |
| Toronto         |        24113 |
| Scottsdale      |        20614 |
| Charlotte       |        12523 |
| Henderson       |        10871 |
| Tempe           |        10504 |
| Pittsburgh      |         9798 |
| Montréal        |         9448 |
| Chandler        |         8112 |
| Mesa            |         6875 |
| Gilbert         |         6380 |
| Cleveland       |         5593 |
| Madison         |         5265 |
| Glendale        |         4406 |
| Mississauga     |         3814 |
| Edinburgh       |         2792 |
| Peoria          |         2624 |
| North Las Vegas |         2438 |
| Markham         |         2352 |
| Champaign       |         2029 |
| Stuttgart       |         1849 |
| Surprise        |         1520 |
| Lakewood        |         1465 |
| Goodyear        |         1155 |

(Output limit exceeded, 25 of 362 total rows shown)

**6. Find the distribution of star ratings to the business in the following 
cities**

1. Avon

SQL code:</br> 
```SQL
SELECT Stars AS Star_Ruting
,SUM(review_count) AS Count 
FROM business
WHERE city = 'Avon'
GROUP BY stars;
```

Copy and Paste the Resulting Table Below (2 columns – star rating and count):
| Star_Ruting | Count |
|---          |---    |
|         1.5 |    10 |
|         2.5 |     6 |
|         3.5 |    88 |
|         4.0 |    21 |
|         4.5 |    31 |
|         5.0 |     3 |

2. Beachwood

SQL code:</br> 
```SQL
SELECT Stars AS Star_Ruting
,SUM(review_count) AS Count 
FROM business
WHERE city = 'Beachwood'
GROUP BY stars;
```

Copy and Paste the Resulting Table Below (2 columns – star rating and count):
| Star_Ruting | Count |
|---          |---    |
|         2.0 |     8 |
|         2.5 |     3 |
|         3.0 |    11 |
|         3.5 |     6 |
|         4.0 |    69 |
|         4.5 |    17 |
|         5.0 |    23 |

**7. Find the top 3 users based on their total number of reviews:**

SQL code:</br> 
```SQL
SELECT name
,review_count
FROM user
ORDER BY review_count DESC
LIMIT 3;
```

Copy and Paste the Result Below:
| name   | review_count |
|---     |       ---    |
| Gerald |         2000 |
| Sara   |         1629 |
| Yuri   |         1339 |

**8. Does posing more reviews correlate with more fans?**

Please explain your findings and interpretation of the results:
	
Not always. For example, consider Amy at the top of the list, which has 503 
fans and 609 reviews, while Mimi (second on the list) has more reviews (968),
but fewer fans. And this trend is also observed in some people below the 
list. Therefore, more criteria are needed to determine the dependence.

SQL code:</br> 
```SQL
SELECT name
,review_count
,fans
FROM user
ORDER BY fans Desc;
```

Result:
| name      | review_count | fans |
|---        |       ---    |---   |
| Amy       |          609 |  503 |
| Mimi      |          968 |  497 |
| Harald    |         1153 |  311 |
| Gerald    |         2000 |  253 |
| Christine |          930 |  173 |
| Lisa      |          813 |  159 |
| Cat       |          377 |  133 |
| William   |         1215 |  126 |
| Fran      |          862 |  124 |
| Lissa     |          834 |  120 |
| Mark      |          861 |  115 |
| Tiffany   |          408 |  111 |
| bernice   |          255 |  105 |
| Roanna    |         1039 |  104 |
| Angela    |          694 |  101 |
| .Hon      |         1246 |  101 |
| Ben       |          307 |   96 |
| Linda     |          584 |   89 |
| Christina |          842 |   85 |
| Jessica   |          220 |   84 |
| Greg      |          408 |   81 |
| Nieves    |          178 |   80 |
| Sui       |          754 |   78 |
| Yuri      |         1339 |   76 |
| Nicole    |          161 |   73 |

(Output limit exceeded, 25 of 10000 total rows shown)

**9. Are there more reviews with the word "love" or with the word "hate" in 
them?**

Answer:

There are 1726 reviews with “love” and 178 reviews with “hate” and 54 that 
contains both “love” and “hate”</br>
As result:</br>
Love: 1726 + 54 = 1780 reviews</br>
Hate: 178 + 54 = 232 reviews

SQL code:</br> 
```SQL
SELECT 
CASE
	WHEN LOWER(text) LIKE '%hate%love%' THEN 'Love and hate'
	WHEN LOWER(text) LIKE '%love%hate%' THEN 'Love and hate'
	WHEN LOWER(text) LIKE '%hate%' THEN 'Hate'
	WHEN LOWER(text) LIKE '%love%' THEN 'Love'
	ELSE 'No such words'
END Text_Contains,
COUNT(*) AS Count_Reviews
FROM review
GROUP BY Text_Contains
ORDER BY Count_Reviews DESC;
```

Result:
| Text_Contains | Count_Reviews |
|---            |       ---     |
| No such words |          8042 |
| Love          |          1726 |
| Hate          |           178 |
| Love and hate |            54 |

**10. Find the top 10 users with the most fans:**

SQL code:</br> 
```SQL
SELECT name AS User
,fans
FROM user
ORDER BY fans DESC
LIMIT 10;
```

Copy and Paste the Result Below:
| User      | fans |
|---        | ---  |
| Amy       |  503 |
| Mimi      |  497 |
| Harald    |  311 |
| Gerald    |  253 |
| Christine |  173 |
| Lisa      |  159 |
| Cat       |  133 |
| William   |  126 |
| Fran      |  124 |
| Lissa     |  120 |

## Part 2: Inferences and Analysis

*left to [Rubricator](../README.md)*

**1. Pick one city and category of your choice and group the businesses in 
that city or category by their overall star rating. Compare the businesses 
with 2-3 stars to the businesses with 4-5 stars and answer the following 
questions. Include your code.**
	
**Do the two groups you chose to analyze have a different distribution of 
hours?**

I picked Toronto and Restaurants for this question. 
Yes, two groups have a different distribution of hours. 
The restaurant with 2.0 stars open from 11:00-23:00 on Saturday. 
The restaurant with 3.0 rating stars open earlier than restaurant with 2.0 
on 10:00 - 4:00 on Saturday.
The restaurant with 4.0 rating stars open late than restorant with 2 stars 
on 18:00 - 23:00 on Saturday.
The restaurant with 4.5 stars opens just like restaurant with 2.0 stars.

SQL code:</br> 
```SQL
SELECT b.name AS Business
,b.city
,c.category
,b.stars
,h.hours
FROM business b INNER JOIN category c
ON b.id=c.business_id INNER JOIN hours h
	ON b.id=h.business_id
WHERE b.city = 'Toronto' AND c.category = 'Restaurants'
GROUP BY b.stars;
```

Result:
| Business      | city    | category    | stars | hours                |
|---            | ---     | ---         | ---   | ---                  |
| 99 Cent Sushi | Toronto | Restaurants |   2.0 | Saturday|11:00-23:00 |
| Pizzaiolo     | Toronto | Restaurants |   3.0 | Saturday|10:00-4:00  |
| Edulis        | Toronto | Restaurants |   4.0 | Saturday|18:00-23:00 |
| Sushi Osaka   | Toronto | Restaurants |   4.5 | Saturday|11:00-23:00 |

**Do the two groups you chose to analyze have a different number of 
reviews?**

Yes. The group with 2-3 stars has less review (In sum: 39) compared with
the group with higher rating stars(In sum: 97).
But the restaurant with 4.5 stars have far fewer reviews than the restaurant 
with 3 stars.
May be Osaka sushi be recently opened or located in a sparsely populated 
area.

SQL code:</br> 
```SQL
SELECT b.name AS Business
,b.city
,c.category
,b.stars
,h.hours
FROM business b INNER JOIN category c
ON b.id=c.business_id INNER JOIN hours h
	ON b.id=h.business_id
WHERE b.city = 'Toronto' AND c.category = 'Restaurants'
GROUP BY b.stars;
```

Result:

| Review | Business      | city    | category    | stars | hours                |
|---     | ---           | ---     | ---         | ---   |---                   |
|     89 | Edulis        | Toronto | Restaurants |   4.0 | Saturday|18:00-23:00 |
|     34 | Pizzaiolo     | Toronto | Restaurants |   3.0 | Saturday|10:00-4:00  |
|      8 | Sushi Osaka   | Toronto | Restaurants |   4.5 | Saturday|11:00-23:00 |
|      5 | 99 Cent Sushi | Toronto | Restaurants |   2.0 | Saturday|11:00-23:00 |
         
**Are you able to infer anything from the location data provided between these 
two groups? Explain.**

The restaurant with 4.0 (Edulis) is located in the busiest place called 
'Entertainment District'.
Therefore it is possible and has the most reviews as other restaurants
(with 5-34 reviews) are located more remotely.

SQL code:</br> 
```SQL
SELECT b.review_count AS Review
,b.name AS Business
,b.city
,c.category
,b.stars
,h.hours
,b.address
FROM business b INNER JOIN category c
ON b.id=c.business_id INNER JOIN hours h
	ON b.id=h.business_id
WHERE b.city = 'Toronto' AND c.category = 'Restaurants'
GROUP BY b.stars
ORDER BY b.review_count DESC;
```

Result:
| Review | Business      | city    | category    | stars | hours                | address               |
|---     | ---           | ---     | ---         | ---   |---                   |---                    |
|     89 | Edulis        | Toronto | Restaurants |   4.0 | Saturday|18:00-23:00 | 169 Niagara Street    |
|     34 | Pizzaiolo     | Toronto | Restaurants |   3.0 | Saturday|10:00-4:00  | 270 Adelaide Street W |
|      8 | Sushi Osaka   | Toronto | Restaurants |   4.5 | Saturday|11:00-23:00 | 5084 Dundas Street W  |
|      5 | 99 Cent Sushi | Toronto | Restaurants |   2.0 | Saturday|11:00-23:00 | 389 Church Street     |
		
**2. Group business based on the ones that are open and the ones that are closed. 
What differences can you find between the ones that are still open and the ones 
that are closed? List at least two differences and the SQL code you used to 
arrive at your answer.**
		
**Difference 1:**

The ones that are still open have more reviews on average than ones that are 
closed.         
         
**Difference 2:**
         
There are more business that are still open listed as 'useful' or 'funny'.
          
SQL code:</br> 
```SQL
SELECT
CASE is_open
	WHEN 0 THEN 'Closed'
	WHEN 1 THEN 'Open'
ELSE 'Smt else'
End Status
,AVG(b.stars) AS AVG_Stars
,SUM(b.review_count) AS Reviews
,AVG(b.review_count) AS AVG_Reviews
,COUNT(r.useful)+COUNT(r.funny) AS useful_funny
FROM business b INNER JOIN review r 
ON b.id = r.id
GROUP BY Status;
```

Result:
| Status |     AVG_Stars | Reviews |   AVG_Reviews | useful_funny |
|---     | ---           | ---     | ---           | ---          |
| Closed |           2.0 |       4 |           4.0 |            2 |
| Open   | 2.96153846154 |     504 | 38.7692307692 |           26 |
	
**3. For this last part of your analysis, you are going to choose the type of 
analysis you want to conduct on the Yelp dataset and are going to prepare 
the data for analysis.**

Ideas for analysis include: Parsing out keywords and business attributes 
for sentiment analysis, clustering businesses to find commonalities or 
anomalies between them, predicting the overall star rating for a business,
predicting the number of fans a user will have, and so on. These are just 
a few examples to get you started, so feel free to be creative and come up 
with your own problem you want to solve. Provide answers, in-line, to all 
of the following:
	
**Indicate the type of analysis you chose to do:**

Decided to analyze the categories of business to understand the side of 
the century moving market         
         
**Write 1-2 brief paragraphs on the type of data you will need for your 
analysis and why you chose that data:**

I will pick several types of business including 'Banks & Credit Unions', 
'Shopping', 'Plumbing', 'Automotive', and 'Apartments'. Then I will analyze 
their star ratings and number of reviews so that I can get some insights on 
which type of business is popular on yelp and in which city. 
                           
                  
**Output of your finished dataset:**
| category              | city       | AVG_Stars | AVG_Review | Count_category |
|---                    | ---        | ---       | ---        | ---            |
| Shopping              | Scottsdale | 3.9       | 32.56      |             30 |
| Automotive            | Charlotte  | 4.5       | 22.0       |              9 |
| Apartments            | Phoenix    | 3.5       | 5.0        |              4 |
| Banks & Credit Unions | Toronto    | 1.5       | 3.0        |              1 |
| Plumbing              | Henderson  | 5.0       | 5.0        |              1 |
       
         
**Provide the SQL code you used to create your final dataset:**

SQL code:</br> 
```SQL
SELECT category
,b.city
,SUBSTR(AVG(b.stars),1,3) AS AVG_Stars
,SUBSTR(AVG(b.review_count),1,5) AS AVG_Review
,COUNT(*) AS Count_category 
FROM category c INNER JOIN business b
ON c.business_id=b.id
WHERE category IN ('Banks & Credit Unions','Shopping','Plumbing','Automotive','Apartments')
GROUP BY category
ORDER BY Count_category DESC;
```

*left to [Rubricator](../README.md)*