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

First `import pandas as pd` imports the panda library and assigns a standard alias pd for easier access. To add, `import matplotlib.pyplot as plt` import matplotlib's module for data vissualization and assigns a standard alis plt.

Then, `df = pd.read_excel('board2.xlsx')` reads an Excel file named board2.xlsx into a Pandas DataFrame named df.

Next, `df['Average'] = (df['Math'] + df['Electronics'] + df['GEAS'] + df['Communication']) / 4` computes the arithmetic mean of four subject scores (Math, Electronics, GEAS, and Communication) for each student and stores the result in a new column called Average.

Then, `vis_comm_filter = (df['Hometown'] == 'Visayas') & (df['Track'] == 'Communication')` creates a boolean filtering condition that checks for rows where Hometown is is exactly 'Visayas' and Track is exactly 'Communication' and stores the data in placholder 'vis_comm_filter'

Then, `VisComm = df[vis_comm_filter][['Name', 'Gender', 'Math', 'Electronics', 'Average']]` applies the boolean filter 'vis_comm_filter' to df to isolate matching students, then selects only five specific columns (Name, Gender, Math, Electronics, Average) and assigns this to a new DataFrame called 'VisComm'.

To continue, `print("Visayas Communication DataFrame")` prints a plain text header above the rendered output.

Then, `display(VisComm)` formats and prints the VisComm DataFrame as the output.

Lastly, `print("Number of rows:", len(VisComm))` 




| Index | Name | Gender | Math | Electronics | Average |
| :--- | :--- | :--- | :--- | :--- | :--- |
| **10** | S11 | Female | 48 | 56 | 54.75 |
| **11** | S12 | Male | 89 | 67 | 76.00 |
| **17** | S18 | Male | 81 | 40 | 63.50 |
| **21** | S22 | Female | 64 | 39 | 62.50 |
| **27** | S28 | Male | 85 | 53 | 67.75 |
