---
title: "Columns and DataType Not Explicitly Set"
disableShare: true
tags: ["generic", "data cleaning", "readability"]
weight: 4
# ShowReadingTime: true	
summary: "Explicitly select columns and set `DataType` in Pandas."
---

### Description

#### Context

In Pandas, all columns are selected by default when a `DataFrame` is imported from a file or other sources. The data type for each column is defined based on the default `dtype` conversion.

#### Problem

If the columns are not selected explicitly, it is not easy for developers to know what to expect in the downstream data schema. If the datatype is not set explicitly, it may silently continue the next step even though the input is unexpected, which may cause errors later. The same applies to other data importing
scenerios.

#### Solution
It is recommended to set the columns and `DataType` explicitly in data processing.


### Type

Generic

### Existing Stage

Data Cleaning

### Effect

Readability

### Example

```diff
### Pandas Column Selection
import pandas as pd
df = pd.read_csv('data.csv')
+ df = df[['col1', 'col2', 'col3']]

### Pandas Set DataType
import pandas as pd
- df = pd.read_csv('data.csv')
+ df = pd.read_csv('data.csv', dtype={'col1': 'str', 'col2': 'int', 'col3': 'float'})
```

### Source:

#### Paper 

#### Grey Literature
- https://github.com/joshlk/pandas_style_guide

#### GitHub Commit

#### Stack Overflow

#### Documentation

