# Week 9 Workshop: Advanced Pandas Retail Chain Performance Analysis

## Background
##### You're working as a data analyst for a retail chain that wants to better understand their sales patterns and customer behavior. The company has collected data on customers, products, and sales transactions. Your task is to use Pandas techniques including DateTime analysis and data aggregation to provide basic insights for the business team.

## Workshop Tasks

### Part 1: DateTime Operations

#### 1. Converting and Working with Dates:

#### * Load all three CSV files and convert date columns to proper DateTime format using pd.to_datetime()


```python
# import pandas and numpy
import pandas as pd
import numpy as np
```

```python
# Load csv files

customers = pd.read_csv('customers_wk9_thurs.csv')
products = pd.read_csv('products_wk9_thurs.csv')
sales = pd.read_csv('sales_wk9_thurs.csv')

print(f"\nThe customers file has {len(customers)} rows.")
print(f"\nThe products file has {len(products)} rows.")
print(f"\nThe sales file has {len(sales)} rows.\n")

```
    
    The customers file has 100 rows.
    
    The products file has 60 rows.
    
    The sales file has 150 rows.

#### * Customers table: Converting date formats


```python
# review customers columns/formats
print("\n* Find the date fields below:\n")
customers.info()

# review date field formats
print("\n* Review date formats for date fields:\n")
print(customers['registration_date'].head()) # yyyy-mm-dd

# review code
print('\n* The variable created to change date shows:\n')
cust_reg_date = pd.to_datetime(customers['registration_date'])
print(cust_reg_date[0:5])

# commit registration date code
customers['registration_date'] = cust_reg_date

# validate results
print("\n* The updated date format should be datetime:\n")
customers['registration_date'].info()
```
    
    * Find the date fields below:
    
    <class 'pandas.DataFrame'>
    RangeIndex: 100 entries, 0 to 99
    Data columns (total 8 columns):
     #   Column             Non-Null Count  Dtype         
    ---  ------             --------------  -----         
     0   customer_id        100 non-null    int64         
     1   first_name         100 non-null    str           
     2   last_name          100 non-null    str           
     3   age                100 non-null    int64         
     4   state              100 non-null    str           
     5   income             100 non-null    int64         
     6   registration_date  100 non-null    datetime64[us]
     7   email              100 non-null    str           
    dtypes: datetime64[us](1), int64(3), str(4)
    memory usage: 6.4 KB
    
    * Review date formats for date fields:
    
    0   2022-01-15
    1   2022-01-22
    2   2022-02-03
    3   2022-02-14
    4   2022-02-28
    Name: registration_date, dtype: datetime64[us]
    
    * The variable created to change date shows:
    
    0   2022-01-15
    1   2022-01-22
    2   2022-02-03
    3   2022-02-14
    4   2022-02-28
    Name: registration_date, dtype: datetime64[us]
    
    * The updated date format should be datetime:
    
    <class 'pandas.Series'>
    RangeIndex: 100 entries, 0 to 99
    Series name: registration_date
    Non-Null Count  Dtype         
    --------------  -----         
    100 non-null    datetime64[us]
    dtypes: datetime64[us](1)
    memory usage: 932.0 bytes
    

##### Sales table: Converting date formats

