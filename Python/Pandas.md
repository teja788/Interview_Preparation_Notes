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

```python
data.head(5)

data. tail(10)

data["var_1"].describe()

data.describe()
```

## Various data frame tranformation operations







