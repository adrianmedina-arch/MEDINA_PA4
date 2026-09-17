# EXPERIMENT 4: DATA WRANGLING AND DATA VISUALIZATION
## Adrian Gabriel M. Medina | 2ECE-C
## 17/09/2026

## I. Intended Learning Outcomes
At the end of this laboratory activity, the student should be able to:
1. filter tabular data using several categorical and numerical conditions;
2. construct focused DataFrames by selecting relevant features;
3. summarize the relationship between categorical features and a numerical variable; and
4. communicate a data comparison using clear and correctly labeled plots.

`Explanation`:

```python
import pandas as pd
```

`Explanation`:
```python
import matplotlib.pyplot as plt
```

## II. Programing Problems

### A. VISAYAS COMMUNICATION DATAFRAME

`Explanation`:

`Code`:
```python
original_df = pd.read_excel('board2.xlsx')
df = original_df.copy()
df['Average'] = df[['Math','Electronics','GEAS','Communication']].mean(axis=1)
```
`Explanation`:

`Code`:
```python
VisComm = df.loc[(df['Hometown'] == 'Visayas') & (df['Track'] == 'Communication'), ['Name', 'Gender', 'Math', 'Electronics', 'Average']]
VisComm
```
`Explanation`:

`Code`:
```python
VisComm.shape[0]
```

### B. VISAYAS FEMALE DATAFRAME

`Explanation`:

`Code`:
```python
VisFemale=df.loc[(df['Hometown'] == 'Visayas') & (df['Gender']=='Female'), ['Name','Track','GEAS','Electronics','Average']]
VisFemale
```

`Explanation`:

`Code`:
```python
VisFemale.loc[VisFemale['Average']>=60]
```

### C. CATEGORY-AVERAGE VISUALIZATION

a.

`Explanation`:

`Code`:
```python
mean_track = df.groupby("Track")["Average"].mean().reset_index()
mean_gender = df.groupby("Gender")["Average"].mean().reset_index()
mean_hometown = df.groupby("Hometown")["Average"].mean().reset_index()
```

b. 








































