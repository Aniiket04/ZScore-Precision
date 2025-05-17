# ZScore-Precision

## Project Overview
**Project Title : ZScore-Precision**
The goal of this project is to involve analyzing height data using Z-scores.

## Objectives
Z-scores standardize data points relative to their population mean and standard deviation, making it easier to:
1. **Identify Anomalies**: Detect outliers in the height dataset, such as unusually short or tall individuals.
2. **Statistical Insights**: Gain insights into the distribution of heights and understand how individuals deviate from the mean.
3. **Predictive Analysis**: Use normalized height data for prediction models, like estimating health-related metrics.

## Project Structure

### 1. Importing Libraries
The notebook begins by importing essential Python libraries, including:
pandas for data manipulation
numpy for numerical operations
seaborn for data visualization
```python
import pandas as pd
import numpy as np
import seaborn as sn
```

### 2. Loading the Dataset
The given dataset is loaded using pandas.read_csv(). This dataset contains data about heights and weights of different individuals
```python
df=pd.read_csv("Height.csv")
df
```

### 3. Data processing
```python
df=df.drop("Weight(Pounds)",axis="columns")
df
df=df.drop("Index",axis="columns")
df
```
Drop the weights and index columns from the DataFrame

```python
df.describe()
```
The df.describe() method provides a summary of key statistical metrics for numerical columns in the DataFrame it typically shows :
Metric	Description
Count	: Number of non-null (non-NaN) entries in the column.
Mean :	Average of the column values.
Std :	Standard deviation, a measure of spread.
Min	: Minimum value in the column.
25%	First quartile (Q1) : Value below which 25% of the data falls.
50%	Median (Q2) : Middle value of the data.
75%	Third quartile (Q3) : Value below which 75% of the data falls.
Max : Maximum value in the column.

### 4. Ploting the graph
Create a histogram of the Height column from the DataFrame df using Seaborn.
```python
sn.histplot(df.Height,kde=True)
```
The kde=True option overlays a Kernel Density Estimate (KDE) curve to show the distribution shape smoothly.

### 5. Calculations
1.
```python
mean=df.Height.mean()
mean
```
Calculates the mean (average) of the values in the Height column of a DataFrame named df in Python using the pandas library.

2.
```python
std=df.Height.std()
std
```
Calculates the standard deviation of the values in the Height column of a pandas DataFrame df.

3.
```python
mean-3*std
```
This code snippet calculates a value three standard deviations below the mean.

4.
```python
mean+3*std
```
This code snippet calculates a value three standard deviations above the mean.

5.
```python
count=df[df.Height<62.28807728318317]
count

```
This code snippet filters the rows in the DataFrame df where the values in the Height column are less than 62.28807728318317.

6.
```python
count.describe()
count2=df[df.Height>73.6981499104168]
count2.describe()
```
This code snippet filters the rows in the DataFrame df where the values in the Height column are greater than 73.6981499104168.

7.
```python
outlier=df[(df.Height>73.6981499104168)|(df.Height<62.28807728318317)]
outlier.describe()
```
This code snippet creates a new DataFrame outlier containing rows where the Height column is an outlier. Specifically, it filters rows where:
a. The Height is greater than 73.6981499104168 (upper bound), or
b. The Height is less than 62.28807728318317 (lower bound).

8.
```python
no_outlier=df[(df.Height<73.6981499104168)&(df.Height>62.28807728318317)]
no_outlier
no_outlier.describe()
```
This code snippet creates a new DataFrame no_outlier containing rows where the Height column values fall within the specified range (i.e., not outliers). Specifically, it filters rows where:
a. The Height is less than 73.6981499104168 (upper bound), and
b. The Height is greater than 62.28807728318317 (lower bound).

9.
```python
(64.54826-mean)/std
```
This code snippet calculates the z-score for the value 64.54826 in relation to the Height column of the DataFrame.

10.
```python
from scipy.stats import zscore
outlier.apply(zscore)<3
```
This code snippet aims to calculate the z-scores of the columns in the outlier DataFrame and checks if each z-score is less than 3.

## Conclusion
By analyzing the Height data using statistical measures, we calculated the mean and standard deviation to understand the central tendency and spread of the dataset. Using these, we identified potential outliers as values lying beyond three standard deviations from the mean (both above and below).
Values less than mean - 3*std or greater than mean + 3*std were considered outliers.
We successfully filtered the dataset into two groups:
a. Outliers — heights significantly different from the typical range.
b. Non-outliers — heights within the expected range of variation.
To further validate these outliers, we computed the z-scores, which standardize data points based on the mean and standard deviation. Data points with an absolute z-score greater than 3 typically indicate strong outliers.This method provides a robust, statistically sound approach to detect and handle outliers in your data, enabling cleaner data analysis and more reliable results in any subsequent modeling or interpretation.

## Author - Aniket Pal
This project is part of my portfolio, showcasing the machine learning skills essential for data science roles.

-**LinkedIn**: [ www.linkedin.com/in/aniket-pal-098690204 ]
-**Email**: [ aniketspal04@gmail.com ]





