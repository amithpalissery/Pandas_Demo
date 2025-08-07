

# 🐼 Data Manipulation and Analysis with Pandas

## 2.1. 📌 Introduction to Pandas

### ➤ What is Pandas?

Pandas is a **Python library** built on top of NumPy that provides **data structures and data analysis tools** for working with structured data.

* Developed for data wrangling and analysis.
* Enables fast, flexible, and expressive data manipulation.
* Ideal for working with **tabular data**, **time series**, and **matrix data**.

### ➤ Why Use Pandas?

* Easy to clean and manipulate data.
* Simplifies operations like filtering, grouping, and reshaping.
* Integrates well with NumPy, SciPy, Matplotlib, and scikit-learn.

---

## 2.2. 🧱 Key Data Structures

### ➤ Series

A **Series** is a **one-dimensional labeled array** capable of holding any data type.

#### 🧪 Example:

```python
import pandas as pd

s = pd.Series([10, 20, 30, 40], index=['a', 'b', 'c', 'd'])
print(s)
```

**Output:**

```
a    10
b    20
c    30
d    40
dtype: int64
```

* Think of it as a column in Excel.
* It has an **index** and **values**.

---

### ➤ DataFrame

A **DataFrame** is a **two-dimensional labeled data structure** with columns of potentially different types.

#### 🧪 Example:

```python
data = {
    'Name': ['Alice', 'Bob', 'Charlie'],
    'Age': [25, 30, 35],
    'City': ['New York', 'Paris', 'London']
}

df = pd.DataFrame(data)
print(df)
```

**Output:**

```
     Name  Age      City
0   Alice   25  New York
1     Bob   30     Paris
2  Charlie   35    London
```

---

## 2.3. 🏗️ Creating DataFrames

### ➤ From a Dictionary

```python
data = {
    'Product': ['Pen', 'Pencil', 'Eraser'],
    'Price': [10, 5, 3]
}
df = pd.DataFrame(data)
```

### ➤ From a CSV File

```python
df = pd.read_csv('data.csv')  # Ensure 'data.csv' exists in your working directory
```

You can also use:

```python
df = pd.read_csv('data.csv', index_col=0)  # To use the first column as the index
```

---

## 2.4. 🛠️ Essential DataFrame Operations

### ➤ Selecting Data

#### 🔹 Select Column:

```python
df['Age']
```

#### 🔹 Select Multiple Columns:

```python
df[['Name', 'City']]
```

#### 🔹 Select Row by Index:

```python
df.loc[1]      # By label
df.iloc[1]     # By position
```

#### 🔹 Slicing Rows:

```python
df[0:2]  # First 2 rows
```

---

### ➤ Filtering Data with Conditions

#### 🔹 Example:

```python
df[df['Age'] > 25]
```

#### 🔹 Multiple Conditions:

```python
df[(df['Age'] > 25) & (df['City'] == 'London')]
```

---

### ➤ Handling Missing Values (NaN)

#### 🔹 Check for Nulls:

```python
df.isnull()
```

#### 🔹 Drop Missing Values:

```python
df.dropna()
```

#### 🔹 Fill Missing Values:

```python
df.fillna(0)  # Replace NaN with 0
```

---

### ➤ Grouping and Aggregating Data (`groupby`)

#### 🔹 Basic Grouping:

```python
df.groupby('City').mean()
```

#### 🔹 Aggregation:

```python
df.groupby('City')['Age'].agg(['mean', 'max', 'min'])
```

#### 🧪 Example:

```python
data = {
    'City': ['New York', 'Paris', 'New York', 'Paris', 'London'],
    'Sales': [100, 200, 150, 180, 120]
}

df = pd.DataFrame(data)
grouped = df.groupby('City').sum()
print(grouped)
```

**Output:**

```
           Sales
City           
London       120
New York     250
Paris        380
```

---

## ✅ Summary

| Operation             | Function/Method                     |
| --------------------- | ----------------------------------- |
| Create DataFrame      | `pd.DataFrame()` or `pd.read_csv()` |
| Select column         | `df['column']`                      |
| Select row            | `df.loc[]`, `df.iloc[]`             |
| Filter rows           | `df[condition]`                     |
| Handle missing values | `df.dropna()`, `df.fillna()`        |
| Group & Aggregate     | `df.groupby().agg()`                |


