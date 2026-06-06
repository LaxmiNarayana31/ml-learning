# Exploratory Data Analysis (EDA) with Pandas [CheatSheet]

> A comprehensive reference for EDA operations using the Pandas library in Python.

---

## 1. Data Loading

* **Read CSV File:** `df = pd.read_csv('filename.csv')`
* **Read Excel File:** `df = pd.read_excel('filename.xlsx')`
* **Read from SQL Database:** `df = pd.read_sql(query, connection)`

---

## 2. Basic Data Inspection

* **Display Top Rows:** `df.head()`
* **Display Bottom Rows:** `df.tail()`
* **Display Data Types:** `df.dtypes`
* **Summary Statistics:** `df.describe()`
* **Display Index, Columns, and Data:** `df.info()`

---

## 3. Data Cleaning

* **Check for Missing Values:** `df.isnull().sum()`
* **Fill Missing Values:** `df.fillna(value)`
* **Drop Missing Values:** `df.dropna()`
* **Rename Columns:** `df.rename(columns={'old_name': 'new_name'})`
* **Drop Columns:** `df.drop(columns=['column_name'])`

---

## 4. Data Transformation

* **Apply Function:** `df['column'].apply(lambda x: function(x))`
* **Group By and Aggregate:** `df.groupby('column').agg({'column': 'sum'})`
* **Pivot Tables:** `df.pivot_table(index='column1', values='column2', aggfunc='mean')`
* **Merge DataFrames:** `pd.merge(df1, df2, on='column')`
* **Concatenate DataFrames:** `pd.concat([df1, df2])`

---

## 5. Data Visualization Integration

* **Histogram:** `df['column'].hist()`
* **Boxplot:** `df.boxplot(column=['column1', 'column2'])`
* **Scatter Plot:** `df.plot.scatter(x='col1', y='col2')`
* **Line Plot:** `df.plot.line()`
* **Bar Chart:** `df['column'].value_counts().plot.bar()`

---

## 6. Statistical Analysis

* **Correlation Matrix:** `df.corr()`
* **Covariance Matrix:** `df.cov()`
* **Value Counts:** `df['column'].value_counts()`
* **Unique Values in Column:** `df['column'].unique()`
* **Number of Unique Values:** `df['column'].nunique()`

---

## 7. Indexing and Selection

* **Select Column:** `df['column']`
* **Select Multiple Columns:** `df[['col1', 'col2']]`
* **Select Rows by Position:** `df.iloc[0:5]`
* **Select Rows by Label:** `df.loc[0:5]`
* **Conditional Selection:** `df[df['column'] > value]`

---

## 8. Data Formatting and Conversion

* **Convert Data Types:** `df['column'].astype('type')`
* **String Operations:** `df['column'].str.lower()`
* **Datetime Conversion:** `pd.to_datetime(df['column'])`
* **Setting Index:** `df.set_index('column')`

---

## 9. Advanced Data Transformation

* **Lambda Functions:** `df.apply(lambda x: x + 1)`
* **Pivot Longer/Wider Format:** `df.melt(id_vars=['col1'])`
* **Stack/Unstack:** `df.stack()`, `df.unstack()`
* **Cross Tabulations:** `pd.crosstab(df['col1'], df['col2'])`

---

## 10. Handling Time Series Data

* **Set Datetime Index:** `df.set_index(pd.to_datetime(df['date']))`
* **Resampling Data:** `df.resample('M').mean()`
* **Rolling Window Operations:** `df.rolling(window=5).mean()`

---

## 11. File Export

* **Write to CSV:** `df.to_csv('filename.csv')`
* **Write to Excel:** `df.to_excel('filename.xlsx')`
* **Write to SQL Database:** `df.to_sql('table_name', connection)`

---

## 12. Data Exploration Techniques

* **Profile Report (with pandas-profiling):** `from pandas_profiling import ProfileReport; ProfileReport(df)`
* **Pairplot (with seaborn):** `import seaborn as sns; sns.pairplot(df)`
* **Heatmap for Correlation (with seaborn):** `sns.heatmap(df.corr(), annot=True)`

---

## 13. Advanced Data Queries

