### Pandas...

is a popular library used for working with relational/tabular data. It provides several expressive data structures. 
Here is a nice tutorial https://pandas.pydata.org/pandas-docs/stable/10min.html for someone getting started.

#### 1. What are Series and DataFrame?

Think of a Series as a Column of data. Series can have row index or row labels. DataFrames are tables of data. 
DataFrames are made up of multiple Series. DataFrames also have a row index or row label.

#### 2. What is a row index or row label?

Each row in a Series or DataFrame can have a label associated with it to look up that row. The default is 0, 1, 2... N 
for a Series or DataFrame. In a dataframe a column can be made the index by calling df.set_index(colname).

#### 3. How do I create a dataframe?

```python
# read a csv file
import pandas as pd
df = pd.read_csv(csvfilepath)

# Using a list of dictionaries
df = pd.DataFrame([
                  {'city': 'London', 'temp': 42},
                  {'city': 'Irvine', 'temp': 71},
                  {'city': 'New York', 'temp': 53}
                  ])

# Using a dictionary where key is column name and value is a list of items. 
df = pd.DataFrame({
                  'city': ['London', 'Irvine', 'New York'],
                  'temp': [42, 71, 53]
                  })

# Note: the above two dataframes are the same! 3 rows, 2 columns.
```

#### 4. How I refer to a column?

```python
df['temp'] # Get the temp column
df['city'] # Get the city column
```

#### 5. How I filter rows, say temp > 50?

```python
# df.loc[<row filter>,<list of column names>]

new_df = df.loc[df['temp'] > 50, :]

# Q: What is "df['temp'] > 50" ?
# A: It create a series with booleans, True for rows where that condition is True and False otherwise.

```


