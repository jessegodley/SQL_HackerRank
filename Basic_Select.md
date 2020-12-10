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
