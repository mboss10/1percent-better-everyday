# Finding the percentage of missing data using a pandas DataFrame

One of the first essential tasks to perform before starting to run data analysis on a set of data is to check the data quality and determine which columns have missing data.

## San Francisco Building Permits sample file
In order to illustrate the method, I'll be using the <a href="">San Francisco Building Permits file available on Kaggle</a>, that stores all types of structural permits from Jan 1, 2013-Feb 25th 2018. Data includes details on application/permit numbers, job addresses, supervisorial districts, and the current status of the applications.  
It turns out there is a lot of NULL/missing data in several columns of that file.  
I want to find the best way to get insights on this before starting any analysis.

## Classic way
Provided that I stored the data in a DataFrame called `sf_permits`,  
I can use `sf_permits.info()` to get an overview of the number of complete entries in each of the columns.  
```
sf_permits.info()
```

<img src=""></img>

## Going beyond the .info()
However, if I want a clearer picture, here's how I can get the percentage of missing entries for each of the ccolumns in descending order:  
```
# Getting percentange of missing data for each column
(sf_permits.isnull().sum()/sf_permits.isnull().count()).sort_values(ascending=False)
```
<img src=""></img>

Sure! Here's an improved version of your KB article with a more structured flow, clearer explanations, and some added context for better understanding.

---

# Finding the Percentage of Missing Data Using a Pandas DataFrame

Before diving into data analysis, it is crucial to assess data quality and identify which columns have missing data. This ensures the reliability of your insights and guides you on data cleaning efforts.

## San Francisco Building Permits Sample File

To illustrate this method, we'll use the [San Francisco Building Permits file available on Kaggle](https://www.kaggle.com/datasets). This dataset contains details of all types of structural permits issued from January 1, 2013, to February 25, 2018. It includes application/permit numbers, job addresses, supervisorial districts, and the current status of applications.  
This file has a significant amount of NULL/missing data in several columns, making it an excellent example for demonstrating how to identify missing data.

## The Classic Way

Assuming we have loaded the data into a DataFrame called `sf_permits`, we can use the `info()` method to get an overview of the number of complete entries in each column.

```python
sf_permits.info()
```

This command will provide a concise summary of the DataFrame, including the number of non-null entries per column. Here's a sample output:

![info_output](path_to_info_image)

## Going Beyond the `.info()`

To get a clearer and more detailed picture of missing data, we can calculate the percentage of missing entries for each column. This method allows us to see which columns have the most missing data, helping prioritize data cleaning tasks.

Here’s how you can do it:

```python
# Calculating the percentage of missing data for each column
missing_data_percentage = (sf_permits.isnull().sum() / sf_permits.isnull().count()).sort_values(ascending=False)
print(missing_data_percentage)
```

This code calculates the percentage of missing values for each column and sorts the results in descending order, making it easy to identify the columns with the highest proportion of missing data.

Here's an example of what the output might look like:

![missing_data_output](path_to_missing_data_image)

## Conclusion

Identifying the percentage of missing data in your dataset is an essential step in the data preparation process. By understanding the extent of missing values, you can make informed decisions on how to handle them, ensuring the accuracy and reliability of your data analysis.

---

By providing a clearer structure and context, this revised article aims to make it easier for readers to follow along and apply the techniques to their own datasets.