```python
# review sales columns/formats
print("\n* Find the date fields below:\n")
sales.info()

# review date field formats
print("\n* Review date formats for date fields:\n")
print(sales['transaction_date'].head()) # yyyy-mm-dd

# review code
print('\n* The variable created to change date shows:\n')
sales_trans_date = pd.to_datetime(sales['transaction_date'])
print(sales_trans_date[0:5])

# commit registration date code
sales['transaction_date'] = sales_trans_date

# validate results
print("\n* The updated date format should be datetime:\n")
sales['transaction_date'].info()
```
    
    * Find the date fields below:
    
    <class 'pandas.DataFrame'>
    RangeIndex: 150 entries, 0 to 149
    Data columns (total 6 columns):
     #   Column            Non-Null Count  Dtype         
    ---  ------            --------------  -----         
     0   sale_id           150 non-null    int64         
     1   customer_id       150 non-null    int64         
     2   product_id        150 non-null    int64         
     3   transaction_date  150 non-null    datetime64[us]
     4   quantity          150 non-null    int64         
     5   total_amount      150 non-null    float64       
    dtypes: datetime64[us](1), float64(1), int64(4)
    memory usage: 7.2 KB
    
    * Review date formats for date fields:
    
    0   2022-02-10 14:30:00
    1   2022-02-15 10:15:00
    2   2022-02-20 16:45:00
    3   2022-02-25 11:20:00
    4   2022-03-01 13:10:00
    Name: transaction_date, dtype: datetime64[us]
    
    * The variable created to change date shows:
    
    0   2022-02-10 14:30:00
    1   2022-02-15 10:15:00
    2   2022-02-20 16:45:00
    3   2022-02-25 11:20:00
    4   2022-03-01 13:10:00
    Name: transaction_date, dtype: datetime64[us]
    
    * The updated date format should be datetime:
    
    <class 'pandas.Series'>
    RangeIndex: 150 entries, 0 to 149
    Series name: transaction_date
    Non-Null Count  Dtype         
    --------------  -----         
    150 non-null    datetime64[us]
    dtypes: datetime64[us](1)
    memory usage: 1.3 KB
  
```python
# review sales columns/formats
print("\n* Find the date fields below:\n")
products.info()

# review date field formats
print("\n* Review date formats for date fields:\n")
print(products['launch_date'].head()) 

# review code
print('\n* The variable created to change date shows:\n')
prod_launch_date = pd.to_datetime(products['launch_date'])
print(prod_launch_date[0:5])

# commit registration date code
products['launch_date'] = prod_launch_date

# validate results
print("\n* The updated date format should be datetime:\n")
products['launch_date'].info()

```
    
    * Find the date fields below:
    
    <class 'pandas.DataFrame'>
    RangeIndex: 60 entries, 0 to 59
    Data columns (total 6 columns):
     #   Column        Non-Null Count  Dtype  
    ---  ------        --------------  -----  
     0   product_id    60 non-null     int64  
     1   product_name  60 non-null     str    
     2   category      60 non-null     str    
     3   price         60 non-null     float64
     4   launch_date   60 non-null     str    
     5   brand         60 non-null     str    
    dtypes: float64(1), int64(1), str(4)
    memory usage: 2.9 KB
    
    * Review date formats for date fields:
    
    0    2021-03-15
    1    2021-04-20
    2    2021-05-10
    3    2021-06-01
    4    2021-06-15
    Name: launch_date, dtype: str
    
    * The variable created to change date shows:
    
    0   2021-03-15
    1   2021-04-20
    2   2021-05-10
    3   2021-06-01
    4   2021-06-15
    Name: launch_date, dtype: datetime64[us]
    
    * The updated date format should be datetime:
    
    <class 'pandas.Series'>
    RangeIndex: 60 entries, 0 to 59
    Series name: launch_date
    Non-Null Count  Dtype         
    --------------  -----         
    60 non-null     datetime64[us]
    dtypes: datetime64[us](1)
    memory usage: 612.0 bytes
   
#### * Extract useful components from the sales transaction dates: year, month, and day of week

