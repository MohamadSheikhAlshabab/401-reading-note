# Read: Class 12: [URL](https://github.com/MohamadSheikhAlshabab/401-reading-note/blob/master/Read12.md)

## 10 minutes to pandas:
 - import: `import numpy as np` ,`import pandas as pd`
 - Object creation :Creating a Series by passing a list of values.
   -EX: ` s = pd.Series([1, 3, 5, np.nan, 6, 8])`
   - output:`0    1.0
1    3.0
2    5.0
3    NaN
4    6.0
5    8.0
dtype: float64` 
- Creating a DataFrame by passing a NumPy array.
  - EX: `dates = pd.date_range('20130101', periods=6)`
  - OUTPUT: `DatetimeIndex(['2013-01-01', '2013-01-02', '2013-01-03', '2013-01-04',
               '2013-01-05', '2013-01-06'],
              dtype='datetime64[ns]', freq='D')`
- Viewing data:Here is how to view the top and bottom rows of the frame:`df.head()`,`df.tail(3)`
- Display the index, columns: `df.index`
- DataFrame.to_numpy() gives a NumPy representation of the underlying data.
- __NumPy arrays have one dtype for the entire array, while pandas DataFrames have one dtype per column__.
- describe() shows a quick statistic summary of your data:`df.describe()`
- Transposing your data:`df.T`
- Sorting by an axis:` df.sort_index(axis=1, ascending=False)`
- Sorting by values:`df.sort_values(by='B')`
---
### Operations:
 - Stats: Performing a descriptive statistic: `df.mean()`
 - Apply: Applying functions to the data:` df.apply(np.cumsum)`
 - Histogramming:`s = pd.Series(np.random.randint(0, 7, size=10))`
 - String Methods: Series is equipped with a set of string processing methods in the str attribute that make it easy to operate on each element of the array, 
 as in the code snippet below:`s = pd.Series(['A', 'B', 'C', 'Aaba', 'Baca', np.nan, 'CABA', 'dog', 'cat'])`
 ---
### Merge:
 - Concat: Concatenating pandas objects together with concat():` df = pd.DataFrame(np.random.randn(10, 4))`
 - Join: SQL style merges. See the Database style joining section: `left = pd.DataFrame({'key': ['foo', 'foo'], 'lval': [1, 2]})`
 - Grouping: following one or more this stpes:
   - 1 - Splitting the data into groups based on some criteria
   - 2 - Applying a function to each group independently
   - 3 - Combining the results into a data structure
   - EX:`df = pd.DataFrame({'A': ['foo', 'bar', 'foo', 'bar',
   ....:                          'foo', 'bar', 'foo', 'foo'],
   ....:                    'B': ['one', 'one', 'two', 'three',
   ....:                          'two', 'two', 'one', 'three'],
   ....:                    'C': np.random.randn(8),
   ....:                    'D': np.random.randn(8)})`
   
  - Grouping and then applying the sum() function to the resulting group: `df.groupby('A').sum()`
  - Grouping by multiple columns forms a hierarchical index, and again we can apply the sum() function: `df.groupby(['A', 'B']).sum() `
---
### Reshaping:
 - Stack: ` tuples = list(zip(*[['bar', 'bar', 'baz', 'baz',
   ....:                      'foo', 'foo', 'qux', 'qux'],
   ....:                     ['one', 'two', 'one', 'two',
   ....:                      'one', 'two', 'one', 'two']]))`
  - `index = pd.MultiIndex.from_tuples(tuples, names=['first', 'second'])`
  - `df = pd.DataFrame(np.random.randn(8, 2), index=index, columns=['A', 'B'])`
  - `df2 = df[:4]`
 - The stack() method “compresses” a level in the DataFrame’s columns: `stacked = df2.stack()`
 - With a “stacked” DataFrame or Series (having a MultiIndex as the index), the inverse operation of stack() is unstack(): `stacked.unstack()`
---
### Pivot tables:
 - ` df = pd.DataFrame({'A': ['one', 'one', 'two', 'three'] * 3,
   .....:                    'B': ['A', 'B', 'C'] * 4,
   .....:                    'C': ['foo', 'foo', 'foo', 'bar', 'bar', 'bar'] * 2,
   .....:                    'D': np.random.randn(12),
   .....:                    'E': np.random.randn(12)})`
 - We can produce pivot tables from this data very easily: `pd.pivot_table(df, values='D', index=['A', 'B'], columns=['C'])`
--- 
### Time series:
 - pandas has simple, powerful, and efficient functionality for performing resampling operations during frequency conversion: `rng = pd.date_range('1/1/2012', periods=100, freq='S')`
 - Time zone representation:` rng = pd.date_range('3/6/2012 00:00', periods=5, freq='D')`
  - `ts = pd.Series(np.random.randn(len(rng)), rng)` 
  - ` ts_utc = ts.tz_localize('UTC')`
 - Converting to another time zone:` ts_utc.tz_convert('US/Eastern')`
 - Converting between time span representations:` rng = pd.date_range('1/1/2012', periods=5, freq='M')`,` ts = pd.Series(np.random.randn(len(rng)), index=rng)`.`ps = ts.to_period()`,`ps.to_timestamp()`
 - Converting between period and timestamp enables some convenient arithmetic functions to be used: `prng = pd.period_range('1990Q1', '2000Q4', freq='Q-NOV')`,`ts = pd.Series(np.random.randn(len(prng)), prng)`,`ts.index = (prng.asfreq('M', 'e') + 1).asfreq('H', 's') + 9`, `ts.head()`
---
### Categoricals:
 - pandas can include categorical data in a DataFrame:` df = pd.DataFrame({"id": [1, 2, 3, 4, 5, 6],
   .....:                    "raw_grade": ['a', 'b', 'b', 'a', 'a', 'e']})`
    -` df["grade"] = df["raw_grade"].astype("category")`,` df["grade"]`
 
---
### Plotting:
 - `import matplotlib.pyplot as plt`,` plt.close('all')`,`ts = pd.Series(np.random.randn(1000)`,`index=pd.date_range('1/1/2000', periods=1000))`,`ts = ts.cumsum()`,`ts.plot()`
---
### Getting data in/out:
 - CSV: ` df.to_csv('foo.csv')`
 - HDF5:Writing to a HDF5 Store: ` df.to_hdf('foo.h5', 'df')`, Reading from a HDF5 Store: `pd.read_hdf('foo.h5', 'df')`
 - Excel: Writing to an excel file: `df.to_excel('foo.xlsx', sheet_name='Sheet1')`, Reading from an excel file: `pd.read_excel('foo.xlsx', 'Sheet1')`, `index_col=None, na_values=['NA'])`
 - Gotchas: If you are attempting to perform an operation you might see an exception like:
 <pre> >>> if pd.Series([False, True, False]):
...     print("I was true")
Traceback
    ...
ValueError: The truth value of an array is ambiguous. Use a.empty, a.any() or a.all().</pre>
---


  
 