* **Query Function:** `df.query('column > value')`
* **Filtering with isin:** `df[df['column'].isin([value1, value2])]`

---

## 14. Memory Optimization

* **Reducing Memory Usage:** `df.memory_usage(deep=True)`
* **Change Data Types to Save Memory:** `df['column'].astype('category')`

---

## 15. Multi-Index Operations

* **Creating MultiIndex:** `df.set_index(['col1', 'col2'])`
* **Slicing on MultiIndex:** `df.loc[(slice('index1_start', 'index1_end'), slice('index2_start', 'index2_end'))]`

---

## 16. Data Merging Techniques

* **Outer Join:** `pd.merge(df1, df2, on='column', how='outer')`
* **Inner Join:** `pd.merge(df1, df2, on='column', how='inner')`
* **Left Join:** `pd.merge(df1, df2, on='column', how='left')`
* **Right Join:** `pd.merge(df1, df2, on='column', how='right')`

---

## 17. Dealing with Duplicates

* **Finding Duplicates:** `df.duplicated()`
* **Removing Duplicates:** `df.drop_duplicates()`

---

## 18. Custom Operations with Apply

* **Custom Apply Functions:** `df.apply(lambda row: custom_func(row['col1'], row['col2']), axis=1)`

---

## 19. Handling Large Datasets

* **Chunking Large Files:** `pd.read_csv('large_file.csv', chunksize=1000)`
* **Iterating Through Data Chunks:** `for chunk in pd.read_csv('file.csv', chunksize=500): process(chunk)`

---

## 20. Integration with Matplotlib for Custom Plots

* **Custom Plotting:** `import matplotlib.pyplot as plt; df.plot(); plt.show()`

---

## 21. Specialized Data Types Handling

* **Working with Categorical Data:** `df['column'].astype('category')`
* **Dealing with Sparse Data:** `pd.arrays.SparseArray(df['column'])`

---

## 22. Performance Tuning

* **Using Swifter for Faster Apply:** `import swifter; df['column'].swifter.apply(lambda x: func(x))`
* **Parallel Processing with Dask:** `import dask.dataframe as dd; ddf = dd.from_pandas(df, npartitions=10)`

---

## 23. Visualization Enhancement

* **Customize Plot Style:** `plt.style.use('ggplot')`
* **Histogram with Bins Specification:** `df['column'].hist(bins=20)`
* **Boxplot Grouped by Category:** `df.boxplot(column='num_column', by='cat_column')`

---

## 24. Advanced Grouping and Aggregation

* **Group by Multiple Columns:** `df.groupby(['col1', 'col2']).mean()`
* **Aggregate with Multiple Functions:** `df.groupby('col1').agg(['mean', 'sum'])`
* **Transform Function:** `df.groupby('col1').transform(lambda x: x - x.mean())`

---

## 25. Time Series Specific Operations

* **Time-Based Grouping:** `df.groupby(pd.Grouper(key='date_col', freq='M')).sum()`
* **Shifting Series for Lag Analysis:** `df['column'].shift(1)`
* **Resample Time Series Data:** `df.resample('M', on='date_col').mean()`

---

## 26. Text Data Specific Operations

* **String Contains:** `df[df['column'].str.contains('substring')]`
* **String Split:** `df['column'].str.split(' ', expand=True)`
* **Regular Expression Extraction:** `df['column'].str.extract(r'(regex)')`

---

## 27. Data Normalization and Standardization

* **Min-Max Normalization:** `(df['column'] - df['column'].min()) / (df['column'].max() - df['column'].min())`
* **Z-Score Standardization:** `(df['column'] - df['column'].mean()) / df['column'].std()`

---

## 28. Working with JSON and XML

* **Reading JSON:** `df = pd.read_json('filename.json')`
* **Reading XML:** `df = pd.read_xml('filename.xml')`

---

## 29. Advanced File Handling

* **Read CSV with Specific Delimiter:** `df = pd.read_csv('filename.csv', delimiter=';')`
* **Writing to JSON:** `df.to_json('filename.json')`

---

---

# ➕ Extra — Interview-Critical Topics (Bonus)

> These are **frequently asked in MNC interviews** but were missing from the original sheet.

