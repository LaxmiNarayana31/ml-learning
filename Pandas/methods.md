# I/O / Serialization

* `read_csv(...)` — load a CSV file into a DataFrame.
* `to_csv(path, ...)` — write a DataFrame to a CSV file.
* `read_parquet(...)` — read a Parquet file into a DataFrame.
* `to_parquet(path, ...)` — write a DataFrame to Parquet.
* `read_excel(...)` — read an Excel sheet into a DataFrame.
* `to_excel(path, ...)` — write a DataFrame to an Excel file.
* `read_sql(query, con, ...)` — load results of a SQL query into a DataFrame.
* `to_sql(name, con, ...)` — write a DataFrame to a SQL table.
* `read_json(...)` — read JSON data into a DataFrame/Series.
* `to_json(path_or_buf, ...)` — serialize a DataFrame/Series to JSON.
* `read_table(...)` — read a delimited table (like read_csv with different defaults).
* `read_feather(...)` / `to_feather(...)` — fast columnar on-disk read/write for DataFrame.

# Quick inspection & summary

* `head(n)` — return the first `n` rows.
* `tail(n)` — return the last `n` rows.
* `info()` — concise summary of DataFrame (dtypes, non-null counts, memory).
* `shape` (attribute) — tuple `(rows, columns)` of the DataFrame.
* `columns` (attribute) — Index of column labels.
* `dtypes` (attribute) — dtypes of each column.
* `describe()` — summary statistics (count, mean, std, quartiles) for numeric (and optionally object) columns.
* `memory_usage(deep=False)` — memory usage per column (and total if requested).
* `sample(n=None, frac=None)` — return a random sample of rows.
* `value_counts()` (Series) — frequency counts of unique values.

# Selection & indexing

* `loc[...]` — label-based row/column selection/indexing.
* `iloc[...]` — integer position-based row/column selection/indexing.
* `at[row_label, col_label]` — fast scalar access by label.
* `iat[row_pos, col_pos]` — fast scalar access by integer position.
* `set_index(keys, inplace=False)` — set one or more columns as the index.
* `reset_index(drop=False, inplace=False)` — reset index back to default integer index.
* `reindex(index=None, columns=None, ...)` — conform DataFrame to new index/columns, filling missing.
* `xs(key, axis=0)` — cross-section selection from MultiIndex.

# Row / column operations

* `drop(labels, axis=0/1, inplace=False)` — drop rows or columns by label.
* `dropna(axis=0/1, how='any', ...)` — remove rows/columns with missing values.
* `fillna(value, inplace=False)` — replace missing values with a specified value/method.
* `replace(to_replace, value, ...)` — replace specified values throughout DataFrame/Series.
* `rename(mapper=None, columns=None, index=None, inplace=False)` — rename axis labels or columns.
* `astype(dtype)` — cast Series/DataFrame columns to specified dtype(s).
* `sort_values(by, ascending=True)` — sort rows by column(s) values.
* `sort_index(axis=0/1)` — sort by index labels.
* `insert(loc, column, value)` — insert a new column at specified column position.
* `pop(item)` — remove and return a column (like `del` but returns the Series).

# Transform / mutate / apply

* `assign(**kwargs)` — add new columns or overwrite columns with expressions.
* `apply(func, axis=0/1)` — apply a function along rows or columns (returns Series/DataFrame).
* `applymap(func)` — apply elementwise function to entire DataFrame.
* `map(func_or_dict)` (Series) — map values using function/dict/Series.
* `pipe(func, *args, **kwargs)` — pass the object through a function (method chaining helper).
* `where(cond, other=...)` — keep values where condition is True, otherwise replace.
* `mask(cond, other=...)` — inverse of `where`: replace where condition is True.
* `agg` / `aggregate(func)` — compute one or more aggregations per column/group.
* `transform(func)` — return transformed object aligned with original index (useful in groupby).

# Merging / combining / reshaping

* `merge(right, how='inner', on=...)` — SQL-style join between DataFrames.
* `concat(objs, axis=0/1)` — concatenate DataFrames along rows or columns.
* `join(other, on=None, how='left')` — join columns of another DataFrame by index or key.
* `pivot(index, columns, values)` — reshape data (unique index/columns pair required).
* `pivot_table(values, index, columns, aggfunc='mean')` — grouped pivot with aggregation.
* `melt(id_vars=None, value_vars=None)` — unpivot wide format to long format.
* `stack()` — pivot columns into a (lower) row-level index (wide→long).
* `unstack()` — inverse of `stack()` (long→wide) at specified level.
* `explode(column)` — transform each element of a list-like column into separate rows.

# Grouping & aggregation / time-window ops

