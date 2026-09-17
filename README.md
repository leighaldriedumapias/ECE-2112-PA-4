Made by: Leigh Aldrie Dumapias | 2ECE-D

This repository contains the Programming Assignment 4 assigned for ECE2112 - Advanced Computer Programming & Algorithms for A.Y. 2026 - 2027. The project includes three specific Python problems intended for NumPy and Matplotlib utilization in Python.

## A. Visayas Communication DataFrame

Objective:

Create a a DataFrame named VisComm containing students whose Hometown is Visayas and whose Track
is Communication. Retain only these columns, in the stated order:

Name, Gender, Math, Electronics, Average

Display the resulting DataFrame and its number of rows. Both filtering conditions must be applied to
the source dataset before the columns are selected.

Code:

```python
import pandas as pd
import matplotlib.pyplot as plt

df = pd.read_excel('board2.xlsx')
df

df['Average'] = (df['Math'] + df['Electronics'] + df['GEAS'] + df['Communication']) / 4

vis_comm_filter = (df['Hometown'] == 'Visayas') & (df['Track'] == 'Communication')
VisComm = df[vis_comm_filter][['Name', 'Gender', 'Math', 'Electronics', 'Average']]


print("Visayas Communication DataFrame")
display(VisComm)
print("Number of rows:", len(VisComm))
```

First `import pandas as pd` imports the panda library and assigns a standard alias pd for easier access. To add, `import matplotlib.pyplot as plt` import matplotlib's module for data vissualization and assigns a standard alias plt.

Then, `df = pd.read_excel('board2.xlsx')` reads an Excel file named board2.xlsx into a Pandas DataFrame named df.

Next, `df['Average'] = (df['Math'] + df['Electronics'] + df['GEAS'] + df['Communication']) / 4` computes the arithmetic mean of four subject scores (Math, Electronics, GEAS, and Communication) for each student and stores the result in a new column called Average.

Then, `vis_comm_filter = (df['Hometown'] == 'Visayas') & (df['Track'] == 'Communication')` creates a boolean filtering condition that checks for rows where Hometown is is exactly 'Visayas' and Track is exactly 'Communication' and stores the data in placholder 'vis_comm_filter'

Then, `VisComm = df[vis_comm_filter][['Name', 'Gender', 'Math', 'Electronics', 'Average']]` applies the boolean filter 'vis_comm_filter' to df to isolate matching students, then selects only five specific columns (Name, Gender, Math, Electronics, Average) and assigns this to a new DataFrame called 'VisComm'.

To continue, `print("Visayas Communication DataFrame")` prints a plain text header above the rendered output.

Then, `display(VisComm)` formats and prints the VisComm DataFrame as the output.

Lastly, `print("Number of rows:", len(VisComm))` calculates and prints the total row count of the filtered DataFrame using len()


Produced Data:

| Index | Name | Gender | Math | Electronics | Average |
| :--- | :--- | :--- | :--- | :--- | :--- |
| **10** | S11 | Female | 48 | 56 | 54.75 |
| **11** | S12 | Male | 89 | 67 | 76.00 |
| **17** | S18 | Male | 81 | 40 | 63.50 |
| **21** | S22 | Female | 64 | 39 | 62.50 |
| **27** | S28 | Male | 85 | 53 | 67.75 |

## B. Visayas Female DataFrame

Objective: 

To create a DataFrame named VisFemale containing students whose Hometown is Visayas and
whose Gender is Female. Retain only:

Name, Track, GEAS, Electronics, Average

Display VisFemale. Then display only the rows of VisFemale whose Average is at least 60. Do not
overwrite VisFemale when performing this second filter.

Code:

```python
import pandas as pd
import matplotlib.pyplot as plt

df = pd.read_excel('board2.xlsx')
df

df['Average'] = (df['Math'] + df['Electronics'] + df['GEAS'] + df['Communication']) / 4

vis_female = (df['Hometown'] == 'Visayas') & (df['Gender'] == 'Female')

VisFemale = df[vis_female][['Name', 'Track', 'GEAS', 'Electronics', 'Average']]

print("Visayas Female DataFrame")
display(VisFemale)

print("\n Visayas Female DataFrame (with average of 60)")
display(VisFemale[VisFemale['Average'] >= 60])
```

