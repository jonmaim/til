# Pandas

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

A Series is defined as an array. It can be considered as a single column DataFrame.

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
