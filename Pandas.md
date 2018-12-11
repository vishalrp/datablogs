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

#### 6. What if I had multiple things to filter on?

```
# Get only rows with city = Irvine OR London
df[(df['city'] == 'Irvine') | (df['city'] == 'London')]

```

#### 7. Group by and compute metrics?

```
# Say we had temp data for each month for 2 cities.

df = pd.DataFrame({'city': ['London']*12 + ['Irvine']*12,
                   'temp': [40, 42, 45, 50, 60, 72, 80, 81, 60, 55, 40, 32,
                            50, 52, 48, 55, 68, 73, 85, 90, 72, 68, 60, 51],
                   'month': list(range(1, 13)) + list(range(1, 13)),
                   'year': [2018]*24,
                   'season': ['winter', 'winter', 'winter', 'spring', 'spring', 'spring',
                              'summer', 'summer', 'summer', 'fall', 'fall', 'fall']*2})

# Mean temperature by city
df.groupby('city')['temp'].mean()                                                                                    

# Mean temperature by city, season
df.groupby(['city', 'season'])['temp'].mean()

Max and mean temperature by city and store into a new dataframe?
new_df = df.groupby('city').agg({'temp': ['mean', 'max']})

# new_df has multiple levels in columns, you can remove it by doing 
new_df.columns = new_df.columns.droplevel()    

# Let's make agg complicated -- group by city and season, and compute mean and max for temp and max for value of year. 
new_df = df.groupby(['city', 'season']).agg({'temp': ['mean', 'max'], 'year': 'max'})  

# You can also explicityly reset column names
new_df.columns = ['temp_mean', 'temp_max', 'year']
new_df.reset_index() 

# now new_df looks like a regular table with default index.

```

#### 8. What if I wanted to merge extra information?

```python

# Say you have country in another dataframe:
df_country = pd.DataFrame([{'country': 'UK', 'city': 'London'},
                           {'country': 'USA', 'city': 'Irvine'}])
df_with_country = df.merge(df_country, on='city')

# now df_with_country has all the columns from df + all the columns from df_country by joining/merging on the city column. i.e. country was added to the data frame.

```