* `groupby(by)` — split-apply-combine grouping object for aggregation/transform/filter.
* `agg` / `aggregate` (GroupBy) — apply aggregation functions to groups.
* `transform` (GroupBy) — apply transformations to each group and return aligned object.
* `filter` (GroupBy) — filter groups based on group-wise criterion.
* `apply` (GroupBy) — apply arbitrary function to each group.
* `rolling(window)` — rolling window operations (e.g., `.mean()`, `.sum()`).
* `expanding()` — cumulative expanding window aggregation.
* `resample(rule, on=None)` — time-series resampling (e.g., 'D', 'M') for frequency conversion.
* `cumsum()` / `cumprod()` / `cumcount()` — cumulative sum/product/count operations.

# Missing / boolean / filtering helpers

* `isna()` / `isnull()` — boolean mask of missing values.
* `notna()` / `notnull()` — boolean mask of non-missing values.
* `drop_duplicates(subset=None, keep='first')` — remove duplicate rows.
* `duplicated(subset=None, keep='first')` — boolean mask marking duplicate rows.
* `isin(values)` — boolean mask for membership in provided values.
* `between(left, right)` (Series) — boolean mask for values between left and right (inclusive).

# Statistics / correlation / descriptive

* `mean()` — arithmetic mean of values.
* `median()` — median of values.
* `std()` — standard deviation.
* `var()` — variance.
* `sum()` — sum of values.
* `min()` / `max()` — minimum and maximum values.
* `count()` — non-null count per column/Series.
* `corr()` — pairwise correlation of columns.
* `cov()` — pairwise covariance of columns.
* `quantile(q)` — compute sample quantile(s).

# Index / categorical / factor handling

* `get_dummies(data, columns=None)` — one-hot encode categorical variables.
* `factorize(values)` — encode values as integer labels and return uniques.
* `astype('category')` — convert a column to categorical dtype (with `.cat` accessor).
* `.cat.categories` / `.cat.codes` / `.cat.remove_unused_categories()` — category accessor helpers.
* `cut(x, bins)` — bin numeric data into discrete intervals.
* `qcut(x, q)` — bin data into quantile-based buckets.

# Datetime & time-series helpers

* `to_datetime(arg, ...)` — convert argument to datetime dtype.
* `.dt` accessor (Series.dt) — access datetime attributes like `.dt.year`, `.dt.month`, `.dt.day`, `.dt.weekday`.
* `shift(periods=1)` — shift index by desired number of periods (useful for lag features).
* `pct_change(periods=1)` — percent change over given number of periods.
* `asfreq(freq)` — convert time series to a specified frequency without aggregation.

# String methods (Series.str)

* `Series.str.strip()` — remove leading/trailing whitespace.
* `Series.str.lower()` / `Series.str.upper()` — change case.
* `Series.str.contains(pat)` — boolean mask for substring/regex match.
* `Series.str.replace(pat, repl)` — replace substring or regex.
* `Series.str.split(pat)` — split strings into lists (can expand into columns).
* `Series.str.extract(pat)` — extract capture groups from regex into columns.

# Index / label helpers

* `index` (attribute) — Index object of row labels.
* `rename_axis(name)` — set the name of the row/column axis.
* `set_axis(labels, axis=0/1, inplace=False)` — set new labels for index/columns.

# Conversion / export helpers

* `to_numpy()` — convert DataFrame/Series to a NumPy array.
* `to_dict()` — convert DataFrame/Series to a dict (various `orient` options).
* `to_records()` — convert to NumPy record array.
* `astype()` — (already listed) cast dtypes explicitly.

# Filtering & expression evaluation

* `query(expr)` — filter DataFrame using a string expression (for readability/performance).
* `eval(expr)` — evaluate an expression in the DataFrame’s namespace (fast column-wise ops).

# Sampling / ranking / selection helpers

* `sample(n=None, frac=None)` — (listed) random sample of rows.
* `rank()` — compute numerical data rank along an axis.
* `nlargest(n, columns)` — return `n` largest rows by column(s).
* `nsmallest(n, columns)` — return `n` smallest rows by column(s).
* `idxmax()` / `idxmin()` — index (label) of max/min value per column/Series.

# Plotting / quick visualization (pandas wrappers)

* `plot()` (Series/DataFrame) — simple plotting API that delegates to matplotlib/plotting backends.
* `hist()` — draw histogram(s) for columns.
* `boxplot()` — draw box plots for distributions.
* `plot.scatter(x, y)` / `plot.line()` — scatter/line plot shortcuts.

# Misc / helpers often used in ML pipelines

* `merge_asof(left, right, on, by=None)` — perform as-of (time-ordered) joins for nearest-key joins.
* `interpolate(method='linear')` — fill missing values using interpolation.
* `unique()` (Series) — return unique values.
* `nunique()` — count distinct values.
* `sem()` — standard error of the mean (and other statistical helpers).
