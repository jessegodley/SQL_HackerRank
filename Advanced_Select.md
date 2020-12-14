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

###**[Occupations](https://www.hackerrank.com/challenges/occupations)**

Pivot the Occupation column in OCCUPATIONS so that each Name is sorted alphabetically and displayed underneath its corresponding Occupation. The output column headers should be Doctor, Professor, Singer, and Actor, respectively.

Note: Print NULL when there are no more names corresponding to an occupation.

**Solution**
```sql
SELECT min(Doctor), min(Professor), min(Singer), min(Actor)
FROM
    ( Select ROW_NUMBER() OVER (PARTITION BY Occupation order by Name) rn, 
        CASE WHEN Occupation = 'Doctor' then Name end as Doctor,
        CASE WHEN Occupation = 'Professor' then Name end as Professor,
        CASE WHEN Occupation = 'Singer' then Name end as Singer,
        CASE WHEN Occupation = 'Actor' then Name end as Actor
    FROM OCCUPATIONS ORDER BY Name) a
GROUP BY rn
ORDER BY rn;
```

**NEW TABLE: BST**

The BST table is described as follows: (This table will be used for all problems until a new table is declared)

You are given a table, BST, containing two columns: N and P, where N represents the value of a node in Binary Tree, and P is the parent of N.

|  Column | Type |
|---|---|
| N | INTEGER |
| P | INTEGER |

###**[Binary Tree Nodes](https://www.hackerrank.com/challenges/binary-search-tree-1)**

Write a query to find the node type of Binary Tree ordered by the value of the node. Output one of the following for each node:

- Root: If node is root node.
- Leaf: If node is leaf node.
- Inner: If node is neither root nor leaf node.

**Solution**
```sql
SELECT N, IF(P IS NULL, 'Root', IF(B.N IN (SELECT P FROM BST), 'Inner', 'Leaf')) FROM BST AS B ORDER BY N;
```

