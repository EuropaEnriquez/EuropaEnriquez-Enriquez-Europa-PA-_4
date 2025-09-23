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

________________________________________________________________________
**UPDATE 1**

#**PA 4**

```
import pandas as pd # Used for creating tabular data

df = pd.read_csv('board2.csv') # The board2.csv imports its data to here
df

df['Average'] = df[['Math','Electronics','GEAS','Communication']].mean(axis=1) #0 For column(left to right calc) & 1 for row(top to bottom calculation.) for the average calculation
df

Instru = df.loc[(df['Track']=='Instrumentation') & # It locates Instrumentation students from Luzon with their subjects, specifically GEAS and Electronics, as well as their name and with their grade of their subject, Electronics > 75
       (df['Hometown']=='Luzon') & 
       (df['Electronics'] > 75),
       ['Name','GEAS','Electronics']] #and displays and sorted only with Name, GEAS, and Electronics
Instru #Displays the DataFrame

Mindy = df.loc[(df['Gender']=='Female') & #Like before, but creates a DataFrame named "Mindy" with female students from Mindanao whose Average >= 55, showing Name, Track, Electronics, and Average.
       (df['Hometown']=='Mindanao') & 
       (df['Average'] >=55),
       ['Name','Track','Electronics','Average']] #and displays and sorted only with Name, GEAS, and Electronics
Mindy #Displays the DataFrame

import matplotlib.pyplot as plt   # Imports the matplotlib library for plotting

track_avg = df.groupby('Track')['Average'].mean()   # It locates the Average column, groups rows by Track, and then computes the mean per Track

plt.figure(figsize=(8,5))   #Creates a new figure for the plot with size 8x5 inches
track_avg.plot(kind="bar")  #Plots the track_avg data as a bar chart for visualization
plt.title('Average Scores by Track')   #Sets the title of the chart as  "Average Scores by Track"
plt.ylabel('Average Score')            #Labels the y-axis as "Average Score"
plt.xlabel('Track')                    #Labels the x-axis as "Track"
plt.xticks(rotation = 0)               #This maintains the x-axis labels to be horizontal
plt.show()                             #Displays the bar chart

track_avg = df.groupby('Gender')['Average'].mean()   # It locates the Average column, groups rows by like last before, but by Gender.

plt.figure(figsize=(8,5))   #Creates a figure for the plot with size 8x5 inches
track_avg.plot(kind="bar")  #Plots the track_avg data as a bar chart for visualization
plt.title('Average Scores by Gender')   #Sets the title of the chart as "Average Scores by Gender"
plt.ylabel('Average Score')             #Labels the y-axis as "Average Score"
plt.xlabel('Gender')                    #Labels the x-axis as "Gender"
plt.xticks(rotation = 0)                #This maintains the x-axis labels to be horizontal
plt.show()                              #Displays the bar chart

track_avg = df.groupby('Hometown')['Average'].mean()   # It locates the Average column, groups rows by Hometown, and computes the mean.

plt.figure(figsize=(8,5))   #Creates a new figure for the plot with size 8x5 inches
track_avg.plot(kind="bar")  #Plots the track_avg data as a bar chart for visualization
plt.title('Average Scores by Hometown')   #Sets the title of the chart as "Average Scores by Hometown"
plt.ylabel('Average Score')               #Labels the y-axis as "Average Score"
plt.xlabel('Hometown')                    #Labels the x-axis as "Hometown"
plt.xticks(rotation = 0)                  #This maintains the x-axis labels to be horizontal
plt.show()                                #Displays the bar chart
```

---

The first line,

```
import pandas as pd #Used for creating tabular data
```

import the essential library named pandas, which is used for working with tabular data.

Next,

```
df = pd.read_csv('board2.csv') # The board2.csv imports its data to here
df
```

reads the CSV file named board2.csv and stores it in a pandas DataFrame called df. This makes the dataset available for analysis, filtering, and visualization. Typing df right after loading simply displays the table so that its contents can be visually checked.

Then,

```
df['Average'] = df[['Math','Electronics','GEAS','Communication']].mean(axis=1) #0 For column(left to right calc) & 1 for row(top to bottom calculation.) for the average calculation
df
```

