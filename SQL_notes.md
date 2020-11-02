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

## Advanced SQL commands





