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