```python
print('\nThe full datetime:\n')
print(sales['transaction_date'].head())

print('\n* The extracted years:\n')
print(sales['transaction_date'].dt.year[0:5])

print('\n* The extracted month numbers:\n')
print(sales['transaction_date'].dt.month[0:5])

print('\n* The extracted month names:\n')
print(sales['transaction_date'].dt.month_name()[0:5])

print('\n* The extracted month abbreviations:\n')
print(sales['transaction_date'].dt.strftime('%b')[0:5])

print('\n* The extracted date numbers:\n')
print(sales['transaction_date'].dt.day[0:5])

print('\n* The extracted day numbers of week:\n')
print(sales['transaction_date'].dt.day_of_week[0:5])

print('\n* The extracted day names of week:\n')
print(sales['transaction_date'].dt.day_name()[0:5])
```
    
    The full datetime:
    
    0   2022-02-10 14:30:00
    1   2022-02-15 10:15:00
    2   2022-02-20 16:45:00
    3   2022-02-25 11:20:00
    4   2022-03-01 13:10:00
    Name: transaction_date, dtype: datetime64[us]
    
    * The extracted years:
    
    0    2022
    1    2022
    2    2022
    3    2022
    4    2022
    Name: transaction_date, dtype: int32
    
    * The extracted month numbers:
    
    0    2
    1    2
    2    2
    3    2
    4    3
    Name: transaction_date, dtype: int32
    
    * The extracted month names:
    
    0    February
    1    February
    2    February
    3    February
    4       March
    Name: transaction_date, dtype: str
    
    * The extracted month abbreviations:
    
    0    Feb
    1    Feb
    2    Feb
    3    Feb
    4    Mar
    Name: transaction_date, dtype: str
    
    * The extracted date numbers:
    
    0    10
    1    15
    2    20
    3    25
    4     1
    Name: transaction_date, dtype: int32
    
    * The extracted day numbers of week:
    
    0    3
    1    1
    2    6
    3    4
    4    1
    Name: transaction_date, dtype: int32
    
    * The extracted day names of week:
    
    0    Thursday
    1     Tuesday
    2      Sunday
    3      Friday
    4     Tuesday
    Name: transaction_date, dtype: str
    
#### * Display the date range covered by your sales data (earliest and latest dates)

```python
min_trans_date = sales['transaction_date'].min().date()
max_trans_date = sales['transaction_date'].max().date()

print(f'\nThe sales transaction dates range between {min_trans_date} and {max_trans_date}.\n')
```
    
    The sales transaction dates range between 2022-02-10 and 2024-03-05.
    
### 2. Basic Time Analysis:

#### Find the busiest day of the week for sales (by counting transactions)

```python
dow = sales['transaction_date'].dt.day_name().rename('weekday')

top = sales.groupby(dow)['sale_id'].count().sort_values(ascending=False)

print(f'\nAs the chart below illustrates, the best day for sales is {top.index[0]} with {top.iloc[0]}.\n')

sales.groupby(dow).agg(num_sales = ('sale_id', 'count')).sort_values('num_sales', ascending=False)

```
    
    As the chart below illustrates, the best day for sales is Friday with 24.

<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>num_sales</th>
    </tr>
    <tr>
      <th>weekday</th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>Friday</th>
      <td>24</td>
    </tr>
    <tr>
      <th>Tuesday</th>
      <td>22</td>
    </tr>
    <tr>
      <th>Saturday</th>
      <td>21</td>
    </tr>
    <tr>
      <th>Thursday</th>
      <td>21</td>
    </tr>
    <tr>
      <th>Sunday</th>
      <td>21</td>
    </tr>
    <tr>
      <th>Wednesday</th>
      <td>21</td>
    </tr>
    <tr>
      <th>Monday</th>
      <td>20</td>
    </tr>
  </tbody>
</table>
</div>

#### Determine which month had the most transactions

```python
month_name = sales['transaction_date'].dt.month_name().rename('month_name')

top_mo = sales.groupby(month_name)['sale_id'].count().sort_values(ascending=False)

print(f'\nAs the chart below illustrates, the best month for sales is {top_mo.index[0]} with {top_mo.iloc[0]}.\n')

sales.groupby(month_name).agg(num_sales = ('sale_id', 'count')).sort_values('num_sales', ascending=False)

```
    
    As the chart below illustrates, the best month for sales is February with 16.
      
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>num_sales</th>
    </tr>
    <tr>
      <th>month_name</th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>February</th>
      <td>16</td>
    </tr>
    <tr>
      <th>December</th>
      <td>14</td>
    </tr>
    <tr>
      <th>March</th>
      <td>14</td>
    </tr>
    <tr>
      <th>August</th>
      <td>12</td>
    </tr>
    <tr>
      <th>April</th>
      <td>12</td>
    </tr>
    <tr>
      <th>July</th>
      <td>12</td>
    </tr>
    <tr>
      <th>June</th>
      <td>12</td>
    </tr>
    <tr>
      <th>May</th>
      <td>12</td>
    </tr>
    <tr>
      <th>October</th>
      <td>12</td>
    </tr>
    <tr>
      <th>November</th>
      <td>12</td>
    </tr>
    <tr>
      <th>September</th>
      <td>12</td>
    </tr>
    <tr>
      <th>January</th>
      <td>10</td>
    </tr>
  </tbody>
