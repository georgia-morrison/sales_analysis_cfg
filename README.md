# Sales Spreadsheet Analysis
Final project from Code First Girls Python Kicksatrter course completed with classmate.

We were required to read in a CSV file and output the total sales. Below is our code:

### Importing necessary libraries and modules
```
import csv
import ssl
ssl._create_default_https_context = ssl._create_unverified_context
import matplotlib.pyplot as plt
import seaborn as sns
import pandas as pd
```
### Creating a function that will read in a csv file and create a list
```
def read_data():
    data = []
    with open('sales.csv', 'r') as sales_csv:
        spreadsheet = csv.DictReader(sales_csv)
        for row in spreadsheet:
            data.append(row)
    return data
```
### Creating a function that calls the previous function and adds the data to a variable called 'sales'. The function then prints the total sales from the year.
```
def run():
    data = read_data()

    sales = []
    for row in data:
        sale = int(row['sales'])
        sales.append(sale)

    total = sum(sales)
    print('Total sales: {}'.format(total))

run()
```
