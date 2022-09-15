# Pandas

### Series

**Series** is a one-dimensional labeled array capable of holding any data type (integers, strings, floating point numbers, Python objects, etc.). 

```python
s = pd.Series(data, index=index)

# Example 1

s = pd.Series(np.random.randn(5), index=["a", "b", "c", "d", "e"])

# Example 2

d = {"b": 1, "a": 0, "c": 2}

pd.Series(d)
```

#### Input
* python dict
* an ndarray
* a scalar value (like 5)


#### Series is Ndarray-like

```python
# First value
s[0]
# First to third
s[:3]
# s such that all values are greater than the median of the values of s.
s[s > s.median()]
# Extract these values in this order
s[[4,3,1]]
# element wise exponential 
np.exp(s)
# Type that the elements are
s.dtype
```
#### Vectorized operations

```python
# Addition
s + s

# Multiplication
s * 2

# Exponential
np.exp(s)

# Adding selected elements
s[1:] + s[:-1]

```
#### Name

```python
s = pd.Series(np.random.randn(5), name="something")

s.name

# Rename

s2 = s.rename("different")
```

### DataFrame


**DataFrame** is a 2-dimensional labeled data structure with columns of potentially different types. You can think of it like a spreadsheet or SQL table, or a dict of Series objects. It is generally the most commonly used pandas object.


```python
# Example 1 

d = {

    "one": pd.Series([1.0, 2.0, 3.0], index=["a", "b", "c"]),

    "two": pd.Series([1.0, 2.0, 3.0, 4.0], index=["a", "b", "c", "d"]),

}

df = pd.DataFrame(d)

# Example 2

d = {"one": [1.0, 2.0, 3.0, 4.0], "two": [4.0, 3.0, 2.0, 1.0]}

pd.DataFrame(d)

# Change index and add/change columns

pd.DataFrame(d, index=["a", "b", "c", "d"], columns=["two", "three"])

```
#### Column and row labels

```python
d.index

Out[42]: Index(['a', 'b', 'c', 'd'], dtype='object')

d.columns

Out[43]: Index(['one', 'two'], dtype='object')
```

#### Input

* Dict of 1D ndarrays, list, dicts, or Series
* 2-D numpy.ndarray
* Structured or record ndarray
* A Series
* Another DataFrame

#### Column selection, addition, deletion

```python
# Select one column
df["one"]

# Change a column
df["three"] = df["one"] * df["two"]

df["flag"] = df["one"] > 2

# Deletion
del df["two"]

three = df.pop("three")

# Assign new columns in method chains
df.assign(three = df["one"] / df["two"]).head()

df.assign(three = lambda x: (x["one"] / x["two"])).head()

# assign always returns a copy leaving the original untouched

```

#### Indexing/Selection

```python
# Select column
df[col]

# Select row by label
df.loc[label]

# Select row by integer location
df.iloc[loc]

# slice rows 
df[5:10]

# select rows by boolean vector
df[bool_vec]

```
#### Operation 

```python
# Addition
df1 + df2

# Subtraction
df - df.iloc[0]

# Scalar operations

df * 5 + 2

# Inverse

1 / df
```

### Methods

#### pipe()
Apply a function to the DataFrame that will overwrite an existing column:
```python
dataframe.pipe(func, args, kwargs) 
```
#### add()
This method is used for addition of dataframe and other, element-wise (binary operator add).

```python
DataFrame.add(other, axis=’columns’, level=None, fill_value=None)

# Example
df.add(1, fill_value = 10)
# replaces nan with 10 and adds 1 to all the elements
```
#### pct_change()
Percentage change between the current and a prior element.

```python
DataFrame.pct_change(periods=1, fill_method='pad', limit=None, freq=None, **kwargs)
```
