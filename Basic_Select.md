The CITY table is described as follows: (This table will be used for all problems until a new table is declared)

|  Field | Type |
|---|-----|
|-------|-----|
| ID  | NUMBER |
| NAME | VARCHAR2(17)   |
| COUNTRYCODE  | VARCHAR2(3)  |
| DISTRICT |  VARCHAR2(20) |
| POPULATION | NUMBER |

###**[Revising the Select Query-1](https://www.hackerrank.com/challenges/revising-the-select-query)**

Query all columns for all American cities in CITY with populations larger than 100,000. The CountryCode for America is USA.
Input Format

**Solution**
```sql
SELECT * FROM City
WHERE CountryCode = 'USA'
AND Population > 100000;
```

###**[Revising the Select Query-2](https://www.hackerrank.com/challenges/revising-the-select-query-2)**

Query the names of all American cities in CITY with populations larger than 120,000. The CountryCode for America is USA.

**Solution**
```sql
SELECT Name FROM City
WHERE CountryCode = 'USA'
AND Population > 120000;
```

###**[Select All](https://www.hackerrank.com/challenges/select-all-sql)**

Query all columns for every row in the CITY table.

**Solution**
```sql
SELECT * FROM City;
```

###**[Select by ID](https://www.hackerrank.com/challenges/select-by-id)**

Query all columns for a city in CITY with the ID 1661.

**Solution**
```sql
SELECT * FROM City
WHERE ID = 1661;
```

###**[Japanese Cities' Detail](https://www.hackerrank.com/challenges/japanese-cities-detail)**

Query the details for all the Japanese cities in CITY. The COUNTRYCODE for Japan is JPN.

**Solution**
```sql
SELECT * FROM City
WHERE CountryCode = 'JPN';
```

###**[Japanese Cities' Name](https://www.hackerrank.com/challenges/japanese-cities-name)**

Query the the names of all the Japanese cities in CITY. The COUNTRYCODE for Japan is JPN.

**Solution**
```sql
SELECT Name FROM City
WHERE CountryCode = 'JPN';
```

**NEW TABLE: STATION**

The STATION table is described as follows: (This table will be used for all problems until a new table is declared)

|  Field | Type |
|---|---|
| ID  | NUMBER |
| CITY | VARCHAR2(21)   |
| STATE  | VARCHAR2(2)  |
| LAT_N |  NUMBER |
| LONG_W | NUMBER |

###**[Weather Observation Station 1](https://www.hackerrank.com/challenges/weather-observation-station-1)**

Query a list of CITY and STATE from STATION.

**Solution**
```sql
SELECT City, State FROM Station;
```

###**[Weather Observation Station 3](https://www.hackerrank.com/challenges/weather-observation-station-3)**

Query a list of CITY names from STATION with even ID numbers only. You may print the results in any order, but must exclude duplicates from your answer.

**Solution**
```sql
SELECT DISTINCT City FROM Station
WHERE MOD(id,2)=0;
```

###**[Weather Observation Station 4](https://www.hackerrank.com/challenges/weather-observation-station-4)**

Let NUM be the number of CITY entries in STATION, and NUMunique be the number of unique cities. Query the value of NUM−NUMunique from STATION.

In other words, query the number of non-unique CITY names in STATION by subtracting the number of unique CITY entries in the table from the total number of CITY entries in the table.

**Solution**
```sql
SELECT COUNT(City) - COUNT(DISTINCT City) FROM Station;
```

###**[Weather Observation Station 5](https://www.hackerrank.com/challenges/weather-observation-station-5)**

Query the two cities in STATION with the shortest and longest CITY names, as well as their respective lengths (i.e.: number of characters in the name). If there is more than one smallest or largest city, choose the one that comes first when ordered alphabetically.

**Solution**
```sql
SELECT City, LENGTH(City) FROM Station
ORDER BY LENGTH(City) ASC, City ASC LIMIT 1;

SELECT City, LENGTH(City) FROM Station
ORDER BY LENGTH(City) DESC, City ASC LIMIT 1;
```

###**[Weather Observation Station 6](https://www.hackerrank.com/challenges/weather-observation-station-6)**

Query the list of CITY names starting with vowels (a, e, i, o, u) from STATION. Your result cannot contain duplicates.

**Solution**
```sql
SELECT DISTINCT City FROM Station
WHERE City RLIKE '^[aeiou]';
```

###**[Weather Observation Station 7](https://www.hackerrank.com/challenges/weather-observation-station-7)**

Query the list of CITY names ending with vowels (a, e, i, o, u) from STATION. Your result cannot contain duplicates.

**Solution**
```sql
SELECT DISTINCT City FROM Station
WHERE City RLIKE '[aeiou]$';
```

###**[Weather Observation Station 8](https://www.hackerrank.com/challenges/weather-observation-station-8/problem)**

Query the list of CITY names from STATION which have vowels (i.e., a, e, i, o, and u) as both their first and last characters. Your result cannot contain duplicates.

**Solution**
```sql
SELECT DISTINCT City FROM Station
WHERE City RLIKE '^[aeiou].*[aeiou]$';
```

###**[Weather Observation Station 9](https://www.hackerrank.com/challenges/weather-observation-station-9/problem)**

Query the list of CITY names from STATION that do not start with vowels. Your result cannot contain duplicates.

**Solution**
```sql
SELECT DISTINCT City FROM Station
WHERE City NOT RLIKE '^[aeiou]';
```

###**[Weather Observation Station 10](https://www.hackerrank.com/challenges/weather-observation-station-10/problem)**

Query the list of CITY names from STATION that do not end with vowels. Your result cannot contain duplicates.

**Solution**
```sql
SELECT DISTINCT City FROM Station
WHERE City NOT RLIKE '[aeiou]$';
```

###**[Weather Observation Station 11](https://www.hackerrank.com/challenges/weather-observation-station-11/problem)**

Query the list of CITY names from STATION that either do not start with vowels or do not end with vowels. Your result cannot contain duplicates.

**Solution**
```sql
SELECT DISTINCT City FROM Station
WHERE City NOT RLIKE '^[aeiou].*[aeiou]$';
```

###**[Weather Observation Station 12](https://www.hackerrank.com/challenges/weather-observation-station-12/problem)**

Query the list of CITY names from STATION that do not start with vowels and do not end with vowels. Your result cannot contain duplicates.

**Solution**
```sql
SELECT DISTINCT City FROM Station
WHERE City NOT RLIKE '^[aeiou]' AND City NOT RLIKE '[aeiou]$';
```

**NEW TABLE: STUDENTS**

The STUDENTS table is described as follows: (This table will be used for all problems until a new table is declared)

|  Column | Type |
|---|---|
| ID  | INTEGER |
| NAME | STRING   |
| MARKS  | INTEGER  |

###**[Higher Than 75 marks](https://www.hackerrank.com/challenges/more-than-75-marks/problem)**

Query the Name of any student in STUDENTS who scored higher than 75 Marks. Order your output by the last three characters of each name. If two or more students both have names ending in the same last three characters (i.e.: Bobby, Robby, etc.), secondary sort them by ascending ID.

**Solution**
```sql
SELECT Name FROM Students
WHERE Marks > 75
ORDER BY RIGHT(Name, 3), ID;
```

**NEW TABLE: EMPLOYEE**

The EMPLOYEE table is described as follows: (This table will be used for all problems until a new table is declared)
