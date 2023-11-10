Query the two cities in STATION with the shortest and longest CITY names, as well as their respective lengths (i.e.: number of characters in the name). If there is more than one smallest or largest city, choose the one that comes first when ordered alphabetically.
The STATION table is described as follows:
![structure of table](https://s3.amazonaws.com/hr-challenge-images/9336/1449345840-5f0a551030-Station.jpg)


Sample Input

For example, CITY has four entries: DEF, ABC, PQRS and WXY.

Sample Output

ABC 3
PQRS 4

----
My answer :

```SQL
(SELECT CITY, Length(CITY)
FROM STATION
ORDER BY LENGTH(CITY), CITY ASC 
LIMIT 1)

UNION ALL

(SELECT CITY, Length(CITY)
FROM STATION
ORDER BY LENGTH(CITY) DESC, CITY DESC
LIMIT 1)
```

OR 

```SQL
SELECT City, LENGTH(City) AS CityLength
FROM STATION
ORDER BY CityLength ASC, City
LIMIT 1;

SELECT City, LENGTH(City) AS CityLength
FROM STATION
ORDER BY CityLength DESC, City
LIMIT 1;
```