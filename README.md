# Sales Spreadsheet Analysis
Final project from Code First Girls Python Kickstarter course completed with classmate.

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

Following this we then extended the project by creating a graph that displayed the sales for each month. This was new to us as we had never used seaborn before and it took a lot of trial and error to get it to work.
### Using pandas to read in the csv file. The next line creates a bar plot with the month on the x-axis and sales on the y-axis. We then added a title and labels to the graph, and finally used the show function to display the graph.
```
sales = pd.read_csv('sales.csv')
sns.barplot(x='month', y='sales', data=sales)
plt.title('Sales By Month')
plt.xlabel("Month")
plt.ylabel("Sales")
plt.show()
```
This gave us the output of the graph shown below:

![Sales Graph](https://user-images.githubusercontent.com/87599176/146179032-90e79f10-18c1-4b3b-ae57-6d88dbca6853.png)

We then decided to extend our project further by creating a table of summary statistics.

### First we used pandas again to create a data frame from the data set. We then created new variables describing key statistics by using pandas built in functions. Finally we formatted this as a table, created another data frame and printed it.
```
df = pd.DataFrame(sales)
max_sales = df['sales'].max()
min_sales = df['sales'].min()
max_spend = df['expenditure'].max()
min_spend = df['expenditure'].min()

d = [['Most Sales', max_sales],
     ['Least Sales', min_sales],
     ['Most Spending', max_spend],
     ['Least Spending', min_spend]]
new_df = pd.DataFrame(d)
print(new_df)
```
## Learnings From This Project
If we had more time we would format the summary table to be more presentable, and find a way to add in the months these figures occurred in.

We also struggled a bit with how remote this course was and having to work on a project collaboratively whilst being at opposite ends of the country. This helped us to build resilience and learn to use outside resources online to imprve our project.
