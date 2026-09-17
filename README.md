# ECE2112_PA4
Created by: Montillana, Jasmine Marie P. | 2ECE-B

This repository contains the completed Programming Assignment 4 for ECE2112: Advance Computer Programming Algorithms. The project demonstrates tabular data filtering, feature selection, group aggregation, and clear visualization using Pandas and Matplolib. 

## Overview & Requirements
The primary objective of this experiment is to perform data wrangling and visualization on the **ECE Board Exam** dataset (`board.xlsx`), observing the required data analysis standards:

**Explicit Condition Filtering:** Apply multi-criteria boolean indexing without modifying the raw dataset. 

**Feature Selection:** Filter and extract relevant columns in exact specified orders.

**Aggregation:** Compute group mean across multiple categorical dimensions. 

**Visualization:** Construct a 3-panel comparative bar chart using custom styling, readable axis labels, and identical vertical scales for direct visual assessment. 


## A. Visayas Communication DataFrame
**Objective:** Create DataFrame named Viscomm containing students whose Hometown is `Visayas` and whose Track is `Communication`. Retain only the following columns in order: `Name`,`Gender`,`Math`,`Electronics`,`Average`.

**Key functions and methods used in this problem:**

Row-wise Agregation (`.mean(axis=1)`): Computes the arithmetic mean across subject columns ('Math','Electronics', 'GEAS', 'Communication') for each row to derive the Average. 

Compound Boolean Indexing (`&`): Combines explicit condition masks `(df['Hometown']=='Visayas')&(df['Track']=='Communication')`

Column Indexing (`[[...]]`): Filters and reorders columns to project only the relevant features. 

**Below is the complete Python code implementation for this problem:**
````
df['Average']= df[['Math','Electronics', 'GEAS', 'Communication']].mean(axis=1)

Viscomm = df[(df['Hometown']=='Visayas')&(df['Track']=='Communication')][['Name','Gender','Math','Electronics','Average']]
Viscomm
````

## B. Visayas Female DataFrame
**Objective:** Filter female students (Gender == 'Female') from `Visayas`, Retain: `Name`, `Track`, `GEAS`, `E;ectronics`, `Average`. Additionally dsiplay a secondary non-destructive view showing only students with an `Average >=60`. 

**Key functions and methods used in this problem:**

Multi-conditioning Filtering: Filters female students residing in Visayas using `(df['Hometown']=='Visayas')&(df['Gender']=='Female')`

Secondary Filtering: Queries the resulting DataFrame `VisFemale[VisFemale['Average'] >= 60])` witout ovewrwriting the master `VisFemale` variable. 

**Below is the complete Python code implementation for this problem:**
````
VisFemale = df[(df['Hometown']=='Visayas')&(df['Gender']=='Female')][['Name','Track','GEAS','Electronics','Average']]
display(VisFemale)

display(VisFemale[VisFemale['Average'] >= 60])
````

## Category-Average Visualization
**Objective:** Analyze performance across categorical dimensions (`Track`, `Gender`, `Hometown`) by aggregating mean score values and rendering side-by-side comparative bar charts.

**Key functions and methods used in this problem:**
`df.groupby('Category')['Average'].mean()`: Groups records by categorical features and calculates arithmetic means. 

`plt.subplots(1, 3, sharey=True)`: Generates a 1x3 grid of subplots sharing aunified Y-axis scale (`0` to `70+`) for direct visual comparability. 

Subplot Customizations: Adds distinctive color paletters (`salmon`, `violet`, `pink`), rotated tick labels, and structured title/axis annotations. 

**Below is the complete Python code implementation for this problem:**
````
fig, axes = plt.subplots(1, 3, figsize=(15, 5), sharey=True)
axes[0].bar(track_mean.index, track_mean.values, color='salmon')
axes[0].set_title('Mean Average by Track')
axes[0].set_xlabel('Track')
axes[0].set_ylabel('Mean Average Score')
axes[0].tick_params(axis='x', labelrotation=15)

axes[1].bar(gender_mean.index, gender_mean.values, color='violet')
axes[1].set_title('Mean Average by Gender')
axes[1].set_xlabel('Gender')

axes[2].bar(hometown_mean.index, hometown_mean.values, color='pink')
axes[2].set_title('Mean Average by Hometown')
axes[2].set_xlabel('Hometown')

plt.tight_layout()
plt.show()

# Interpretation statements based on computed data
print('1. Communication had the highest sample mean Average among all the tracks.')
print('2. Male students had the highest sample mean Average among genders.')
print('3. Across regions, Luzon recorded the highest sample mean Average.')
````

Category Summary Data:
Track Means: Coomunication (67.975), | Microelectronics (67.5000) | Instrumenttation (65.225)
Gender Means: Male (67.183) | Female (66.617)
Hometown Means: Luzon (68.083) | Mindanao (66.679) | Visayas (65.750)

Data Intrepretation Statements:
```
print('1. Communication had the highest sample mean Average among all the tracks.')
print('2. Male students had the highest sample mean Average among genders.')
print('3. Across regions, Luzon recorded the highest sample mean Average.')
```
**README File Version History**
September 17, 2026 Initial Commit & Full Documentation for Experiment 4