adds a new column called Average to the DataFrame. This column contains the mean score for each student based on their Math, Electronics, GEAS, and Communication grades. The parameter axis=1 specifies that the mean is calculated across each row (left to right) instead of down each column. After this operation, df is displayed again to show the updated table with the new Average column.

The next line,

```
Instru = df.loc[(df['Track']=='Instrumentation') & # It locates Instrumentation students from Luzon with their subjects, specifically GEAS and Electronics, as well as their name and with their grade of their subject, Electronics > 75
       (df['Hometown']=='Luzon') & 
       (df['Electronics'] > 75),
       ['Name','GEAS','Electronics']] #and displays and sorted only with Name, GEAS, and Electronics
Instru #Displays the DataFrame
```

creates a new filtered DataFrame called Instru that contains only students whose Track is Instrumentation, Hometown at Luzon, Electronics and GEAS with a score greater than 70. Typing Instru also displays the result.

Similarly,

```
Mindy = df.loc[(df['Gender']=='Female') & #Like before, but creates a DataFrame named "Mindy" with female students from Mindanao whose Average >= 55, showing Name, Track, Electronics, and Average.
       (df['Hometown']=='Mindanao') & 
       (df['Average'] >=55),
       ['Name','Track','Electronics','Average']] #and displays and sorted only with Name, GEAS, and Electronics
Mindy #Displays the DataFrame
```

creates a filtered DataFrame, but named as called Mindy. This subset contains only female students from Mindanao with an Average score of 55 or higher. The displayed columns include their Name, Track, Electronics score, and Average.

Next, , plots are used for creating plots and charts by using:
```
import matplotlib.pyplot as plt   # Imports the matplotlib library for plotting
```
```
track_avg = df.groupby('Track')['Average'].mean()   # It locates the Average column, groups rows by Track, and then computes the mean per Track
```

This syntax groups the DataFrame by Track and calculates the mean of the Average column for each group. This summary is then visualized with these lines of code:

```
plt.figure(figsize=(8,5))   #Creates a new figure for the plot with size 8x5 inches
track_avg.plot(kind="bar")  #Plots the track_avg data as a bar chart for visualization
plt.title('Average Scores by Track')   #Sets the title of the chart as  "Average Scores by Track"
plt.ylabel('Average Score')            #Labels the y-axis as "Average Score"
plt.xlabel('Track')                    #Labels the x-axis as "Track"
plt.xticks(rotation = 0)               #This maintains the x-axis labels to be horizontal
plt.show()                             #Displays the bar chart
```

which creates a bar chart comparing the average performance of students across different tracks. 

The same procedure is repeated for Gender and Hometown. However, with:

```
track_avg = df.groupby('Gender')['Average'].mean()   # It locates the Average column, groups rows by like last before, but by Gender.

plt.figure(figsize=(8,5))   #Creates a figure for the plot with size 8x5 inches
track_avg.plot(kind="bar")  #Plots the track_avg data as a bar chart for visualization
plt.title('Average Scores by Gender')   #Sets the title of the chart as "Average Scores by Gender"
plt.ylabel('Average Score')             #Labels the y-axis as "Average Score"
plt.xlabel('Gender')                    #Labels the x-axis as "Gender"
plt.xticks(rotation = 0)                #This maintains the x-axis labels to be horizontal
plt.show()                              #Displays the bar chart
```

and Lastly,

```
track_avg = df.groupby('Hometown')['Average'].mean()   # It locates the Average column, groups rows by Hometown, and computes the mean.

plt.figure(figsize=(8,5))   #Creates a new figure for the plot with size 8x5 inches
track_avg.plot(kind="bar")  #Plots the track_avg data as a bar chart for visualization
plt.title('Average Scores by Hometown')   #Sets the title of the chart as "Average Scores by Hometown"
plt.ylabel('Average Score')               #Labels the y-axis as "Average Score"
plt.xlabel('Hometown')                    #Labels the x-axis as "Hometown"
plt.xticks(rotation = 0)                  #This maintains the x-axis labels to be horizontal
plt.show()                                #Displays the bar chart
```

which produces bar charts that display the average scores by gender and by hometown. These visualizations provide a clear comparison of how performance differs across categories and help in spotting patterns in the dataset.

