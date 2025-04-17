
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


## Dataset Description

We'll create a database named `sales_data.db` with one table: `sales`.

### Table Schema
```sql
CREATE TABLE sales (
  product TEXT,
  quantity INTEGER,
  price REAL
);
```

### Sample Data
| product   | quantity | price |
|-----------|----------|-------|
| Product A | 10       | 20.0  |
| Product B | 5        | 50.0  |
| Product A | 7        | 20.0  |
| Product C | 3        | 70.0  |
| Product B | 4        | 50.0  |
| Product C | 6        | 70.0  |

---

## 🚀 Full Process (Code Included)

python
# Import libraries
import sqlite3
import pandas as pd
import matplotlib.pyplot as plt

# Step 1: Create the database and insert sample data
conn = sqlite3.connect('sales_data.db')
cursor = conn.cursor()

# Create table
cursor.execute('''
    CREATE TABLE IF NOT EXISTS sales (
        product TEXT,
        quantity INTEGER,
        price REAL
    )
''')

# Sample data
sales_data = [
    ('Product A', 10, 20.0),
    ('Product B', 5, 50.0),
    ('Product A', 7, 20.0),
    ('Product C', 3, 70.0),
    ('Product B', 4, 50.0),
    ('Product C', 6, 70.0)
]

# Insert data
cursor.executemany('INSERT INTO sales (product, quantity, price) VALUES (?, ?, ?)', sales_data)
conn.commit()

# Step 2: Write SQL query to summarize data
query = '''
SELECT product,
       SUM(quantity) AS total_qty,
       SUM(quantity * price) AS revenue
FROM sales
GROUP BY product
'''

# Step 3: Load data into pandas
df = pd.read_sql_query(query, conn)

# Step 4: Print summary
print("Sales Summary:\n")
print(df)

# Step 5: Plot bar chart
df.plot(kind='bar', x='product', y='revenue', legend=False, color='skyblue')
plt.title('Revenue by Product')
plt.xlabel('Product')
plt.ylabel('Revenue')
plt.tight_layout()
plt.savefig('sales_chart.png')  # Save chart
plt.show()

# Step 6: Close connection
conn.close()
```



## Expected Output

###  Printed Output
```
    product  total_qty  revenue
0  Product A         17    340.0
1  Product B          9    450.0
2  Product C          9    630.0
```

### Chart
- A bar chart saved as **sales_chart.png** showing revenue per product.


## Requirements

Install required packages if not already installed:
```bash
pip install pandas matplotlib
```


## Learning Outcomes

- Learn basic SQL queries
- Practice importing SQL data into Python
- Perform data summarization
- Create your first sales chart using Matplotlib


## Files Generated

- `sales_data.db`: SQLite database
- `sales_chart.png`: Revenue chart
- This `README.md` file

