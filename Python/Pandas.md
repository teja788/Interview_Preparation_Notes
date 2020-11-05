# Pandas Summary notes

* Pandas is a very efficent library to perfrom data transformation operations
* Statement to get the package - import pandas as pd


## Basic objects

* Two core objects in pandas - DataFrame and Series
* Series is a sequence or list of values
* Data frame is a table with rows and columns. each column belongs to same datatype



```python

lis = pd.Series([1,2,3],index = ["a","b","c"]) # create a series

data = pd.DataFrame({'Yes': [1, 2], 'No': ["a", "b"]}) # to create a data frame

data = pd.DataFrame({'Yes': [1, 2], 'No': ["a", "b"]},
                          index = ["ind1","ind2"]) # to create a data frame with index
```

## Data Loading and Writing

**read_table, read_csv** - can be used to read in the data files from system, cloud, web etc.

* read_csv has many parameters which can be used to customize loading

**to_csv** - used to write data to system. it also contains many parameters for custom operations

```python

data = pd.read_csv("path_of_file",header = True, index = 0) 

data.to_csv("filename", index = False)

help(read_csv) # this loads the documentation for checking all parameters

```

## Data attributes

**head, tail** - used to get first or last n rows. helps to look at the data

**shape** - gives no. of columns and rows in data

**describe** - gives a good snapshot of columns (min,max, median etc)

**value_counts()** - gives frquency count of a column

```python
data.head(5)

data. tail(10)

data["var_1"].describe()

data.describe()

data["var_1"].value_counts()
```

## Various data frame tranformation operations

### Indexing and selecting

* ** iloc, loc** are used for indexing and selecting data

* iloc - selects using index of rows and columns
* iloc treats the data like big matrix and just gives what are the elements in that position. It ignores actual index lables and column names
* loc - selects using labels of rows and columns
* loc uses the index lables and column names
* One main thing to remember 0:10 in iloc means 0,1,2,...9. whereas 0-10 in loc means 0,1,2,3...10
* conditional selection can be done using loc

examples:
```python
data.column_name, data["column_name"] # select a column from data frame

data.colum_name[0] # gives the first row of column

data.iloc[0] # selects the first row

data.iloc[:,0] # selects the first column

data.iloc[:3,0] # first 3 rows of first column

data.iloc[[0,1,2],0] # selection using a list

data.iloc[-5:] # last 5 rows

data.loc[0,"var_1"] # gives first row of var_1

data.loc[:,["var_1","var_2"]] # selects all rows of two variables

data.set_index("var_1) - sets index to var_1

data.loc[data.var_1 == "something"] # all rows following this condition selected

data.loc[(data.var_1 == "something) & (data.var_2 == "somethingelse")] # selection using multiple conditions

data.loc[data.var_1.isin("var_1","var_2")]

data.loc[data.var_1.notnull()] # gives all not null rows based on var_1

data.loc[data.var_1 = "something"] = value # assigs the value to conditions selected data
```

### map, lambda, apply

* map is used to apply a custom function to each value
* apply is similar method as map but can transform whole dataframe

example:
```python
data.var_1.map(lambda x: x - data.var_1.mean())
data.var_1 - data.var_1.mean() # acheiveing above through different way
```


ref:
https://www.kaggle.com/residentmario/indexing-selecting-assigning












