---
title: "Dataframe Coversion API Misused"
disableShare: true
# ShowReadingTime: true
tags: ["api-specific", "data preparation", "consistency"]
weight: 14
---

### Description

When converting DataFrame to NumPy array, it is better to use `df.to\_numpy()` than `df.values()`. As noted in a post, `df.values()` has inconsistency problem. With `.values` it is unclear whether the returned value would be the actual array, some transformation of it, or one of the Pandas custom arrays. However, `.values` is not deprecated yet. Although the library developers note it as a warning in the documentation, it does not log a warning or error when compiling if we use `.value`. 

### Type

API Specific

### Existing Stage

Data Preparation

### Effect

Consistency

### Example

```diff
### NumPy & Pandas
import numpy as np
import pandas as pd

index = [1, 2, 3, 4, 5, 6, 7]
a = [np.nan, np.nan, np.nan, 0.1, 0.1, 0.1, 0.1]
b = [0.2, np.nan, 0.2, 0.2, 0.2, np.nan, np.nan]
c = [np.nan, 0.5, 0.5, np.nan, 0.5, 0.5, np.nan]
df = pd.DataFrame({'A': a, 'B': b, 'C': c}, index=index)
df = df.rename_axis('ID')
- arr = df.values
+ arr = df.to_numpy()
```

### Source:

#### Paper 
#### Grey Literature

#### GitHub Commit

#### Stack Overflow
- https://stackoverflow.com/questions/13187778/convert-pandas-dataframe-to-numpy-array/54508052#54508052

#### Documentation