</table>
</div>

#### Count how many sales happened in each year

```python
year_num = sales['transaction_date'].dt.year.rename('year')

sales.groupby(year_num).agg(num_sales = ('sale_id', 'count')).sort_values('num_sales', ascending=False)
```
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>num_sales</th>
    </tr>
    <tr>
      <th>year</th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>2023</th>
      <td>72</td>
    </tr>
    <tr>
      <th>2022</th>
      <td>65</td>
    </tr>
    <tr>
      <th>2024</th>
      <td>13</td>
    </tr>
  </tbody>
</table>
</div>

### Part 2: GroupBy and Aggregation

#### 1. Product Analysis:

#### * Group products by category and calculate the average price for each category

```python
products.groupby('category').agg(
        total_price = ('price', 'mean')).sort_values('total_price', ascending=False).round(2)
```
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>total_price</th>
    </tr>
    <tr>
      <th>category</th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>Sports &amp; Outdoors</th>
      <td>105.90</td>
    </tr>
    <tr>
      <th>Electronics</th>
      <td>59.99</td>
    </tr>
    <tr>
      <th>Clothing</th>
      <td>52.24</td>
    </tr>
    <tr>
      <th>Accessories</th>
      <td>35.07</td>
    </tr>
    <tr>
      <th>Home &amp; Garden</th>
      <td>30.16</td>
    </tr>
  </tbody>
</table>
</div>

#### * Count how many products are in each category

```python
products.groupby('category').agg(
        total_prods = ('product_id', 'count')).sort_values('total_prods', ascending=False)
```
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>total_prods</th>
    </tr>
    <tr>
      <th>category</th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>Electronics</th>
      <td>13</td>
    </tr>
    <tr>
      <th>Accessories</th>
      <td>12</td>
    </tr>
    <tr>
      <th>Clothing</th>
      <td>12</td>
    </tr>
    <tr>
      <th>Home &amp; Garden</th>
      <td>12</td>
    </tr>
    <tr>
      <th>Sports &amp; Outdoors</th>
      <td>11</td>
    </tr>
  </tbody>
</table>
</div>

#### 2. Customer Analysis

#### * Group customers by state and find the average age in each state

```python
customers.groupby('state').agg(
    avg_age = ('age','mean')).sort_values('state')
```
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>avg_age</th>
    </tr>
    <tr>
      <th>state</th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>CA</th>
      <td>34.10</td>
    </tr>
    <tr>
      <th>FL</th>
      <td>39.00</td>
    </tr>
    <tr>
      <th>IL</th>
      <td>37.25</td>
    </tr>
    <tr>
      <th>NY</th>
      <td>36.50</td>
    </tr>
    <tr>
      <th>TX</th>
      <td>38.30</td>
    </tr>
  </tbody>
</table>
</div>

#### * Calculate total spending per customer (sum up all their purchases)

```python
sales.groupby('customer_id').agg(
        sum_purch = ('total_amount', 'sum')).iloc[0:10]
```
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>tot_purch</th>
    </tr>
    <tr>
      <th>customer_id</th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>1</th>
      <td>229.98</td>
    </tr>
    <tr>
      <th>2</th>
      <td>179.96</td>
    </tr>
    <tr>
      <th>3</th>
      <td>154.98</td>
    </tr>
    <tr>
      <th>4</th>
      <td>234.95</td>
    </tr>
    <tr>
      <th>5</th>
      <td>149.98</td>
    </tr>
    <tr>
      <th>6</th>
      <td>219.96</td>
    </tr>
    <tr>
      <th>7</th>
      <td>169.98</td>
    </tr>
    <tr>
      <th>8</th>
      <td>174.96</td>
    </tr>
    <tr>
      <th>9</th>
      <td>139.96</td>
    </tr>
    <tr>
      <th>10</th>
      <td>94.98</td>
    </tr>
  </tbody>
</table>
</div>

#### * Find customers who have made the most purchases

