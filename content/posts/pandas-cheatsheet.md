---
title: "Pandas - Quick review"
date: 2024-02-05T19:30:06+05:30
draft: false
toc: false
images:
tags: [python, pandas, ml]
---  

#### Introduction
Pandas, open-source library for data analysis and manipulation in python. The following is like a cheatsheet for myself to go through before interviews. Examples can be found in [github](https://gist.github.com/animi4695/80de2fc7462d04f57920c8492148cb07).

#### Importing, Exporting data
```
# read/write csv from/to file
pd.read_csv(filename) | df.to_csv(filename)

# read from a delimited text file (like TSV)
pd.read_table(filename)

pd.read_excel(filename) | df.to_excel(filename)

# read/write from/to a SQL table/db
pd.read_sql(query, connection_object) | df.to_sql(tablename, connection_object)

# read/write json from/to string, url or file
pd.read_json(json_string) | df.to_json(filename)

# parse an html URL, string or file and extracts tables to a list of dataframes
pd.read_html(url) | df.to_html(filename)

# takes the contents of your clipboard and passes it to read_table(), viceversa
pd.read_clipboard() | df.to_clipboard()

# From a dict, key for columns, values for data as lists
pd.DataFrame(dict)
```

#### Viewing/Inspecting data
```
df.head(n) - First n rows of df

df.tail(n) - Last n rows of df

df.shape() - num of rows & columns

df.info() - index, datatype and memory info

df.describe() - summary statistic for numerical columns

```

#### Selection
```
df[col] - returns column with label col as Series

df[[col1, col2]] - returns columns as a new df

s.iloc[0] - selection by position

s.loc[0] - selection by index

df.iloc[0, :] - first row

df.iloc[0, 0] - first element of first column
```

#### Data Cleaning
```
df.columns = ['a', 'b', 'c'] - renames columns

pd.isnull - checks for null values, return boolean array

pd.notnull()

# options:
# axis = 1 (drops all columns containing null values)
# thresh = n (drops all rows having less than n non-null values)
df.dropna() - drops all rows containing null values

df.fillna(x) - replaces all null values with x

s.fillna(s.mean()) - replaces all null values with mean

s.astype(float) - converts datatype of series to float

s.replace(1, 'one') - replaces all values equal to 1 with 'one'

s.replace([1,3], ['one', 'three']) - replaces all 1 with 'one', 3 with 'three'

df.rename(columns = lambda x : x + 1) - rename columns

df.rename(index = lambda x : x + 1) - rename index

df.rename(columns = {'old_name' : 'new_name}) - selective renaming

df.set_index('column_one') - changes the index

```

#### Filter, sort & groupby
```
df[df[col] > 0.5] - rows where col column is > 0.5

df.sort_values(col1) - sorts values by col1 in ascending order

df.sort_values([col1, col2], ascending=[True, False]) - col1 by ascending order, col2 by descending order

df.groupby(col) - returns a groupby object for values from one column

df.groupby([col1, col2]) - returns a groupby object values from multiple columns

df.groupby(col1)['col2'] - returns mean of values in col2, grouped by values in col1

df.pivot_table(index = col1, values = [col2, col3], aggfunc = mean) - creates a pivot table that groups by col1 and calcultes the mean of col2, col3

df.apply(np.mean) - applies a function across each column

df.apply(np.max, axis = 1) - applies a function across each row
```

#### join/combine
```
df1.append(df2) - adds rows in df1 to end of df2 (columns should be identical)

pd.concat([df1, df2], axis = 1) - adds columns in df1 to end of df2 (rows should be identical)

df1.join(df2, on=col1, how = 'inner') - SQL-style joins the columns in df1 with columns on df2 where the rows for col have identical value. 'how' can be left, right, outer, inner
```
---
*References : Python Pandas for your grandpa, Dataquest pandas cheatsheet*   
