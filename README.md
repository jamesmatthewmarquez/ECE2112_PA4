# ECE2112_PA4: Data Wrangling and Data Visualization
## I. Intended Learning Outcomes
1. filter tabular data using several categorical and numerical conditions
2. construct focused DataFrames by selecting relevant features
3. summarize the relationship between categorical features and a numerical variable
4. communicate a data comparison using clear and correctly labeled plots
## II. Instructions
Use the same ECE Board Exam 2 dataset supplied for Experiment 4. Work in a Jupyter Notebook
using Pandas and a Python plotting library used in class. Use the dataset’s existing column labels,
including Name, Gender, Track, Hometown, Math, GEAS, Electronics, and Average.

• Derive all tables and plot values from the dataset. Do not manually type rows, category means, or
plotted values

• When applying more than one condition, make every condition explicit in the filtering expression

• Keep the original DataFrame unchanged

• Every graph must have a title, axis labels, readable category labels, and a consistent scale appro-
private to the data

## A. VISAYAS COMMUNICATION DATAFRAME
Filters students originating from Visayas whose specialization is Communication.
<table>
  <tr>
    
    import pandas as pd
    
    df = pd.read_excel ("board2.xlsx")
    
    df["Average"] = df[["Math", "Electronics", "GEAS", "Communication"]].mean(axis=1)
    
    df['Hometown'] == "Visayas"
    
    df["Track"] == "Communication"
    
    (df["Hometown"] == "Visayas") & (df["Track"] == "Communication")
    
    [["Name", "Gender", "Math", "Electronics", "Average"]]
    
    VisComm = df[(df["Hometown"] == "Visayas") & (df["Track"] == "Communication")]
                [["Name", "Gender", "Math", "Electronics", "Average"]]
    
  </tr>
</table>
