# Pandas

[Official documentation](https://pandas.pydata.org/pandas-docs/stable/reference/index.html#api).

There is 2 data structures in pandas: **DataFrame** (table) and **Series** (list).

A DataFrame is defined as a dictionary where keys are the column names. Unless specified otherwise row names are 0-indexed.

```python
# 0-indexed DataFrame
fruits = pd.DataFrame({'Apples': [30], 'Bananas': [21]})
```

|     | Apples       | Bananas |
|---|-------------|-----|
| 0     | 30 | 21 |


```python
# name-indexed DataFrame
fruit_sales = pd.DataFrame({'Apples': [35, 41], 'Bananas': [21, 34]}, index=['2017 Sales', '2018 Sales'])
```

|     | Apples       | Bananas |
|---|-------------|-----|
| 2017 Sales | 35 | 21 |
| 2018 Sales | 41 | 34 |

A Series is defined as an array. It can be considered as a single column DataFrame. In fact, when selecting an entire column of a DataFrame, a Series is returned (`<class 'pandas.core.series.Series'>`).

```python
# named Series with name-indexed elements
ingredients = pd.Series(['4 cups', '1 cup', '2 large', '1 can'], index=['Flour', 'Milk', 'Eggs', 'Spam'], name='Dinner')
```

|   | Dinner       |
|---|-------------|
| Flour | 4 cups | 
| Milk | 1 cup | 
| Eggs | 2 large | 
| Spam | 1 can | 

## Selection

* Column-first, row-second: native Python indexing `[]`
* Row-first, column-second: `loc` and `iloc` methods. 

```python
# select all rows and for each row only the first column
reviews.iloc[:, 0]

# select the last 5 rows and for each row all columns
reviews.iloc[-5:]
```

Difference between `loc` and `iloc`:
 
* `iloc` indexes `0:10` like this `0,...,9`, while
* `loc` indexes inclusively: `0:10` becomes `0,...,10`.

### Label-based selection

`loc` can use the DataFrame labels, while `iloc` can only treat it like a matrix. 

```python
# get rows 0, 1, 10 and 100 with columns labeled 'country','province','region_1','region_2'
df = reviews.loc[[0,1,10,100], ['country','province','region_1','region_2']]

# get first 100 rows with columns 'country' and 'variety'
df = reviews.loc[:99, ['country', 'variety']]
```
### Conditional selection

```python
# get the best wines from Italy
reviews.loc[(reviews.country == 'Italy') & (reviews.points >= 90)]
```

## Functions

### Summary

Summary functions apply on columns: `describe()`, `unique()`, `mean()`, `value_counts()`, etc.

### Map

`.map` (transform) a Series (column) into another. Original Series remains untouched.

```python
# remean the scores the wines received to 0
review_points_mean = reviews.points.mean()
reviews.points.map(lambda p: p - review_points_mean)

# tip: compiler is not smart enough to see the DataFrame didn't change, that is why the mean value is cached
```

### Apply

`.apply` transform a DataFrame into another. Original DataFrame remains untouched.

```python
# get each row sequentially in function `f`
reviews.apply(f, axis='columns')

# get each column sequentially in function `f`
reviews.apply(f, axis='index')
```

