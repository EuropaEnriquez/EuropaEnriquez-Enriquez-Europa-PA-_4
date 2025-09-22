#**PA 4**

```
import pandas as pd
import matplotlib.pyplot as plt

df = pd.read_csv('board2.csv')
df

df['Average'] = df[['Math','Electronics','GEAS','Communication']].mean(axis=1)
df

Instru = df.loc[(df['Track']=='Instrumentation') & 
       (df['Hometown']=='Luzon') & 
       (df['Electronics'] > 70),
       ['Name','GEAS','Electronics']]
Instru

Mindy = df.loc[(df['Gender']=='Female') &
       (df['Hometown']=='Mindanao') & 
       (df['Average'] >=55),
       ['Name','Track','Electronics','Average']]
Mindy

track_avg = df.groupby('Track')['Average'].mean()

plt.figure(figsize=(8,5))
track_avg.plot(kind="bar")
plt.title('Average Scores by Track')
plt.ylabel('Average Score')
plt.xlabel('Track')
plt.xticks(rotation = 0)
plt.show()

track_avg = df.groupby('Gender')['Average'].mean()

plt.figure(figsize=(8,5))
track_avg.plot(kind="bar")
plt.title('Average Scores by Gender')
plt.ylabel('Average Score')
plt.xlabel('Gender')
plt.xticks(rotation = 0)
plt.show()

track_avg = df.groupby('Hometown')['Average'].mean()

plt.figure(figsize=(8,5))
track_avg.plot(kind="bar")
plt.title('Average Scores by Hometown')
plt.ylabel('Average Score')
plt.xlabel('Hometown')
plt.xticks(rotation = 0)
plt.show()
```

---

The first two lines,

```
import pandas as pd
import matplotlib.pyplot as plt
```

import two essential libraries: pandas, which is used for working with tabular data, and matplotlib.pyplot, which is used for creating plots and charts. Assigning pandas to the alias pd and pyplot to plt is a common convention that makes commands shorter and easier to type.

Next,

```
df = pd.read_csv('board2.csv')
df
```

reads the CSV file named board2.csv and stores it in a pandas DataFrame called df. This makes the dataset available for analysis, filtering, and visualization. Typing df right after loading simply displays the table so that its contents can be visually checked.

Then,

```
df['Average'] = df[['Math','Electronics','GEAS','Communication']].mean(axis=1)
df
```

adds a new column called Average to the DataFrame. This column contains the mean score for each student based on their Math, Electronics, GEAS, and Communication grades. The parameter axis=1 specifies that the mean is calculated across each row (left to right) instead of down each column. After this operation, df is displayed again to show the updated table with the new Average column.

The next line,

```
Instru = df.loc[(df['Track']=='Instrumentation') & 
       (df['Hometown']=='Luzon') & 
       (df['Electronics'] > 70),
       ['Name','GEAS','Electronics']]
Instru
```

creates a new filtered DataFrame called Instru that contains only students whose Track is Instrumentation, Hometown at Luzon, Electronics and GEAS with a score greater than 70. Typing Instru also displays the result.

Similarly,

```
Mindy = df.loc[(df['Gender']=='Female') &
       (df['Hometown']=='Mindanao') & 
       (df['Average'] >=55),
       ['Name','Track','Electronics','Average']]
Mindy
```

creates a filtered DataFrame, but named as called Mindy. This subset contains only female students from Mindanao with an Average score of 55 or higher. The displayed columns include their Name, Track, Electronics score, and Average.

Next,

```
track_avg = df.groupby('Track')['Average'].mean()
```

This syntax groups the DataFrame by Track and calculates the mean of the Average column for each group. This summary is then visualized with these lines of code:

```
plt.figure(figsize=(8,5))
track_avg.plot(kind="bar")
plt.title('Average Scores by Track')
plt.ylabel('Average Score')
plt.xlabel('Track')
plt.xticks(rotation = 0)
plt.show()
```

which creates a bar chart comparing the average performance of students across different tracks. 

The same procedure is repeated for Gender and Hometown. However, with:

```
track_avg = df.groupby('Gender')['Average'].mean()

plt.figure(figsize=(8,5))
track_avg.plot(kind="bar")
plt.title('Average Scores by Gender')
plt.ylabel('Average Score')
plt.xlabel('Gender')
plt.xticks(rotation = 0)
plt.show()
```

and Lastly,

```
track_avg = df.groupby('Hometown')['Average'].mean()

plt.figure(figsize=(8,5))
track_avg.plot(kind="bar")
plt.title('Average Scores by Hometown')
plt.ylabel('Average Score')
plt.xlabel('Hometown')
plt.xticks(rotation = 0)
plt.show()
```

which produces bar charts that display the average scores by gender and by hometown. These visualizations provide a clear comparison of how performance differs across categories and help in spotting patterns in the dataset.