```python
sales.groupby('customer_id').agg(
        tot_purch = ('quantity', 'sum')).sort_values('tot_purch', ascending=False).iloc[0:9]
```
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>tot_purch</th>
    </tr>
    <tr>
      <th>customer_id</th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>40</th>
      <td>8</td>
    </tr>
    <tr>
      <th>55</th>
      <td>7</td>
    </tr>
    <tr>
      <th>60</th>
      <td>7</td>
    </tr>
    <tr>
      <th>52</th>
      <td>7</td>
    </tr>
    <tr>
      <th>28</th>
      <td>6</td>
    </tr>
    <tr>
      <th>58</th>
      <td>6</td>
    </tr>
    <tr>
      <th>23</th>
      <td>6</td>
    </tr>
    <tr>
      <th>20</th>
      <td>5</td>
    </tr>
    <tr>
      <th>15</th>
      <td>5</td>
    </tr>
  </tbody>
</table>
</div>

#### 3. Sales Analysis:

#### * Calculate total sales revenue by month

```python
rev_mo = sales['transaction_date'].dt.to_period('M').rename('month')

sales.groupby(rev_mo).agg(total_revenue=('total_amount', 'sum'))
```
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>total_revenue</th>
    </tr>
    <tr>
      <th>month</th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>2022-02</th>
      <td>229.93</td>
    </tr>
    <tr>
      <th>2022-03</th>
      <td>504.92</td>
    </tr>
    <tr>
      <th>2022-04</th>
      <td>415.90</td>
    </tr>
    <tr>
      <th>2022-05</th>
      <td>450.90</td>
    </tr>
    <tr>
      <th>2022-06</th>
      <td>502.84</td>
    </tr>
    <tr>
      <th>2022-07</th>
      <td>485.90</td>
    </tr>
    <tr>
      <th>2022-08</th>
      <td>376.87</td>
    </tr>
    <tr>
      <th>2022-09</th>
      <td>660.90</td>
    </tr>
    <tr>
      <th>2022-10</th>
      <td>493.90</td>
    </tr>
    <tr>
      <th>2022-11</th>
      <td>481.89</td>
    </tr>
    <tr>
      <th>2022-12</th>
      <td>730.85</td>
    </tr>
    <tr>
      <th>2023-01</th>
      <td>384.91</td>
    </tr>
    <tr>
      <th>2023-02</th>
      <td>750.87</td>
    </tr>
    <tr>
      <th>2023-03</th>
      <td>440.90</td>
    </tr>
    <tr>
      <th>2023-04</th>
      <td>508.87</td>
    </tr>
    <tr>
      <th>2023-05</th>
      <td>726.89</td>
    </tr>
    <tr>
      <th>2023-06</th>
      <td>483.84</td>
    </tr>
    <tr>
      <th>2023-07</th>
      <td>444.90</td>
    </tr>
    <tr>
      <th>2023-08</th>
      <td>493.87</td>
    </tr>
    <tr>
      <th>2023-09</th>
      <td>489.86</td>
    </tr>
    <tr>
      <th>2023-10</th>
      <td>741.90</td>
    </tr>
    <tr>
      <th>2023-11</th>
      <td>540.87</td>
    </tr>
    <tr>
      <th>2023-12</th>
      <td>727.86</td>
    </tr>
    <tr>
      <th>2024-01</th>
      <td>479.88</td>
    </tr>
    <tr>
      <th>2024-02</th>
      <td>688.86</td>
    </tr>
    <tr>
      <th>2024-03</th>
      <td>169.95</td>
    </tr>
  </tbody>
</table>
</div>

#### * Find the average transaction amount by day of the week

```python
dow1 = sales['transaction_date'].dt.day_of_week.rename('day_of_wk')
sales.groupby(dow1).agg(avg_amount=('total_amount', 'mean')).round(2)
```
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>avg_amount</th>
    </tr>
    <tr>
      <th>day_of_wk</th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>90.93</td>
    </tr>
    <tr>
      <th>1</th>
      <td>74.03</td>
    </tr>
    <tr>
      <th>2</th>
      <td>96.07</td>
    </tr>
    <tr>
      <th>3</th>
      <td>102.27</td>
    </tr>
    <tr>
      <th>4</th>
      <td>100.94</td>
    </tr>
    <tr>
      <th>5</th>
      <td>61.12</td>
    </tr>
    <tr>
      <th>6</th>
      <td>99.55</td>
    </tr>
  </tbody>
