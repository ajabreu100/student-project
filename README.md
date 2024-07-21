# Exploring Student Data Analysis

### Project Overview
---

This project aims to provide insightful analysis of student performance, parental occupations, and attendance patterns within a local school district. By utilizing collected data, we aim to address key questions such as how students are performing in their math classes, what students’ parents do for work, and how often students are absent from school.

![Dashboard 1](https://github.com/user-attachments/assets/9eec26f6-281b-4545-844a-9cacc90a1b60)


### Data Sources

EV Data: The primary dataset utilized for the analysis is the "Cleaned Data" file, which represents the cleaned and refined dataset, and the "Raw data" link, which directs access to the raw, untouched imported dataset.

### Tools

-Excel - Data Cleaning ([Cleaned Data](cleaned_ev_data.csv), [Raw data](https://catalog.data.gov/dataset/electric-vehicle-population-data/resource/fa51be35-691f-45d2-9f3e-535877965e69))

-SQLite Studio - Data Analysis

-Tableau - Creating Visualizations


### Data Cleaning/ Preparation

In the data cleaning process phase, we performed tasks such as:
1. Loading CSV file into Excel, along with an initial inspection
2. Filling any missing values that may not have been completed
3. Examining data for any duplicate values
4. Transforming all text casing to proper case
5. Trimming unnecessary data or spaces
6. Formating column titles

### Exploratory Data Analysis

##### Main Question
-Which county of Washington state contains the most EV vehicle registrations
##### Bonus Questions
-Which EV vehicles contain the highest driving range

-What other states are registered in the Washington DOL

### Data Analysis

```python
# Load libraries
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
import seaborn as sns

# Import data
students = pd.read_csv('students.csv')

# Print first few rows of data
print(students.head())
# Print summary statistics for all columns
print(students.describe(include='all'))
# Calculate mean
print(students.math_grade.mean())
# Calculate median
print(students.math_grade.median())
# Calculate mode
print(students.math_grade.mode()[0])
# Calculate range
print(students.math_grade.max() - students.math_grade.min())
# Calculate standard deviation
print(students.math_grade.std())
# Calculate MAD
print(students.math_grade.mad())
# Create a histogram of math grades

sns.histplot(x='math_grade',data=students)
plt.show()
plt.clf()

# Create a box plot of math grades

sns.boxplot(x='math_grade',data=students)
plt.show()
plt.clf()

# Calculate number of students with mothers in each job category
print(students.Mjob.value_counts())
# Calculate proportion of students with mothers in each job category
print(students.Mjob.value_counts(normalize=True))
# Create bar chart of Mjob

sns.countplot(x='Mjob',data=students)
plt.show()
plt.clf()

# Create pie chart of Mjob

students.Mjob.value_counts().plot.pie()
plt.show()
plt.clf()

#Extras
students.address.value_counts().plot.pie()
plt.show()
plt.clf()

sns.histplot(x='absences',data=students)
plt.show()
plt.clf()

sns.countplot(x='Fjob',data=students)
plt.show()
plt.clf()
```

### Results

My findings are summarized as follows:
1. King County had the highest registration count under the Washington DOL.
2. The vehicles in the top-performing EV range include the Chevy Bolt, Hyundai Kona, and Tesla Model S.
3. The other top states registered under the Washington DOL include California, Virginia, and Maryland.

### Recommendations

Based on the results formulated from the analysis:

The counties of King, Snohomish, and Pierce have the highest chance of electric vehicle-related engagement.
Focusing on those areas will increase the likelihood of engagement, as EVs are exponentially more prevalent in these regions.

### Limitations
Unfortunately, some rows have missing values that could not be accounted for in certain calculations. Though the number of NULL values wasn't large, there is still data missing from our overall findings. 

### References

My raw data source: [Click here](https://catalog.data.gov/dataset/electric-vehicle-population-data/resource/fa51be35-691f-45d2-9f3e-535877965e69)

