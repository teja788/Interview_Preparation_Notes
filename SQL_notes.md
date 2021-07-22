# SQL - Notes

* SQL stands for Structred Query Langauage. It is used for creation, extraction and manipulation of databases
* SQL is case insensetive


## Commonly used SQL commands

**Select** - to select variables from a table

**where** - to filter the table by a condition

**order by** - to order the results by a column or multiple columns

**limit** - restricts how many rows to return

**Like,IN,Between,OR,AND,NOT,IS NULL** - various logical operators to filter data

**Count, Sum, Avg, Min/Max** - perform various aggregate opearations

**Distinct** - used to get unique values, can be used with count, group by etc.

**Cast** - used to covert data type of a column



examples:

```sql
Select * from table

Select var1,var2 as temp from table where var1 = 30 order by var2 asc

Select * from table Limit 10

Select * from table where var1 like "abc%"

Select * from table where var1 in [1,2,3]

Select * from table where var1>=5 and var2<10

Select * from table where var1 is null

Select * from table where var1 is not null

Select Sum(var1) from table

Select cast(var1 as integer) from table 

```

##Intermediate SQL commands

**Group By** - seperate data into groups

**Having** - allows you to filter on grouped columns

**Case, When, Then, Else, End** - used similar if else  to make a new column conditionaly based on some other column, Column made can be used with groupby

**Join On** - used to join two tables based on a column or columns
  * Inner - to join based on the matching items between the col
  * Left - gives the joined rows and all the rows in left table. right part of new table will be null for the table where left only present
  * Right - oppposite of Left join
  * Full Outer Join - it is a combination of both left and right join
  * Self Join - Join the table on itself
  
**Union** - To combine rows of two tables one below other

**intersect** - works intersecting columns, similar to set intersects

**minus** - rows from below table will be eliminated from rows of above table



```sql
Select count(*) as count_var1 from table group by var1

Select max(var2) as max_var2, var1 from table group by var1 Having max(var2) <10

Select case when var1<10 then "a"
            when var1<20 then "b"
            else "c" End as flag
       from table
  
Select a.*, b.* from table1 a join table2 b on a.var_1 = b.var_1

Select a.*, b.* from table1 a join table2 b on a.var_1 = b.var_1 and a.var_2 = b.var_2


Select * from table1
Union
Select * from table2

```
### String manipulation Commands

**Left, Right** - Pull a certain no. of characters from left or right side of strings.

**Trim** - used to remove characters from beginnining and end of a string.

**Substr** - used to create a substring by specifying start position and no. of characters.

**concat** - used to concatenate columns side by side

**Upper, Lower** - for changing case of string to lower, upper

**Coalesce** - it is used to replace null values

examples:
```sql
Select Left(var1,10) as var1_left from table

Select substr(var1,4,2) as var1_substr from table

Select concat(var1,var2) as var_concat from table

Select coalesce(var1,"null") as var1_null from table

```

## Advanced SQL commands

### Sub Queries
* They are too for perfoming task in multiple steps. Inner queries are first executed.

* Sub queries can be used to aggregate in multiple stages. They can also be used in conditional logic 

* Can be used in joins

* sub queries create a view (temp table) using inner query and perform operations of outer query on that.

examples:
```sql

select * from(
 select var1 from table where var2 = "something") sub
 where sub.var2 = "something else"
 
select * form table1 where var1 = (
  select min(var1) from table2)
 ```
 
### Window functions
* window function performs calculation across set of rows based on other rows.
* it is similar to group by but rows wont be aggregated and retain there original form.
* window can be given alias

**Over, Partition by** - used commonly in window funcrions

**Row_number()** - used to give row number over rows seperated by patitions

**rank** - same as row no but will give same rank if two values are same and next rank is skipped

**dense_rank()** - same as rank but ranks are not skipped

**lag, lead** - used to compare with before or after value

examples:
```sql
Select *,sum(var_2) over (partition by var_1 order by var_3) as var_2_total from table

select *, rank() over (partition by var_1 order by var_2) from table

select var_1 - lag(var_1, 1) as diff from table1

select sum(var_1) over window_var2, avg(var_1) over window_var2 from table
 window window_var2 as (partition by var_2 order by var_3)

```
### Performance improvements
* Make tables smaller, make joins less complicated
* Explain can be used at start of query to get an idea how long query runs


## Reference
https://mode.com/sql-tutorial/introduction-to-sql/

## Commonly asked sql interview questions

* select the second highest salary

```sql
Select max(salary) from table 
      where salary<(select max(salary) from table)
```
* select nth highest salary 

```sql
SELECT salary 
FROM
(SELECT salary 
FROM emp
ORDER BY salary DESC LIMIT n)as table2 
ORDER BY table2.salary ASC
LIMIT 1

select * from (select distinct sal from emp order by sal desc)
where rownum <= 3

minus

select * from (select distinct sal from emp order by sal desc)
where rownum <= 2
```
* select alternate rows of table

```sql
 select rownum rn, col1,col2 from table
          order by rn
           where mod(rn,2)!=0
```
* select first n rows and last n rows of table

```sql
select * from (select rownum r, table.* from table)
where r > ( select count(*) - n from table) or r < n
```



## references
* https://www.youtube.com/playlist?list=PLqM7alHXFySGweLxxAdBDK1CcDEgF-Kwx - youtube geeksforgeeks

## link to help create datasets and try out queries
# To create the dataset
* https://www.mockaroo.com/
# to upload the data and try queries
* https://sqliteonline.com/

## most asked questions with solutions
* https://www.youtube.com/watch?v=fvPddKyHxpQ&list=PL6n9fhu94yhXcztdLO7i6mdyaegC8CJwR