First `import pandas as pd` imports the panda library and assigns a standard alias pd for easier access. To add, `import matplotlib.pyplot as plt` import matplotlib's module for data vissualization and assigns a standard alias plt.

Then, `df = pd.read_excel('board2.xlsx')` reads an Excel file named board2.xlsx into a Pandas DataFrame named df.

Next, `df['Average'] = (df['Math'] + df['Electronics'] + df['GEAS'] + df['Communication']) / 4` computes the arithmetic mean of four subject scores (Math, Electronics, GEAS, and Communication) for each student and stores the result in a new column called Average.

Then, `vis_female = (df['Hometown'] == 'Visayas') & (df['Gender'] == 'Female')` creates a filtering condition that selects rows where Hometown is 'Visayas' and Gender is 'Female' ans stores the dat in 'vis_female'

Next, `VisFemale = df[vis_female][['Name', 'Track', 'GEAS', 'Electronics', 'Average']]` filters rows & selects columns: Applies the boolean condition to filter df, keeping only female students from Visayas. It then extracts only specific columns (Name, Track, GEAS, Electronics, and Average) to create the new DataFrame VisFemale.

To continue,

`print("Visayas Female DataFrame")`

`display(VisFemale)`

Prints a title header 'Visayas Female DataFrame', then displays the full VisFemale table through `display(VisFemale)` as the output.

Lastly,

`print("\n Visayas Female DataFrame (with average of 60)")`

`display(VisFemale[VisFemale['Average'] >= 60])`

Prints a second title header 'Visayas Female DataFrame (with average of 60)' and displays a filtered subset of VisFemale containing only students whose Average score is 60 or higher.

Produced Data:

Visayas Female DataFrame

| Index | Name | Gender | Math | Electronics | Average |
| :--- | :--- | :--- | :--- | :--- | :--- |
| **5** | S6 | Female | — | 45 | 75.50 |
| **10** | S11 | Female | — | 56 | 54.75 |
| **20** | S21 | Female | — | 51 | 68.50 |
| **21** | S22 | Female | — | 39 | 62.50 |
| **23** | S24 | Female | — | 45 | 57.75 |
| **25** | S26 | Female | — | 47 | 65.75 |

Visayas Female DataFrame (with average of 60)

| Index | Name | Gender | Math | Electronics | Average |
| :--- | :--- | :--- | :--- | :--- | :--- |
| **5** | S6 | Female | — | 45 | 75.50 |
| **20** | S21 | Female | — | 51 | 68.50 |
| **21** | S22 | Female | — | 39 | 62.50 |
| **25** | S26 | Female | — | 47 | 65.75 |

## C. Category Average Visualization

Objective:

Examine how the recorded Average differs across the three categorical features Track, Gender, and Hometown.

a. For each feature, compute the mean of Average for every category using Pandas.

b. Display the three summary tables.

c. Create one figure containing three bar charts: mean Average by Track, by Gender, and by
Hometown.

d. Below the figure, write three concise statements identifying the category with the highest sample
mean for each feature.

Interpretation rule: Describe the observed dataset only. A difference in group means does not, by
itself, establish that a feature causes a higher board-exam score.

Code:

```python
import pandas as pd
import matplotlib.pyplot as plt

df = pd.read_excel('board2.xlsx')
df

df['Average'] = (df['Math'] + df['Electronics'] + df['GEAS'] + df['Communication']) / 4

track_avg = df.groupby('Track')['Average'].mean().reset_index()
gender_avg = df.groupby('Gender')['Average'].mean().reset_index()
hometown_avg = df.groupby('Hometown')['Average'].mean().reset_index()

print("Mean Average by Track:")
display(track_avg)

print("\nMean Average by Gender:")
display(gender_avg)

print("\nMean Average by Hometown:")
display(hometown_avg)

plt.figure(figsize=(15, 5))

# Plot for Track
plt.subplot(1, 3, 1)
plt.bar(track_avg['Track'], track_avg['Average'])
plt.title('Mean Average by Track')
plt.ylim(0, 100)

# Plot for Gender
plt.subplot(1, 3, 2)
plt.bar(gender_avg['Gender'], gender_avg['Average'])
plt.title('Mean Average by Gender')
plt.ylim(0, 100)

# Plot for Hometown
plt.subplot(1, 3, 3)
plt.bar(hometown_avg['Hometown'], hometown_avg['Average'])
plt.title('Mean Average by Hometown')
plt.ylim(0, 100)

plt.show()

print("For Track dataset, students in the Communication track recorded the highest sample mean average grade (67.98)")
print("\nFor Gender dataset, male students recorded the highest sample mean average grade (67.18).")
print("\nFor Hometown dataset, students from Luzon recorded the highest sample mean average grade (68.08)")
```