---

## 30. Copy vs View (Most Common Interview Trap)

* **Safe Copy of DataFrame:** `df_copy = df.copy()`
* **Avoid SettingWithCopyWarning:** Always use `.copy()` when slicing before modifying

```python
# Wrong - may raise SettingWithCopyWarning
df2 = df[df['col'] > 5]
df2['new_col'] = 1

# Correct
df2 = df[df['col'] > 5].copy()
df2['new_col'] = 1
```

---

## 31. map() vs apply() vs applymap() — Classic Interview Question

* **map()** — element-wise on a Series only: `df['col'].map({'a': 1, 'b': 2})`
* **apply()** — row/column-wise on DataFrame or Series: `df.apply(func, axis=1)`
* **applymap()** — element-wise on entire DataFrame: `df.applymap(func)` *(deprecated in Pandas 2.1+, use `df.map(func)`)*

```python
# map: replace values using dict or function
df['grade'].map({'A': 4, 'B': 3, 'C': 2})

# apply: custom logic across rows
df.apply(lambda row: row['col1'] + row['col2'], axis=1)

# map on DataFrame: apply to every cell
df.map(lambda x: round(x, 2))
```

---

## 32. Binning Data

* **Equal-Width Bins:** `pd.cut(df['column'], bins=5)`
* **Equal-Frequency Bins:** `pd.qcut(df['column'], q=4)`
* **With Custom Labels:** `pd.cut(df['column'], bins=[0, 25, 50, 75, 100], labels=['Low', 'Mid', 'High', 'Very High'])`

---

## 33. Top-N Queries

* **Largest N values:** `df.nlargest(5, 'column')`
* **Smallest N values:** `df.nsmallest(5, 'column')`
* **Top N per group:**

```python
df.groupby('category').apply(lambda x: x.nlargest(3, 'sales')).reset_index(drop=True)
```

---

## 34. Explode (List-Type Columns)

* **Explode list column into rows:** `df.explode('column')`

```python
df = pd.DataFrame({'name': ['Alice', 'Bob'], 'skills': [['Python', 'SQL'], ['R', 'Tableau']]})
df.explode('skills')
```

---

## 35. Method Chaining (Clean Pipeline Style)

```python
result = (
    df
    .dropna(subset=['revenue'])
    .rename(columns={'rev': 'revenue'})
    .query('revenue > 1000')
    .groupby('region')['revenue']
    .sum()
    .reset_index()
    .sort_values('revenue', ascending=False)
)
```

---

## 36. Window Functions

* **Cumulative Sum:** `df['column'].cumsum()`
* **Cumulative Max:** `df['column'].cummax()`
* **Cumulative Min:** `df['column'].cummin()`
* **Percent Change:** `df['column'].pct_change()`
* **Rank:** `df['column'].rank(method='dense')`

---

## 37. Useful Shortcuts Often Asked

* **Shape of DataFrame:** `df.shape`
* **Column names as list:** `df.columns.tolist()`
* **Count of non-null values:** `df.count()`
* **Check if column exists:** `'col' in df.columns`
* **Sample random rows:** `df.sample(n=5, random_state=42)`
* **Reset index:** `df.reset_index(drop=True)`
* **Sort by column:** `df.sort_values('column', ascending=False)`
* **Transpose DataFrame:** `df.T`

---

## Quick Reference Summary

| Category | Key Methods |
|---|---|
| Loading | `read_csv`, `read_excel`, `read_sql`, `read_json`, `read_xml` |
| Inspection | `head`, `tail`, `info`, `describe`, `dtypes`, `shape` |
| Cleaning | `isnull`, `fillna`, `dropna`, `drop_duplicates`, `copy` |
| Transformation | `apply`, `map`, `groupby`, `merge`, `concat`, `pivot_table` |
| Visualization | `hist`, `boxplot`, `plot.scatter`, `plot.line` |
| Statistics | `corr`, `cov`, `value_counts`, `unique`, `nunique` |
| Export | `to_csv`, `to_excel`, `to_sql`, `to_json` |
| Interview Traps | `copy()`, `map vs apply`, `loc vs iloc`, `cut vs qcut` |

---
