# ECE2112_PA4
Created by: Montillana, Jasmine Marie P. | 2ECE-B

This repository contains the completed Programming Assignment 4 for ECE2112: Advance Computer Programming Algorithms. The project demonstrates tabular data filtering, feature selection, group aggregation, and clear visualization using Pandas and Matplolib. 

## Overview & Requirements
The primary objective of this experiment is to perform data wrangling and visualization on the **ECE Board Exam** dataset (`board.xlsx`), observing the required data analysis standards:

**Explicit Condition Filtering:** Apply multi-criteria boolean indexing without modifying the raw dataset. 

**Feature Selection:** Filter and extract relevant columns in exact specified orders.

**Averages:** Compute group mean across multiple categorical dimensions. 

**Visualization:** Construct a 3-panel comparative bar chart using custom styling, readable axis labels, and identical vertical scales for direct visual assessment. 


## A. Visayas Communication DataFrame
**Objective:** Create DataFrame named Viscomm containing students whose Hometown is `Visayas` and whose Track is `Communication`. Retain only the following columns in order: `Name`,`Gender`,`Math`,`Electronics`,`Average`.

**Key functions and methods used in this problem:**
Row-wise Averages (`.mean(axis=1)`): Computes the arithmetic mean across subject columns ('Math','Electronics', 'GEAS', 'Communication') for each row to derive the Average. 

Compound Boolean Indexing (`&`): Combines explicit condition masks `(df['Hometown']=='Visayas')&(df['Track']=='Communication')`

Column Indexing (`[[...]]`): Filters and reorders columns to project only the relevant features. 

**Below is the complete Python code implementation for this problem:**
````
df['Average']= df[['Math','Electronics', 'GEAS', 'Communication']].mean(axis=1)

Viscomm = df[(df['Hometown']=='Visayas')&(df['Track']=='Communication')][['Name','Gender','Math','Electronics','Average']]
Viscomm
````

## B. Visayas Female DataFrame
**Objective:**
**Key functions and methods used in this problem:**
**Below is the complete Python code implementation for this problem:**
````
````

## Category-Average Visualization
**Objective:**
**Key functions and methods used in this problem:**
**Below is the complete Python code implementation for this problem:**
````
````
**README File Version History**
September 17, 2026

