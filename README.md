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
* Imports the Pandas library.
* Pandas is used to read, filter, organize, and analyze tabular data.
* pd is the shorter name used when calling Pandas functions.

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

`Explanation`:

`Code`:
```python
mean_track
```

`Explanation`:

`Code`:
```python
mean_gender
```

`Explanation`:

`Code`:
```python
mean_hometown
```

c.

`Explanation`:

`Code`:
```python
plt.figure(figsize=(15,5))

plt.subplot(1,3,1)
plt.bar(mean_track['Track'],mean_track['Average'])
plt.title('Mean Average by Track')
plt.xlabel('Track')
plt.ylabel('Mean Average Grade')
plt.xticks(rotation=30)
plt.ylim(0,100)

plt.subplot(1,3,2)
plt.bar(mean_gender['Gender'],mean_gender['Average'])
plt.title('Mean Average by Gender')
plt.xlabel('Gender')
plt.ylabel('Mean Average Grade')
plt.ylim(0,100)

plt.subplot(1,3,3)
plt.bar(mean_hometown['Hometown'],mean_hometown['Average'])
plt.title('Mean Average by Hometown')
plt.xlabel('Hometown')
plt.ylabel('Mean Average Grade')
plt.xticks(rotation=30)
plt.ylim(0,100)

plt.tight_layout()
plt.show()
```

d.

`Explanation`:

```text
The Communication track has the highest sample mean Average of 67.98 among the track categories.

Male students have the highest sample mean Average of 67.18 among the gender categories.

Students from Luzon have the highest sample mean Average of 68.08 among the hometown categories.
```


#### READMe file version
SEPT 17, 2026 = Initial Output






