</table>
</div>

#### * Determine which product category generates the most total revenue

```python
prod_sales =pd. merge(sales[['product_id','total_amount']], products[['product_id','category']], on ='product_id')
prod_sales.groupby('category').agg(tot_rev=('total_amount','sum')).sort_values('tot_rev', ascending=False)
```
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>tot_rev</th>
    </tr>
    <tr>
      <th>category</th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>Sports &amp; Outdoors</th>
      <td>3544.64</td>
    </tr>
    <tr>
      <th>Electronics</th>
      <td>3524.29</td>
    </tr>
    <tr>
      <th>Clothing</th>
      <td>2745.39</td>
    </tr>
    <tr>
      <th>Accessories</th>
      <td>2053.25</td>
    </tr>
    <tr>
      <th>Home &amp; Garden</th>
      <td>1541.46</td>
    </tr>
  </tbody>
</table>
</div>

#### Part 3: Basic Data Insights

#### * Find which state has the most customers

```python
customers.groupby('state').agg(tot_custs=('customer_id', 'count'))
```
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>tot_custs</th>
    </tr>
    <tr>
      <th>state</th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>CA</th>
      <td>20</td>
    </tr>
    <tr>
      <th>FL</th>
      <td>20</td>
    </tr>
    <tr>
      <th>IL</th>
      <td>20</td>
    </tr>
    <tr>
      <th>NY</th>
      <td>20</td>
    </tr>
    <tr>
      <th>TX</th>
      <td>20</td>
    </tr>
  </tbody>
</table>
</div>

#### * Identify the top 5 customers by total spending

```python
sales.groupby('customer_id').agg(tot_spend=('total_amount','sum')).sort_values('tot_spend', ascending=False).iloc[0:5]
```
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>tot_spend</th>
    </tr>
    <tr>
      <th>customer_id</th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>31</th>
      <td>379.97</td>
    </tr>
    <tr>
      <th>13</th>
      <td>359.96</td>
    </tr>
    <tr>
      <th>41</th>
      <td>329.98</td>
    </tr>
    <tr>
      <th>84</th>
      <td>319.98</td>
    </tr>
    <tr>
      <th>30</th>
      <td>284.98</td>
    </tr>
  </tbody>
</table>
</div>

#### * Determine which day of the week has the highest average transaction value

```python
dow2 = sales['transaction_date'].dt.day_name().rename('day_of_wk')
sales.groupby(dow2).agg(avg_amount=('total_amount', 'mean')).round(2).sort_values('avg_amount', ascending=False)
```
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>avg_amount</th>
    </tr>
    <tr>
      <th>day_of_wk</th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>Thursday</th>
      <td>102.27</td>
    </tr>
    <tr>
      <th>Friday</th>
      <td>100.94</td>
    </tr>
    <tr>
      <th>Sunday</th>
      <td>99.55</td>
    </tr>
    <tr>
      <th>Wednesday</th>
      <td>96.07</td>
    </tr>
    <tr>
      <th>Monday</th>
      <td>90.93</td>
    </tr>
    <tr>
      <th>Tuesday</th>
      <td>74.03</td>
    </tr>
    <tr>
      <th>Saturday</th>
      <td>61.12</td>
    </tr>
  </tbody>
</table>
</div>

## Discussion Questions

### 1. DateTime Benefits: How can extracting day of the week and month from dates help a retail business make better decisions?

##### Based on days, weeks, or months businesses can:
#####    (a) Allocate resources staffing, inventory etc. based on time periods
#####    (b) Run sales on certain products on slow sales periods

### 2. GroupBy Value: Why is it useful to group data by categories, states, or time periods rather than looking at individual transactions?

##### By grouping you see higher level trends by categories that individual transactions will no tell you.

### 3. Business Applications: Based on your findings, what simple recommendations would you give to help the retail chain improve their performance?

##### (a) Run promotions on slow days like tuesday, saturday, and monday
##### (b) Increase inventory for sports & Outdoor equipment and Electronics


```python

```
