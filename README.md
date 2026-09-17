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

`import pandas as pd`
      - Imports the Pandas library and assigns it the alias pd

`df = pd.read_excel ("board2.xlsx")`
      - Loads the Excel file named board2.xlsx into a DataFrame variable named df

`df["Average"] = df[["Math", "Electronics", "GEAS", "Communication"]].mean(axis=1)`
      - Calculates the row-wise mean (axis=1) across the specified four subjects and stores the result in a new column named Average

`df['Hometown'] == "Visayas"`
      - Generates a Boolean Series checking which rows have "Visayas" as their Hometown (returns True/False).

`df["Track"] == "Communication"`
      - Generates a Boolean Series checking which rows have "Communication" as their Track
      
`(df["Hometown"] == "Visayas") & (df["Track"] == "Communication")`
      - Combines both conditions using the bitwise & operator to check which rows meet both criteria simultaneously
    
`[["Name", "Gender", "Math", "Electronics", "Average"]]`
      - Represents a Python list of column names used to filter or select specific columns from a DataFrame
    
`VisComm = df[(df["Hometown"] == "Visayas") & (df["Track"] == "Communication")]
                 [["Name", "Gender", "Math", "Electronics", "Average"]]`
      - Filters df for students from Visayas in the Communication track, selects only the specified columns, and assigns the resulting DataFrame to VisComm

## B. VISAYAS FEMALE DATAFRAME
Filters female students originating from Visayas
<table>
  <tr>
    
    (df["Hometown"] == "Visayas") & (df["Gender"] == "Female")
    
    [["Name", "Track", "GEAS", "Electronics", "Average"]]
    
    VisFemale = df[(df["Hometown"] == "Visayas") & (df["Gender"] == "Female")]
                  [["Name", "Track", "GEAS", "Electronics", "Average"]]
                  
    VisFemale[VisFemale["Average"]>=60]
    
  </tr>
</table>

`(df["Hometown"] == "Visayas") & (df["Gender"] == "Female")`
      - Generates a Boolean Series that evaluates to True for rows where the student's hometown is "Visayas" and gender is "Female"
    
`[["Name", "Track", "GEAS", "Electronics", "Average"]]`
      - Represents a list of column names to select from a DataFrame
    
`VisFemale = df[(df["Hometown"] == "Visayas") & (df["Gender"] == "Female")]
               [["Name", "Track", "GEAS", "Electronics", "Average"]]`
      - 
                  
`VisFemale[VisFemale["Average"]>=60]`
      - 

## C. CATEGORY-AVERAGE VISUALIZATION
Computes sample mean averages grouped by categorical features (Track, Gender, Hometown) and displays them in a sub-plotted bar chart figure
<table>
  <tr>
    
    track_mean = df.groupby("Track")["Average"].mean().reset_index()

    gender_mean = df.groupby("Gender")["Average"].mean().reset_index()

    hometown_mean = df.groupby("Hometown")["Average"].mean().reset_index()
    
    print("Mean Average by Track: ")
    display (track_mean)
    
    print("Mean Average by Gender: ")
    display (gender_mean)
    
    print("Mean Average by Hometown: ")
    display(hometown_mean)

    import matplotlib.pyplot as plt

    fig, axes = plt.subplots(1,3,figsize=(18,5))
    
    axes[0].bar(track_mean["Track"], track_mean["Average"])
    axes[0].set_title("Mean Average by Track")
    axes[0].set_xlabel("Track")
    axes[0].set_ylabel("Mean Average")
    
    axes[1].bar(gender_mean["Gender"], gender_mean["Average"])
    axes[1].set_title("Mean Average by Gender")
    axes[1].set_xlabel("Gender")
    axes[1].set_ylabel("Mean Average")
    
    axes[2].bar(hometown_mean["Hometown"], hometown_mean["Average"])
    axes[2].set_title("Mean Average by Hometown")
    axes[2].set_xlabel("Hometown")
    axes[2].set_ylabel("Mean Average")
    
    plt.tight_layout()
    plt.show()

    highest_track = track_mean.loc[track_mean["Average"].idxmax()]
    highest_gender = gender_mean.loc[gender_mean["Average"].idxmax()]
    highest_hometown = hometown_mean.loc[hometown_mean["Average"].idxmax()]

    print(f"1. Among the Track categories, {highest_track["Track"]} has the highest " f"sample mean Average of {highest_track["Average"]: .2f}.")
    print()
    
    print(f"1. Among the Gender categories, {highest_gender["Gender"]} has the highest " f"sample mean Average of {highest_gender["Average"]: .2f}.")
    print()
    
    print(f"1. Among the Hometown categories, {highest_hometown["Hometown"]} has the highest " f"sample mean Average of {highest_hometown["Average"]: .2f}.")
    print()
    
  </tr>
</table>
