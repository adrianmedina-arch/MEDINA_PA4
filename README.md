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
* import pandas as pd imports Pandas for reading, filtering, and analyzing the dataset.
* pd is the shorter alias for Pandas.
* import matplotlib.pyplot as plt imports Pyplot for creating graphs.

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
* .shape returns the dimensions of the DataFrame.
* .shape[0] returns only the number of rows.

`Code`:
```python
VisComm.shape[0]
```

### B. VISAYAS FEMALE DATAFRAME

`Explanation`:
* df['Hometown'] == 'Visayas' selects students from Visayas.
* df['Gender'] == 'Female' selects female students.
* The & operator requires both conditions to be true.
* Only Name, Track, GEAS, Electronics, and Average are retained.
* The resulting DataFrame is stored in VisFemale.

`Code`:
```python
VisFemale=df.loc[(df['Hometown'] == 'Visayas') & (df['Gender'] == 'Female'), ['Name','Track','GEAS','Electronics','Average']]
VisFemale
```

`Explanation`:
* VisFemale['Average']>=60 checks which students have an Average equal to or greater than 60.
* .loc[] displays only the rows that satisfy the condition.

`Code`:
```python
VisFemale.loc[VisFemale['Average']>=60]
```

### C. CATEGORY-AVERAGE VISUALIZATION

a.

`Explanation`:
* .groupby('Track') groups students according to their track.
* .groupby('Gender') groups students according to their gender.
* .groupby('Hometown') groups students according to their hometown.
* ['Average'].mean() calculates the mean Average for every category.
* .reset_index() converts the grouped category back into a regular column.

`Code`:
```python
mean_track = df.groupby("Track")["Average"].mean().reset_index()
mean_gender = df.groupby("Gender")["Average"].mean().reset_index()
mean_hometown = df.groupby("Hometown")["Average"].mean().reset_index()
```

b. 

`Explanation`:
* Writing mean_track displays the mean Average for each track.

`Code`:
```python
mean_track
```

`Explanation`:
* Writing mean_gender displays the mean Average for each gender.

`Code`:
```python
mean_gender
```

`Explanation`:
* Writing mean_hometown displays the mean Average for each hometown.

`Code`:
```python
mean_hometown
```

c.

`Explanation`:
* plt.figure(figsize=(15,5)) creates the figure and sets its size.
* plt.subplot(1,3,1) places the Track graph in the first position.
* plt.subplot(1,3,2) places the Gender graph in the second position.
* plt.subplot(1,3,3) places the Hometown graph in the third position.
* plt.bar() creates each bar chart using the categories and their mean averages.
* plt.title() gives each graph a title.
* plt.xlabel() and plt.ylabel() label the axes.
* plt.xticks(rotation=30) rotates long category labels for readability.
* plt.ylim(0,100) gives all three graphs the same scale.
* plt.tight_layout() prevents the labels and graphs from overlapping.
* plt.show() displays the completed figure.

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






