First `import pandas as pd` imports the panda library and assigns a standard alias pd for easier access. To add, `import matplotlib.pyplot as plt` import matplotlib's module for data vissualization and assigns a standard alias plt.

Then, `df = pd.read_excel('board2.xlsx')` reads an Excel file named board2.xlsx into a Pandas DataFrame named df.

Next, `df['Average'] = (df['Math'] + df['Electronics'] + df['GEAS'] + df['Communication']) / 4` computes the arithmetic mean of four subject scores (Math, Electronics, GEAS, and Communication) for each student and stores the result in a new column called Average.

Then,

`track_avg = df.groupby('Track')['Average'].mean().reset_index()`

`gender_avg = df.groupby('Gender')['Average'].mean().reset_index()`

`hometown_avg = df.groupby('Hometown')['Average'].mean().reset_index()`

each of these groups the dataset by categorical variables (Track, Gender, and Hometown) calculates the mean average score for each of the three categories, and resets the index the keep the DataFrames clean. Placeholder names were named as track_avg, gender_avg, hometown_avg, respectively, as to match for graph plotting.

Next, 

`print("Mean Average by Track:")`

`display(track_avg)`

`print("\nMean Average by Gender:")`

`display(gender_avg)`

`print("\nMean Average by Hometown:")`

`display(hometown_avg)`

display each of the summary tables and prints descriptive headers respectively and renders each grouped average as outputs.

Then, `plt.figure(figsize=(15, 5))` initializes and sets up a wide figure canvas measuring 15x5 inches to accomodate the the three charts that will put side-by-side

Next, 

`plt.subplot(1, 3, 1)`

`plt.bar(track_avg['Track'], track_avg['Average'])`

`plt.title('Mean Average by Track')`

`plt.ylim(0, 100)`

is the first bar section (for Track) which has `plt.subplot(1, 3, 1)` which focuses on the 1st position in a 1-row by 3-column grid. Then  plots a bar chart comparing tracks against average scores through `plt.bar(track_avg['Track'], track_avg['Average'])`, adds a specific title `plt.title('Mean Average by Track')`, and locks the y-axis range from 0 to 100 with `plt.ylim(0, 100)`.

To continue, 

`plt.subplot(1, 3, 2)`

`plt.bar(gender_avg['Gender'], gender_avg['Average'])`

`plt.title('Mean Average by Gender')`

`plt.ylim(0, 100)`

 is the second bar section (for Gender) which has `plt.subplot(1, 3, 2)` which focuses on the 2nd position in the grid. Then plots a bar chart comparing tracks against average scores through `plt.bar(gender_avg['Gender'], gender_avg['Average'])`, adds a specific title `plt.title('Mean Average by Gender')`, and locks the y-axis range from 0 to 100 with `plt.ylim(0, 100)`.

Next, 

`plt.subplot(1, 3, 3)`

`plt.bar(hometown_avg['Hometown'], hometown_avg['Average'])`

`plt.title('Mean Average by Hometown')`

`plt.ylim(0, 100)`

is the third bar section (for Track) has `plt.subplot(1, 3, 3)` which focuses on the 3rd position in the grid. Then plots average scores grouped by student hometown through `plt.bar(hometown_avg['Hometown'], hometown_avg['Average'])`, adds a specific title `plt.title('Mean Average by Hometown')`, and again, locks the y-axis range from 0 to 100 with `plt.ylim(0, 100)`.

Next, `plt.show()` simultaneously renders all three plotted bar charts onto the screen as outputs

Lastly, 

`print("For Track dataset, students in the Communication track recorded the highest sample mean average grade (67.98)")`

`print("\nFor Gender dataset, male students recorded the highest sample mean average grade (67.18).")`

`print("\nFor Hometown dataset, students from Luzon recorded the highest sample mean average grade (68.08)")`

Displays written statements summarizing which groups scored the highest in each category based on the means calculated.

## README File Version History:

September 17, 2026 - Initial Code and README output uploaded; also format and details tweaks


 
