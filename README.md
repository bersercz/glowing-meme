# Police Data Analysis

## About Dataset
### Here, 
### The dataset contains police traffic stop records, including details about driver demographics (age, gender), violations, stop duration, and search information. Missing data was cleaned to ensure accuracy. This data is available as a CSV file. We are going to analyze this data set using the Pandas DataFrame.

###  Data Analyzing & Cleaning
```python
police_data.head()
police_data.count()
police_data.isnull().sum()
police_data[police_data.duplicated]
```
# Problem Statement & Solutions

### 1. Remove the column that only contains missing values
```python
police_data.isnull().sum()
police_data.drop('country_name', axis=1, inplace=True)
```

### 2. For Speeding , were Men or Women stopped more often ? 
```python
police_data[police_data.violation == 'Speeding'].driver_gender.value_counts()
```

### 3. Does gender affect who gets searched during a stop ?
```python
police_data.groupby('driver_gender')['search_conducted'].sum()
```

### 4. What is the mean stop_duration ?
```python
police_data['stop_duration'] = police_data['stop_duration'].map({ '0-15 Min':7.5, '15-30 Min': 24 , '30+ Min': 45 })
police_data['stop_duration'].mean()
```

### 5. Compare the age distributions for each violation
```python
police_data.groupby('driver_age')['violation'].value_counts()
police_data.groupby('driver_age')['violation'].describe()
```


# Findings

### 1. Data cleaning removed incomplete columns, making the dataset more reliable for analysis.
### 2. Speeding emerged as the most common traffic violation in the dataset.
### 3. Male drivers were stopped and searched more frequently compared to female drivers.
### 4. The average stop duration was moderate, reflecting typical time spent on traffic checks.
### 5. Age patterns showed younger drivers were more often involved in speeding, while other violations were more evenly spread across age groups.


# Conclusion

### The analysis shows that traffic stops are influenced by demographic factors such as age and gender. Speeding is the most frequent reason for stops, with men and younger drivers appearing more often in violation records. The project highlights how structured data analysis can reveal trends in law enforcement practices.
