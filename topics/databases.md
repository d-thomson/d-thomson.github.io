# Databases

## Introduction
A database is an organized collection of data, generally stored and accessed electronically from a computer system. A database could be as simple as a text file with a list of names. Or it could be as complex as a large, relational database management system, complete with in-built tools to help you maintain the data. In this lesson, we will be focusing on Database Management Systems and SQL.

A Database Management System (DBMS), is a software program that enables the creation and management of databases. Generally, these databases will be more complex than the text file/spreadsheet example in the previous lesson. In fact, most of today's database systems are referred to as a Relational Database Management System (RDBMS), because of their ability to store related data across multiple tables.

Data is retrieved, modified or created from a database using a domain specific langauge called SQL, or Structure Query Language. It is particularly useful in handling structured data where there are relations between different entities/variables of the data.

## Tutorial
To interact with a database, we need to learn SQL. This tutorial will cover the basics of SQL.

#### Select
The SELECT statement is used to select data from a database.

```sql
SELECT column1, column2, ...
FROM mytable;
```
Above, `column1` and `column2` are the fields from `mytable` that we are extracting selecting. If you want to select all the fields in a certain table, we can use the `select *` method.

```sql
SELECT *
FROM mytable
```
The above statement will return all columns and rows from `mytable`. We can also use the `distinct` keyoword to only return distinct rows in the result set.
```sql
SELECT DISTINCT *
FROM mytable
```

#### Where
The WHERE statement is used to filter records returned by a SELECT statement. This clause is designed to allow you to only extract  rows from a table that fulfill a particular condition. In the example below, we are selecting all the fields from `mytable` and only grabbing the rows where column1 is equal to 1.

```sql
SELECT column1, column2
FROM mytable
WHERE column1 = 1
```
This is also possible with text and date fields, as well as various conditionals statements.

```sql
SELECT column1, column2, column3
FROM mytable
WHERE column3 > to_date('04/03/1999', 'MM/DD/YYYY')
```
You'll see above that we used a function, `to_date`. This is used to cast the string date to a date-type.

#### Linking Conditionals
Where clauses can also be combined with `and`, `or` and `not` statements which filters records on more than one condition. Using the `and` operator will bring back records if all the conditions between the `and` statement are true. The `or` operator will bring back records if at least one of the conditions between the `or` statement is true. The `not` operator will bring back records that are false. The `not` keyword is often shorthanded as `<>` which means not equal to.  

```sql
SELECT column1, column2, column3
FROM mytable
WHERE column1 = 1 AND column3 > to_date('04/03/1999', 'MM/DD/YYYY')
```
```sql
SELECT column1, column2, column3
FROM mytable
WHERE column1 = 1 OR column3 > to_date('04/03/1999', 'MM/DD/YYYY')
```
```sql
SELECT column1, column2, column3
FROM mytable
WHERE column2 NOT 'ABC'
```
```sql
SELECT column1, column2, column3
FROM mytable
WHERE column1 <> 1
```

#### Order By
The `order by` operation will sort the result set that is returned for you. There is an optional operator at the end where you can specify ascending or descending if you like. This keyword must always come last in the query, after any `where` clauses. Multiple columns can be selected to sort on with precendence to the first, then second and so on.

```sql
SELECT *
FROM mytable
ORDER BY column1, column2, column3 ASC
```
```sql
SELECT *
FROM mytable
ORDER BY column1
```
#### Aliases 
Aliases are used to give column or table names a temporary identifier or name in a query. These are often used to help with query readability. Aliases are assigned using the `as` keyword.

```sql
SELECT EMP.column1 AS ID, EMP.column2 AS FIRST_NAME
FROM mytable AS EMP
```

#### Joins
A join is used to combine result sets from multiple tables based on a predefined relationship in the column data. In this example, we have two columns with the same data, ID. One table contains the first names and another table contains the last names. We can join the two tables on the IDs to combine the information

```sql
SELECT fname.ID, fname.first_name, lname.last_name
FROM table1 AS fname
JOIN table2 AS lname ON fname.ID = lname.ID
```
```sql
SELECT fname.ID, fname.first_name, lname.last_name
FROM table1 AS fname, table2 AS lname
WHERE fname.ID = lname.ID
```
Both these queries will return the same result sets, selecting both tables and using a `where` clause to filter only where the IDs are equal is the same as a join.

#### Unions
A union is a way of combining the result sets of two queries. There are some constraints with unions, the number of columns must be the same and the columns must have the same data types.

```sql
SELECT fname.ID FROM table1 AS fname
UNION
SELECT lname.ID FROM table2 AS lname
```
The above query will return 1 column with all the IDs from table1 and table2.

#### Group By
The `group by` keyword is used alongside aggregate functions. Aggregate functions perform some sort of aggregation on a column. Some examples of aggregate functions are `count`, `max`, `min`, `sum` and `avg`. In the example below, we count the number of IDs and group by the first name, this way we will get a count of how many people have that name.
```sql
SELECT COUNT(fname.ID), fname.first_name
FROM table1 AS fname
GROUP BY fname.first_name
```

## Example
Here is a worked example.

## Tips, Tricks and Interview Questions
* What are tables and fields?
* What is a join?
* What is a database?
* What is an DBMS?
* What is an RDBMS?
