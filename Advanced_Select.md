**NEW TABLE: TRIANGLES**

The TRIANGLES table is described as follows: (This table will be used for all problems until a new table is declared)

|  Column | Type |
|---|---|
| A | INTEGER |
| B | INTEGER |
| C | INTEGER | 

###**[Type of Triangle](https://www.hackerrank.com/challenges/what-type-of-triangle)**

Write a query identifying the type of each record in the TRIANGLES table using its three side lengths. Output one of the following statements for each record in the table:

Equilateral: It's a triangle with  sides of equal length.
Isosceles: It's a triangle with  sides of equal length.
Scalene: It's a triangle with  sides of differing lengths.
Not A Triangle: The given values of A, B, and C don't form a triangle.

**Soultion**
```sql
SELECT
  CASE
    WHEN A + B <= C or A + C <= B or B + C <= A THEN 'Not A Triangle'
    WHEN A = B and B = C THEN 'Equilateral'
    WHEN A = B or A = C or B = C THEN 'Isosceles'
    ELSE 'Scalene'
  END tuple
FROM TRIANGLES;
```

**NEW TABLE: OCCUPATIONS**

The OCCUPATIONS table is described as follows: (This table will be used for all problems until a new table is declared)

|  Column | Type |
|---|---|
| Name | STRING |
| Occupation | STRING | 

###**[The PADS](https://www.hackerrank.com/challenges/the-pads)**

Generate the following two result sets:

1. Query an alphabetically ordered list of all names in OCCUPATIONS, immediately followed by the first letter of each profession as a parenthetical (i.e.: enclosed in parentheses). For example: AnActorName(A), ADoctorName(D), AProfessorName(P), and ASingerName(S).

2. Query the number of ocurrences of each occupation in OCCUPATIONS. Sort the occurrences in ascending order, and output them in the following format:

There are a total of [occupation_count] [occupation]s.

where [occupation_count] is the number of occurrences of an occupation in OCCUPATIONS and [occupation] is the lowercase occupation name. If more than one Occupation has the same [occupation_count], they should be ordered alphabetically.

**Solution**
```sql
SELECT CONCAT(Name, '(', LEFT(Occupation,1), ')')
FROM Occupations ORDER BY Name;

SELECT CONCAT('There are a total of ', COUNT(Occupation), ' ', LOWER(Occupation), 's.')
FROM Occupations GROUP BY Occupation ORDER BY COUNT(Occupation), Occupation;
```

