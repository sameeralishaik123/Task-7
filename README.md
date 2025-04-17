# Task 7: Basic Sales Summary from SQLite using Python

This project is part of the **Data Analyst Internship** (Elevate Labs). It demonstrates how to:
- Create a small SQLite database
- Run SQL queries using Python
- Summarize sales data (quantity and revenue per product)
- Visualize the output with a bar chart using Matplotlib


## Objective

- Use Python to connect to an SQLite database
- Execute SQL queries to get sales summary
- Display results using `print()` and a simple bar chart
- Save the chart as an image


## Tools & Libraries

- **Python 3.x**
- Built-in **sqlite3**
- **pandas**
- **matplotlib**
- Optional: Jupyter Notebook or any code editor


##  Dataset Description

We'll create a database named `sales_data.db` with one table: `sales`.

## Bar char picture: 
"sales_chart_pretty.png"

## Table Schema
```sql
CREATE TABLE sales (
  product TEXT,
  quantity INTEGER,
  price REAL
);
## Taken Data in sql:

product | quantity | price
Product A | 10 | 20.0
Product B | 5 | 50.0
Product A | 7 | 20.0
Product C | 3 | 70.0
Product B | 4 | 50.0
Product C | 6 | 70.0

Steps to Run the Project
1. Create and Populate the SQLite Database
Use the sqlite3 module in Python to:

Create the database file

Create a sales table

Insert sample data (products, quantities, and prices)

2. Query and Analyze the Data
Run SQL to summarize the data:

sql
Copy
Edit
SELECT product, 
       SUM(quantity) AS total_qty, 
       SUM(quantity * price) AS revenue
FROM sales
GROUP BY product;
3. Load Data into Pandas and Visualize
Use pandas.read_sql_query() to load results

Print the summary table

Use matplotlib to plot a bar chart:

X-axis: Product

Y-axis: Revenue

Save the chart as sales_chart.png

## Sample Output
Printed DataFrame:
mathematica
Copy
Edit
    product  total_qty  revenue
0  Product A         17    340.0
1  Product B          9    450.0
2  Product C          9    630.0
Bar Chart:
A bar graph showing revenue by product, saved as sales_chart.png


## Final Outcome

Database created with sales data.
SQL query calculates total quantity and revenue by product.
Results printed in the console.
Bar chart of revenue per product is generated and saved.


