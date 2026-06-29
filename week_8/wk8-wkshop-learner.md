```python
import pandas as pd
import numpy as np
```

# 1. Data Loading and Exploration

## * Read all CSV files into Pandas DataFrames


```python
stores = pd.read_csv('stores.csv')
sales = pd.read_csv('sales.csv')
products = pd.read_csv('products.csv')
inventory = pd.read_csv('inventory.csv')
customers = pd.read_csv('customers.csv')
```

## * Display the first few rows of each DataFrame


```python
stores.head()
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>store_id</th>
      <th>store_name</th>
      <th>address</th>
      <th>city</th>
      <th>state</th>
      <th>zip_code</th>
      <th>region</th>
      <th>size_sqft</th>
      <th>opening_date</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>1</td>
      <td>City Center</td>
      <td>123 Retail Blvd</td>
      <td>New York</td>
      <td>NY</td>
      <td>10001</td>
      <td>Northeast</td>
      <td>32500.0</td>
      <td>2005-05-20</td>
    </tr>
    <tr>
      <th>1</th>
      <td>2</td>
      <td>Mall of Chicago</td>
      <td>456 Shopping Ave</td>
      <td>Chicago</td>
      <td>IL</td>
      <td>60611</td>
      <td>Midwest</td>
      <td>45000.0</td>
      <td>2007-08-15</td>
    </tr>
    <tr>
      <th>2</th>
      <td>3</td>
      <td>Los Angeles Plaza</td>
      <td>789 Commerce St</td>
      <td>Los Angeles</td>
      <td>CA</td>
      <td>90001</td>
      <td>West</td>
      <td>55000.0</td>
      <td>2004-03-10</td>
    </tr>
    <tr>
      <th>3</th>
      <td>4</td>
      <td>Houston Galleria</td>
      <td>321 Main St</td>
      <td>Houston</td>
      <td>Texas</td>
      <td>77002</td>
      <td>Southwest</td>
      <td>NaN</td>
      <td>2008-11-05</td>
    </tr>
    <tr>
      <th>4</th>
      <td>5</td>
      <td>Phoenix Outlet</td>
      <td>654 Desert Rd</td>
      <td>Phoenix</td>
      <td>AZ</td>
      <td>85001</td>
      <td>Southwest</td>
      <td>18500.0</td>
      <td>2010-06-30</td>
    </tr>
  </tbody>
</table>
</div>




```python
sales.head()
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>sale_id</th>
      <th>date</th>
      <th>store_id</th>
      <th>customer_id</th>
      <th>product_id</th>
      <th>quantity</th>
      <th>total</th>
      <th>payment_method</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>1</td>
      <td>2022-01-15</td>
      <td>3.0</td>
      <td>12</td>
      <td>5</td>
      <td>2</td>
      <td>49.98</td>
      <td>Credit Card</td>
    </tr>
    <tr>
      <th>1</th>
      <td>2</td>
      <td>2022-01-16</td>
      <td>1.0</td>
      <td>5</td>
      <td>10</td>
      <td>1</td>
      <td>49.99</td>
      <td>credit card</td>
    </tr>
    <tr>
      <th>2</th>
      <td>3</td>
      <td>2022-01-18</td>
      <td>2.0</td>
      <td>8</td>
      <td>3</td>
      <td>1</td>
      <td>349.99</td>
      <td>DEBIT CARD</td>
    </tr>
    <tr>
      <th>3</th>
      <td>4</td>
      <td>2022-01-20</td>
      <td>4.0</td>
      <td>20</td>
      <td>7</td>
      <td>1</td>
      <td>349.99</td>
      <td>Cash</td>
    </tr>
    <tr>
      <th>4</th>
      <td>5</td>
      <td>2022-01-22</td>
      <td>5.0</td>
      <td>3</td>
      <td>15</td>
      <td>1</td>
      <td>1599.99</td>
      <td>CC</td>
    </tr>
  </tbody>
</table>
</div>




```python
products.head()
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>product_id</th>
      <th>product_name</th>
      <th>category</th>
      <th>subcategory</th>
      <th>brand</th>
      <th>price</th>
      <th>cost</th>
      <th>weight</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>1</td>
      <td>Apple iPhone 13</td>
      <td>Electronics</td>
      <td>Smartphones</td>
      <td>Apple</td>
      <td>899.99</td>
      <td>649.99</td>
      <td>0.45</td>
    </tr>
    <tr>
      <th>1</th>
      <td>2</td>
      <td>Samsung Galaxy S21</td>
      <td>electronics</td>
      <td>Smartphones</td>
      <td>Samsung</td>
      <td>799.99</td>
      <td>539.99</td>
      <td>0.50</td>
    </tr>
    <tr>
      <th>2</th>
      <td>3</td>
      <td>Sony WH-1000XM4</td>
      <td>ELECTRONICS</td>
      <td>Headphones</td>
      <td>Sony</td>
      <td>349.99</td>
      <td>210.00</td>
      <td>0.60</td>
    </tr>
    <tr>
      <th>3</th>
      <td>4</td>
      <td>Dell XPS 13</td>
      <td>Electronics</td>
      <td>Laptops</td>
      <td>Dell</td>
      <td>1299.99</td>
      <td>899.99</td>
      <td>2.80</td>
    </tr>
    <tr>
      <th>4</th>
      <td>5</td>
      <td>Nike Classic Tee</td>
      <td>Clothing</td>
      <td>Shirts</td>
      <td>Nike</td>
      <td>24.99</td>
      <td>12.50</td>
      <td>0.20</td>
    </tr>
  </tbody>
</table>
</div>




```python
inventory.head()
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>inventory_id</th>
      <th>store_id</th>
      <th>product_id</th>
      <th>quantity_in_stock</th>
      <th>last_restock_date</th>
      <th>reorder_level</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>1</td>
      <td>1</td>
      <td>1</td>
      <td>25</td>
      <td>2022-10-15</td>
      <td>10.0</td>
    </tr>
    <tr>
      <th>1</th>
      <td>2</td>
      <td>1</td>
      <td>5</td>
      <td>42</td>
      <td>2022-11-02</td>
      <td>15.0</td>
    </tr>
    <tr>
      <th>2</th>
      <td>3</td>
      <td>1</td>
      <td>10</td>
      <td>18</td>
      <td>2022-09-30</td>
      <td>8.0</td>
    </tr>
    <tr>
      <th>3</th>
      <td>4</td>
      <td>1</td>
      <td>15</td>
      <td>5</td>
      <td>2022-10-20</td>
      <td>10.0</td>
    </tr>
    <tr>
      <th>4</th>
      <td>5</td>
      <td>1</td>
      <td>20</td>
      <td>12</td>
      <td>NaN</td>
      <td>15.0</td>
    </tr>
  </tbody>
</table>
</div>




```python
customers.head()
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>customer_id</th>
      <th>first_name</th>
      <th>last_name</th>
      <th>email</th>
      <th>phone</th>
      <th>address</th>
      <th>city</th>
      <th>state</th>
      <th>zip_code</th>
      <th>registration_date</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>1</td>
      <td>James</td>
      <td>Smith</td>
      <td>james.smith@gmail.com</td>
      <td>555-123-4567</td>
      <td>123 Main St</td>
      <td>New York</td>
      <td>NY</td>
      <td>10001</td>
      <td>2021-03-15</td>
    </tr>
    <tr>
      <th>1</th>
      <td>2</td>
      <td>Mary</td>
      <td>Johnson</td>
      <td>NaN</td>
      <td>212.555.6789</td>
      <td>456 Park Ave</td>
      <td>New York</td>
      <td>NY</td>
      <td>10022</td>
      <td>2020-11-02</td>
    </tr>
    <tr>
      <th>2</th>
      <td>3</td>
      <td>John</td>
      <td>Williams</td>
      <td>jwilliams@yahoo.com</td>
      <td>(555) 987-6543</td>
      <td>789 Broadway</td>
      <td>Los Angeles</td>
      <td>California</td>
      <td>90001-1234</td>
      <td>2021-05-20</td>
    </tr>
    <tr>
      <th>3</th>
      <td>4</td>
      <td>Patricia</td>
      <td>Brown</td>
      <td>pbrown@hotmail.com</td>
      <td>5551234567</td>
      <td>321 Elm St</td>
      <td>Chicago</td>
      <td>IL</td>
      <td>60601</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>4</th>
      <td>5</td>
      <td>Robert</td>
      <td>Jones</td>
      <td>rjones23@gmail.com</td>
      <td>555-987-3456</td>
      <td>555 Pine St</td>
      <td>Houston</td>
      <td>TX</td>
      <td>77002</td>
      <td>2020-09-12</td>
    </tr>
  </tbody>
</table>
</div>



# 2. Exploratory Analysis

## * Obtain summary statistics for numerical columns


```python
sales.describe()
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>sale_id</th>
      <th>store_id</th>
      <th>customer_id</th>
      <th>product_id</th>
      <th>quantity</th>
      <th>total</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>count</th>
      <td>40.000000</td>
      <td>39.000000</td>
      <td>40.000000</td>
      <td>40.000000</td>
      <td>40.000000</td>
      <td>40.000000</td>
    </tr>
    <tr>
      <th>mean</th>
      <td>20.500000</td>
      <td>6.487179</td>
      <td>14.075000</td>
      <td>13.500000</td>
      <td>1.625000</td>
      <td>352.296500</td>
    </tr>
    <tr>
      <th>std</th>
      <td>11.690452</td>
      <td>4.235637</td>
      <td>8.303189</td>
      <td>8.857852</td>
      <td>0.952392</td>
      <td>377.625776</td>
    </tr>
    <tr>
      <th>min</th>
      <td>1.000000</td>
      <td>1.000000</td>
      <td>1.000000</td>
      <td>1.000000</td>
      <td>1.000000</td>
      <td>19.980000</td>
    </tr>
    <tr>
      <th>25%</th>
      <td>10.750000</td>
      <td>3.000000</td>
      <td>6.750000</td>
      <td>5.750000</td>
      <td>1.000000</td>
      <td>99.737500</td>
    </tr>
    <tr>
      <th>50%</th>
      <td>20.500000</td>
      <td>6.000000</td>
      <td>13.500000</td>
      <td>11.500000</td>
      <td>1.000000</td>
      <td>229.985000</td>
    </tr>
    <tr>
      <th>75%</th>
      <td>30.250000</td>
      <td>9.500000</td>
      <td>20.250000</td>
      <td>21.250000</td>
      <td>2.000000</td>
      <td>352.487500</td>
    </tr>
    <tr>
      <th>max</th>
      <td>40.000000</td>
      <td>15.000000</td>
      <td>29.000000</td>
      <td>30.000000</td>
      <td>5.000000</td>
      <td>1599.990000</td>
    </tr>
  </tbody>
</table>
</div>




```python
products.describe()
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>product_id</th>
      <th>price</th>
      <th>cost</th>
      <th>weight</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>count</th>
      <td>30.000000</td>
      <td>30.000000</td>
      <td>30.000000</td>
      <td>28.000000</td>
    </tr>
    <tr>
      <th>mean</th>
      <td>15.500000</td>
      <td>191.724000</td>
      <td>203.159000</td>
      <td>3.835714</td>
    </tr>
    <tr>
      <th>std</th>
      <td>8.803408</td>
      <td>452.483576</td>
      <td>278.924138</td>
      <td>5.693236</td>
    </tr>
    <tr>
      <th>min</th>
      <td>1.000000</td>
      <td>-1599.990000</td>
      <td>1.800000</td>
      <td>0.200000</td>
    </tr>
    <tr>
      <th>25%</th>
      <td>8.250000</td>
      <td>46.990000</td>
      <td>28.375000</td>
      <td>0.500000</td>
    </tr>
    <tr>
      <th>50%</th>
      <td>15.500000</td>
      <td>134.990000</td>
      <td>82.500000</td>
      <td>1.150000</td>
    </tr>
    <tr>
      <th>75%</th>
      <td>22.750000</td>
      <td>322.490000</td>
      <td>236.250000</td>
      <td>3.750000</td>
    </tr>
    <tr>
      <th>max</th>
      <td>30.000000</td>
      <td>1299.990000</td>
      <td>1100.000000</td>
      <td>25.000000</td>
    </tr>
  </tbody>
</table>
</div>




```python
inventory.describe()
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>inventory_id</th>
      <th>store_id</th>
      <th>product_id</th>
      <th>quantity_in_stock</th>
      <th>reorder_level</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>count</th>
      <td>75.000000</td>
      <td>75.000000</td>
      <td>75.000000</td>
      <td>75.000000</td>
      <td>69.000000</td>
    </tr>
    <tr>
      <th>mean</th>
      <td>38.000000</td>
      <td>8.000000</td>
      <td>12.733333</td>
      <td>22.640000</td>
      <td>12.681159</td>
    </tr>
    <tr>
      <th>std</th>
      <td>21.794495</td>
      <td>4.349588</td>
      <td>7.179801</td>
      <td>13.923187</td>
      <td>3.327659</td>
    </tr>
    <tr>
      <th>min</th>
      <td>1.000000</td>
      <td>1.000000</td>
      <td>1.000000</td>
      <td>0.000000</td>
      <td>8.000000</td>
    </tr>
    <tr>
      <th>25%</th>
      <td>19.500000</td>
      <td>4.000000</td>
      <td>6.500000</td>
      <td>15.000000</td>
      <td>10.000000</td>
    </tr>
    <tr>
      <th>50%</th>
      <td>38.000000</td>
      <td>8.000000</td>
      <td>13.000000</td>
      <td>25.000000</td>
      <td>10.000000</td>
    </tr>
    <tr>
      <th>75%</th>
      <td>56.500000</td>
      <td>12.000000</td>
      <td>19.000000</td>
      <td>33.500000</td>
      <td>15.000000</td>
    </tr>
    <tr>
      <th>max</th>
      <td>75.000000</td>
      <td>15.000000</td>
      <td>25.000000</td>
      <td>45.000000</td>
      <td>20.000000</td>
    </tr>
  </tbody>
</table>
</div>



## * Check for missing values in all dataframes


```python
print('\nStores: Columns/Missing values')
stores.isnull().sum()
```

    
    Stores: Columns/Missing values
    




    store_id        0
    store_name      0
    address         0
    city            0
    state           0
    zip_code        0
    region          0
    size_sqft       2
    opening_date    1
    dtype: int64




```python
print('\nSales: Columns/Missing values')
sales.isnull().sum()
```

    
    Sales: Columns/Missing values
    




    sale_id           0
    date              1
    store_id          1
    customer_id       0
    product_id        0
    quantity          0
    total             0
    payment_method    1
    dtype: int64




```python
print('\nProducts: Columns/Missing values')
products.isnull().sum()
```

    
    Products: Columns/Missing values
    




    product_id      0
    product_name    0
    category        0
    subcategory     0
    brand           0
    price           0
    cost            0
    weight          2
    dtype: int64




```python
print('\nInventory: Columns/Missing values')
inventory.isnull().sum()
```

    
    Inventory: Columns/Missing values
    




    inventory_id         0
    store_id             0
    product_id           0
    quantity_in_stock    0
    last_restock_date    9
    reorder_level        6
    dtype: int64




```python
print('\nCustomers: Columns/Missing values')
customers.isnull().sum()
```

    
    Customers: Columns/Missing values
    




    customer_id          0
    first_name           0
    last_name            0
    email                3
    phone                2
    address              0
    city                 0
    state                0
    zip_code             1
    registration_date    3
    dtype: int64



## * Display the data types of each column


```python
print('\nStores: Columns/Data Types')
stores.dtypes
```

    
    Stores: Columns/Data Types
    




    store_id          int64
    store_name          str
    address             str
    city                str
    state               str
    zip_code            str
    region              str
    size_sqft       float64
    opening_date        str
    dtype: object




```python
print('\nSales: Columns/Data Types')
sales.dtypes
```

    
    Sales: Columns/Data Types
    




    sale_id             int64
    date                  str
    store_id          float64
    customer_id         int64
    product_id          int64
    quantity            int64
    total             float64
    payment_method        str
    dtype: object




```python
print('\nProducts: Columns/Data Types')
products.dtypes
```

    
    Products: Columns/Data Types
    




    product_id        int64
    product_name        str
    category            str
    subcategory         str
    brand               str
    price           float64
    cost            float64
    weight          float64
    dtype: object




```python
print('\nInventory: Columns/Data Types')
inventory.dtypes
```

    
    Inventory: Columns/Data Types
    




    inventory_id           int64
    store_id               int64
    product_id             int64
    quantity_in_stock      int64
    last_restock_date        str
    reorder_level        float64
    dtype: object




```python
print('\nCustomers: Columns/Data Types')
customers.dtypes
```

    
    Customers: Columns/Data Types
    




    customer_id          int64
    first_name             str
    last_name              str
    email                  str
    phone                  str
    address                str
    city                   str
    state                  str
    zip_code               str
    registration_date      str
    dtype: object



# 3. Basic Information Retrieval

## * How many unique products are in the product catalog?


```python
dupe_prods = products.duplicated(subset=['product_name']).sum()

print('\n=========================================================================')
print(f'The number of duplicate products in the product table is {dupe_prods}.')
print('=========================================================================\n')

```

    
    =========================================================================
    The number of duplicate products in the product table is 0.
    =========================================================================
    
    

## * What are the top 5 most expensive products?


```python
top_5 = products.nlargest(5, 'price')[['product_name', 'price']]

print('\n=======================================================')
print("The top 5 most expensive products are:")
print()
for i, row in enumerate(top_5.itertuples(), start=1):
    print(f"{i}) {row.product_name:<25} ${row.price:,.2f}")
print('=======================================================\n')    

```

    
    =======================================================
    The top 5 most expensive products are:
    
    1) Dell XPS 13               $1,299.99
    2) Apple iPhone 13           $899.99
    3) Samsung Galaxy S21        $799.99
    4) Dyson V11 Vacuum          $599.99
    5) Sony PlayStation 5        $499.99
    =======================================================
    
    

## * Which store has the largest floor space?


```python
# 1st try

biggest = stores.nlargest(1,'size_sqft')[['store_name', 'size_sqft']]

print('\n====================================================================================')
for y in biggest.itertuples():
    print(f"The {y.store_name} has the largest floor space with {y.size_sqft:,} sq feet.")
print('====================================================================================\n')    

```

    
    ====================================================================================
    The Los Angeles Plaza has the largest floor space with 55,000.0 sq feet.
    ====================================================================================
    
    


```python
# 2nd try
row = stores.nlargest(1, 'size_sqft').iloc[0]

print('\n====================================================================================')
print(f"The {row.store_name} has the largest floor space with {row.size_sqft:,} sq feet.")
print('====================================================================================\n')
```

    
    ====================================================================================
    The Los Angeles Plaza has the largest floor space with 55,000.0 sq feet.
    ====================================================================================
    
    

## * What is the distribution of customers by state?



```python
state_abbrev = {
    'Alabama': 'AL', 'Alaska': 'AK', 'Arizona': 'AZ', 'Arkansas': 'AR',
    'California': 'CA', 'Colorado': 'CO', 'Connecticut': 'CT', 'Delaware': 'DE',
    'Florida': 'FL', 'Georgia': 'GA', 'Hawaii': 'HI', 'Idaho': 'ID',
    'Illinois': 'IL', 'Indiana': 'IN', 'Iowa': 'IA', 'Kansas': 'KS',
    'Kentucky': 'KY', 'Louisiana': 'LA', 'Maine': 'ME', 'Maryland': 'MD',
    'Massachusetts': 'MA', 'Michigan': 'MI', 'Minnesota': 'MN', 'Mississippi': 'MS',
    'Missouri': 'MO', 'Montana': 'MT', 'Nebraska': 'NE', 'Nevada': 'NV',
    'New Hampshire': 'NH', 'New Jersey': 'NJ', 'New Mexico': 'NM', 'New York': 'NY',
    'North Carolina': 'NC', 'North Dakota': 'ND', 'Ohio': 'OH', 'Oklahoma': 'OK',
    'Oregon': 'OR', 'Pennsylvania': 'PA', 'Rhode Island': 'RI', 'South Carolina': 'SC',
    'South Dakota': 'SD', 'Tennessee': 'TN', 'Texas': 'TX', 'Utah': 'UT',
    'Vermont': 'VT', 'Virginia': 'VA', 'Washington': 'WA', 'West Virginia': 'WV',
    'Wisconsin': 'WI', 'Wyoming': 'WY'
}
customers['state'] = customers['state'].map(state_abbrev).fillna(customers['state'])
customers['state'].value_counts()
```




    state
    TX    5
    CA    4
    NY    2
    MD    2
    IL    1
    AZ    1
    PA    1
    FL    1
    OH    1
    NC    1
    IN    1
    WA    1
    CO    1
    MA    1
    OR    1
    NV    1
    MI    1
    TN    1
    KY    1
    WI    1
    NM    1
    MO    1
    Name: count, dtype: int64



# 4. Data Cleaning - Handling Missing Values

## * Create copies of original DataFrames for cleaning


```python
inventory_raw = inventory.copy()
inventory_raw.head()
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>inventory_id</th>
      <th>store_id</th>
      <th>product_id</th>
      <th>quantity_in_stock</th>
      <th>last_restock_date</th>
      <th>reorder_level</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>1</td>
      <td>1</td>
      <td>1</td>
      <td>25</td>
      <td>2022-10-15</td>
      <td>10.0</td>
    </tr>
    <tr>
      <th>1</th>
      <td>2</td>
      <td>1</td>
      <td>5</td>
      <td>42</td>
      <td>2022-11-02</td>
      <td>15.0</td>
    </tr>
    <tr>
      <th>2</th>
      <td>3</td>
      <td>1</td>
      <td>10</td>
      <td>18</td>
      <td>2022-09-30</td>
      <td>8.0</td>
    </tr>
    <tr>
      <th>3</th>
      <td>4</td>
      <td>1</td>
      <td>15</td>
      <td>5</td>
      <td>2022-10-20</td>
      <td>10.0</td>
    </tr>
    <tr>
      <th>4</th>
      <td>5</td>
      <td>1</td>
      <td>20</td>
      <td>12</td>
      <td>NaN</td>
      <td>15.0</td>
    </tr>
  </tbody>
</table>
</div>




```python
stores_raw = stores.copy()
stores_raw.head()
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>store_id</th>
      <th>store_name</th>
      <th>address</th>
      <th>city</th>
      <th>state</th>
      <th>zip_code</th>
      <th>region</th>
      <th>size_sqft</th>
      <th>opening_date</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>1</td>
      <td>City Center</td>
      <td>123 Retail Blvd</td>
      <td>New York</td>
      <td>NY</td>
      <td>10001</td>
      <td>Northeast</td>
      <td>32500.0</td>
      <td>2005-05-20</td>
    </tr>
    <tr>
      <th>1</th>
      <td>2</td>
      <td>Mall of Chicago</td>
      <td>456 Shopping Ave</td>
      <td>Chicago</td>
      <td>IL</td>
      <td>60611</td>
      <td>Midwest</td>
      <td>45000.0</td>
      <td>2007-08-15</td>
    </tr>
    <tr>
      <th>2</th>
      <td>3</td>
      <td>Los Angeles Plaza</td>
      <td>789 Commerce St</td>
      <td>Los Angeles</td>
      <td>CA</td>
      <td>90001</td>
      <td>West</td>
      <td>55000.0</td>
      <td>2004-03-10</td>
    </tr>
    <tr>
      <th>3</th>
      <td>4</td>
      <td>Houston Galleria</td>
      <td>321 Main St</td>
      <td>Houston</td>
      <td>Texas</td>
      <td>77002</td>
      <td>Southwest</td>
      <td>NaN</td>
      <td>2008-11-05</td>
    </tr>
    <tr>
      <th>4</th>
      <td>5</td>
      <td>Phoenix Outlet</td>
      <td>654 Desert Rd</td>
      <td>Phoenix</td>
      <td>AZ</td>
      <td>85001</td>
      <td>Southwest</td>
      <td>18500.0</td>
      <td>2010-06-30</td>
    </tr>
  </tbody>
</table>
</div>




```python
sales_raw = sales.copy()
sales_raw.head()
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>sale_id</th>
      <th>date</th>
      <th>store_id</th>
      <th>customer_id</th>
      <th>product_id</th>
      <th>quantity</th>
      <th>total</th>
      <th>payment_method</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>1</td>
      <td>2022-01-15</td>
      <td>3.0</td>
      <td>12</td>
      <td>5</td>
      <td>2</td>
      <td>49.98</td>
      <td>Credit Card</td>
    </tr>
    <tr>
      <th>1</th>
      <td>2</td>
      <td>2022-01-16</td>
      <td>1.0</td>
      <td>5</td>
      <td>10</td>
      <td>1</td>
      <td>49.99</td>
      <td>credit card</td>
    </tr>
    <tr>
      <th>2</th>
      <td>3</td>
      <td>2022-01-18</td>
      <td>2.0</td>
      <td>8</td>
      <td>3</td>
      <td>1</td>
      <td>349.99</td>
      <td>DEBIT CARD</td>
    </tr>
    <tr>
      <th>3</th>
      <td>4</td>
      <td>2022-01-20</td>
      <td>4.0</td>
      <td>20</td>
      <td>7</td>
      <td>1</td>
      <td>349.99</td>
      <td>Cash</td>
    </tr>
    <tr>
      <th>4</th>
      <td>5</td>
      <td>2022-01-22</td>
      <td>5.0</td>
      <td>3</td>
      <td>15</td>
      <td>1</td>
      <td>1599.99</td>
      <td>CC</td>
    </tr>
  </tbody>
</table>
</div>




```python
products_raw = products.copy()
products_raw.head()
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>product_id</th>
      <th>product_name</th>
      <th>category</th>
      <th>subcategory</th>
      <th>brand</th>
      <th>price</th>
      <th>cost</th>
      <th>weight</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>1</td>
      <td>Apple iPhone 13</td>
      <td>Electronics</td>
      <td>Smartphones</td>
      <td>Apple</td>
      <td>899.99</td>
      <td>649.99</td>
      <td>0.45</td>
    </tr>
    <tr>
      <th>1</th>
      <td>2</td>
      <td>Samsung Galaxy S21</td>
      <td>electronics</td>
      <td>Smartphones</td>
      <td>Samsung</td>
      <td>799.99</td>
      <td>539.99</td>
      <td>0.50</td>
    </tr>
    <tr>
      <th>2</th>
      <td>3</td>
      <td>Sony WH-1000XM4</td>
      <td>ELECTRONICS</td>
      <td>Headphones</td>
      <td>Sony</td>
      <td>349.99</td>
      <td>210.00</td>
      <td>0.60</td>
    </tr>
    <tr>
      <th>3</th>
      <td>4</td>
      <td>Dell XPS 13</td>
      <td>Electronics</td>
      <td>Laptops</td>
      <td>Dell</td>
      <td>1299.99</td>
      <td>899.99</td>
      <td>2.80</td>
    </tr>
    <tr>
      <th>4</th>
      <td>5</td>
      <td>Nike Classic Tee</td>
      <td>Clothing</td>
      <td>Shirts</td>
      <td>Nike</td>
      <td>24.99</td>
      <td>12.50</td>
      <td>0.20</td>
    </tr>
  </tbody>
</table>
</div>




```python
customers_raw = customers.copy()
customers_raw.head()
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>customer_id</th>
      <th>first_name</th>
      <th>last_name</th>
      <th>email</th>
      <th>phone</th>
      <th>address</th>
      <th>city</th>
      <th>state</th>
      <th>zip_code</th>
      <th>registration_date</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>1</td>
      <td>James</td>
      <td>Smith</td>
      <td>james.smith@gmail.com</td>
      <td>555-123-4567</td>
      <td>123 Main St</td>
      <td>New York</td>
      <td>NY</td>
      <td>10001</td>
      <td>2021-03-15</td>
    </tr>
    <tr>
      <th>1</th>
      <td>2</td>
      <td>Mary</td>
      <td>Johnson</td>
      <td>NaN</td>
      <td>212.555.6789</td>
      <td>456 Park Ave</td>
      <td>New York</td>
      <td>NY</td>
      <td>10022</td>
      <td>2020-11-02</td>
    </tr>
    <tr>
      <th>2</th>
      <td>3</td>
      <td>John</td>
      <td>Williams</td>
      <td>jwilliams@yahoo.com</td>
      <td>(555) 987-6543</td>
      <td>789 Broadway</td>
      <td>Los Angeles</td>
      <td>CA</td>
      <td>90001-1234</td>
      <td>2021-05-20</td>
    </tr>
    <tr>
      <th>3</th>
      <td>4</td>
      <td>Patricia</td>
      <td>Brown</td>
      <td>pbrown@hotmail.com</td>
      <td>5551234567</td>
      <td>321 Elm St</td>
      <td>Chicago</td>
      <td>IL</td>
      <td>60601</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>4</th>
      <td>5</td>
      <td>Robert</td>
      <td>Jones</td>
      <td>rjones23@gmail.com</td>
      <td>555-987-3456</td>
      <td>555 Pine St</td>
      <td>Houston</td>
      <td>TX</td>
      <td>77002</td>
      <td>2020-09-12</td>
    </tr>
  </tbody>
</table>
</div>



## * Identify all missing values in each dataset


```python
stores.isnull().sum()
```




    store_id        0
    store_name      0
    address         0
    city            0
    state           0
    zip_code        0
    region          0
    size_sqft       2
    opening_date    1
    dtype: int64




```python
sales.isnull().sum()
```




    sale_id           0
    date              1
    store_id          1
    customer_id       0
    product_id        0
    quantity          0
    total             0
    payment_method    1
    dtype: int64




```python
customers.isnull().sum()
```




    customer_id          0
    first_name           0
    last_name            0
    email                3
    phone                2
    address              0
    city                 0
    state                0
    zip_code             1
    registration_date    3
    dtype: int64




```python
inventory.isnull().sum()
```




    inventory_id         0
    store_id             0
    product_id           0
    quantity_in_stock    0
    last_restock_date    9
    reorder_level        6
    dtype: int64




```python
products.isnull().sum()
```




    product_id      0
    product_name    0
    category        0
    subcategory     0
    brand           0
    price           0
    cost            0
    weight          2
    dtype: int64



## * For numerical columns with missing values, replace with column mean


```python
stores['size_sqft'].fillna(stores['size_sqft'].mean())
```




    0     32500.000000
    1     45000.000000
    2     55000.000000
    3     30653.846154
    4     18500.000000
    5     22000.000000
    6     35000.000000
    7     27500.000000
    8     42000.000000
    9     16500.000000
    10    29000.000000
    11    31500.000000
    12    24000.000000
    13    30653.846154
    14    20000.000000
    Name: size_sqft, dtype: float64




```python
inventory['reorder_level'].fillna(inventory['reorder_level'].mean())
```




    0     10.0
    1     15.0
    2      8.0
    3     10.0
    4     15.0
          ... 
    70    10.0
    71     8.0
    72    10.0
    73    15.0
    74    10.0
    Name: reorder_level, Length: 75, dtype: float64




```python
products['weight'].fillna(products['weight'].mean())
```




    0      0.450000
    1      0.500000
    2      0.600000
    3      2.800000
    4      0.200000
    5      0.900000
    6     10.000000
    7      3.500000
    8      3.835714
    9      2.000000
    10     1.300000
    11     0.700000
    12     1.500000
    13     0.300000
    14     3.500000
    15     0.500000
    16     1.000000
    17     0.600000
    18     0.400000
    19     6.700000
    20    25.000000
    21     3.835714
    22     8.500000
    23    12.000000
    24     0.350000
    25     0.900000
    26     4.500000
    27    15.000000
    28     0.500000
    29     3.200000
    Name: weight, dtype: float64



## *For categorical columns with missing values, replace with most frequent value


```python
sales.isna().sum()
sales.head()
sales['payment_method'].mode()[0]
sales['payment_method'].fillna(sales['payment_method'].mode()[0])
```




    0     Credit Card
    1     credit card
    2      DEBIT CARD
    3            Cash
    4              CC
    5            Visa
    6          PayPal
    7       Apple Pay
    8           Debit
    9            Cash
    10    Credit Card
    11             DC
    12           cash
    13    Credit Card
    14     Debit Card
    15         paypal
    16       ApplePay
    17           Cash
    18    Credit Card
    19    CREDIT CARD
    20     Debit Card
    21             PP
    22           Cash
    23         Credit
    24      GooglePay
    25    Credit Card
    26     debit card
    27           Cash
    28         PayPal
    29     Debit Card
    30    Credit Card
    31           Cash
    32    Credit Card
    33     Debit Card
    34    Credit Card
    35           Cash
    36         PayPal
    37     google pay
    38    Credit Card
    39           CASH
    Name: payment_method, dtype: str



## *For date columns with missing values, use forward fill or backward fill as appropriate


```python
stores.isna().sum()
stores
stores['opening_date']
stores['opening_date'].ffill()
```




    0     2005-05-20
    1     2007-08-15
    2     2004-03-10
    3     2008-11-05
    4     2010-06-30
    5     2009-09-12
    6     2012-04-22
    7     2006-07-18
    8     2006-07-18
    9     2014-10-09
    10    2011-02-14
    11    2015-08-27
    12    2016-12-03
    13    2013-05-11
    14    2018-09-25
    Name: opening_date, dtype: str




```python
sales.isna().sum()
sales['date']
sales['date'].ffill()
```




    0     2022-01-15
    1     2022-01-16
    2     2022-01-18
    3     2022-01-20
    4     2022-01-22
    5     2022-02-01
    6     2022-02-03
    7     2022-02-05
    8     2022-02-08
    9     2022-02-10
    10    2022-02-15
    11    2022-02-19
    12    2022-02-22
    13    2022-03-01
    14    2022-03-05
    15    2022-03-10
    16    2022-03-15
    17    2022-03-20
    18    2022-03-25
    19    2022-04-01
    20    2022-04-05
    21    2022-04-10
    22    2022-04-15
    23    2022-04-20
    24    2022-04-25
    25    2022-05-01
    26    2022-05-05
    27    2022-05-10
    28    2022-05-15
    29    2022-05-20
    30    2022-05-20
    31    2022-06-01
    32    2022-06-05
    33    2022-06-10
    34    2022-06-15
    35    2022-06-20
    36    2022-06-25
    37    2022-07-01
    38    2022-07-05
    39    2022-07-10
    Name: date, dtype: str




```python
customers.isnull().sum()
customers['registration_date']
customers['registration_date'].ffill()
```




    0     2021-03-15
    1     2020-11-02
    2     2021-05-20
    3     2021-05-20
    4     2020-09-12
    5     2021-02-28
    6     2021-01-17
    7     2020-10-05
    8     2021-06-30
    9     2020-08-22
    10    2021-04-09
    11    2020-12-27
    12    2021-07-14
    13    2020-07-18
    14    2021-01-03
    15    2021-01-03
    16    2020-10-19
    17    2021-03-01
    18    2020-09-05
    19    2021-05-12
    20    2020-11-30
    21    2021-02-14
    22    2020-08-08
    23    2021-04-25
    24    2021-04-25
    25    2020-07-01
    26    2020-07-01
    27    2021-06-17
    28    2020-09-30
    29    2021-01-28
    30    2020-10-15
    Name: registration_date, dtype: str




```python
inventory.head()
inventory.isnull().sum()
inventory['last_restock_date']
# inven = inventory['last_restock_date'].ffill()
# inven.tolist()
inventory['last_restock_date'].ffill()
```




    0     2022-10-15
    1     2022-11-02
    2     2022-09-30
    3     2022-10-20
    4     2022-10-20
             ...    
    70    2022-10-16
    71    2022-09-25
    72    2022-11-22
    73    2022-10-01
    74    2022-10-01
    Name: last_restock_date, Length: 75, dtype: str



# 5. Removing Duplicates

## * Check for and remove any duplicate entries in the customers and products dataframes


```python
# cheack for duplicate customer records by customer_id
customers.duplicated().sum()
customers['customer_id'].duplicated().sum()
customers['customer_id'].duplicated()
customers[customers['customer_id'].duplicated(keep=False)]
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>customer_id</th>
      <th>first_name</th>
      <th>last_name</th>
      <th>email</th>
      <th>phone</th>
      <th>address</th>
      <th>city</th>
      <th>state</th>
      <th>zip_code</th>
      <th>registration_date</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>25</th>
      <td>26</td>
      <td>Betty</td>
      <td>Lewis</td>
      <td>betty.lewis@gmail.com</td>
      <td>5551597532</td>
      <td>753 MacArthur Blvd</td>
      <td>Baltimore</td>
      <td>Maryland</td>
      <td>21202</td>
      <td>2020-07-01</td>
    </tr>
    <tr>
      <th>26</th>
      <td>26</td>
      <td>Betty</td>
      <td>Lewis</td>
      <td>blewis23@gmail.com</td>
      <td>555 159 7532</td>
      <td>753 MacArthur Boulevard</td>
      <td>Baltimore</td>
      <td>MD</td>
      <td>21202</td>
      <td>2020-07-01</td>
    </tr>
  </tbody>
</table>
</div>




```python
customers[customers['customer_id'].duplicated(keep=False)]

# Keeps most recent entry for customer

customers.drop_duplicates(subset='customer_id', keep='last')
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>customer_id</th>
      <th>first_name</th>
      <th>last_name</th>
      <th>email</th>
      <th>phone</th>
      <th>address</th>
      <th>city</th>
      <th>state</th>
      <th>zip_code</th>
      <th>registration_date</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>1</td>
      <td>James</td>
      <td>Smith</td>
      <td>james.smith@gmail.com</td>
      <td>555-123-4567</td>
      <td>123 Main St</td>
      <td>New York</td>
      <td>NY</td>
      <td>10001</td>
      <td>2021-03-15</td>
    </tr>
    <tr>
      <th>1</th>
      <td>2</td>
      <td>Mary</td>
      <td>Johnson</td>
      <td>NaN</td>
      <td>212.555.6789</td>
      <td>456 Park Ave</td>
      <td>New York</td>
      <td>NY</td>
      <td>10022</td>
      <td>2020-11-02</td>
    </tr>
    <tr>
      <th>2</th>
      <td>3</td>
      <td>John</td>
      <td>Williams</td>
      <td>jwilliams@yahoo.com</td>
      <td>(555) 987-6543</td>
      <td>789 Broadway</td>
      <td>Los Angeles</td>
      <td>California</td>
      <td>90001-1234</td>
      <td>2021-05-20</td>
    </tr>
    <tr>
      <th>3</th>
      <td>4</td>
      <td>Patricia</td>
      <td>Brown</td>
      <td>pbrown@hotmail.com</td>
      <td>5551234567</td>
      <td>321 Elm St</td>
      <td>Chicago</td>
      <td>IL</td>
      <td>60601</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>4</th>
      <td>5</td>
      <td>Robert</td>
      <td>Jones</td>
      <td>rjones23@gmail.com</td>
      <td>555-987-3456</td>
      <td>555 Pine St</td>
      <td>Houston</td>
      <td>TX</td>
      <td>77002</td>
      <td>2020-09-12</td>
    </tr>
    <tr>
      <th>5</th>
      <td>6</td>
      <td>Jennifer</td>
      <td>Miller</td>
      <td>jmiller@outlook.com</td>
      <td>NaN</td>
      <td>898 Cedar Dr</td>
      <td>Phoenix</td>
      <td>AZ</td>
      <td>85001</td>
      <td>2021-02-28</td>
    </tr>
    <tr>
      <th>6</th>
      <td>7</td>
      <td>Michael</td>
      <td>Davis</td>
      <td>mdavis@gmail.com</td>
      <td>555.432.7654</td>
      <td>742 Maple Ave</td>
      <td>Philadelphia</td>
      <td>PA</td>
      <td>19103</td>
      <td>2021-01-17</td>
    </tr>
    <tr>
      <th>7</th>
      <td>8</td>
      <td>Linda</td>
      <td>Garcia</td>
      <td>lgarcia@yahoo.com</td>
      <td>555 876 2345</td>
      <td>953 Oak Ln</td>
      <td>San Antonio</td>
      <td>Texas</td>
      <td>78205</td>
      <td>2020-10-05</td>
    </tr>
    <tr>
      <th>8</th>
      <td>9</td>
      <td>William</td>
      <td>Rodriguez</td>
      <td>wrodriguez@hotmail.com</td>
      <td>5558889999</td>
      <td>159 Washington Blvd</td>
      <td>San Diego</td>
      <td>CA</td>
      <td>92101</td>
      <td>2021-06-30</td>
    </tr>
    <tr>
      <th>9</th>
      <td>10</td>
      <td>Elizabeth</td>
      <td>Wilson</td>
      <td>ewilson@gmail.com</td>
      <td>(555) 333-2211</td>
      <td>753 Lincoln Rd</td>
      <td>Dallas</td>
      <td>TX</td>
      <td>75201</td>
      <td>2020-08-22</td>
    </tr>
    <tr>
      <th>10</th>
      <td>11</td>
      <td>David</td>
      <td>Martinez</td>
      <td>dmartinez@yahoo.com</td>
      <td>555-111-3333</td>
      <td>246 Jefferson Ave</td>
      <td>San Jose</td>
      <td>CA</td>
      <td>95113</td>
      <td>2021-04-09</td>
    </tr>
    <tr>
      <th>11</th>
      <td>12</td>
      <td>Barbara</td>
      <td>Anderson</td>
      <td>NaN</td>
      <td>555.444.9876</td>
      <td>135 Madison St</td>
      <td>Austin</td>
      <td>TX</td>
      <td>NaN</td>
      <td>2020-12-27</td>
    </tr>
    <tr>
      <th>12</th>
      <td>13</td>
      <td>Richard</td>
      <td>Taylor</td>
      <td>rtaylor@outlook.com</td>
      <td>5552223333</td>
      <td>864 Adams Ct</td>
      <td>Jacksonville</td>
      <td>FL</td>
      <td>32202</td>
      <td>2021-07-14</td>
    </tr>
    <tr>
      <th>13</th>
      <td>14</td>
      <td>Susan</td>
      <td>Thomas</td>
      <td>sthomas45@gmail.com</td>
      <td>NaN</td>
      <td>579 Monroe Pl</td>
      <td>Fort Worth</td>
      <td>TX</td>
      <td>76102</td>
      <td>2020-07-18</td>
    </tr>
    <tr>
      <th>14</th>
      <td>15</td>
      <td>Joseph</td>
      <td>Hernandez</td>
      <td>jhernandez@yahoo.com</td>
      <td>555-777-8888</td>
      <td>951 Jackson Dr</td>
      <td>Columbus</td>
      <td>OH</td>
      <td>43215</td>
      <td>2021-01-03</td>
    </tr>
    <tr>
      <th>15</th>
      <td>16</td>
      <td>Jessica</td>
      <td>Moore</td>
      <td>jmoore@hotmail.com</td>
      <td>555.666.1234</td>
      <td>357 Tyler St</td>
      <td>Charlotte</td>
      <td>North Carolina</td>
      <td>28202</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>16</th>
      <td>17</td>
      <td>Thomas</td>
      <td>Martin</td>
      <td>tmartin@gmail.com</td>
      <td>(555) 444-5678</td>
      <td>159 Polk Ave</td>
      <td>San Francisco</td>
      <td>CA</td>
      <td>94102</td>
      <td>2020-10-19</td>
    </tr>
    <tr>
      <th>17</th>
      <td>18</td>
      <td>Sarah</td>
      <td>Jackson</td>
      <td>sjackson@yahoo.com</td>
      <td>5557890123</td>
      <td>753 Harrison Rd</td>
      <td>Indianapolis</td>
      <td>IN</td>
      <td>46204</td>
      <td>2021-03-01</td>
    </tr>
    <tr>
      <th>18</th>
      <td>19</td>
      <td>Charles</td>
      <td>Thompson</td>
      <td>cthompson@outlook.com</td>
      <td>555-321-6547</td>
      <td>951 Van Buren St</td>
      <td>Seattle</td>
      <td>Washington</td>
      <td>98101</td>
      <td>2020-09-05</td>
    </tr>
    <tr>
      <th>19</th>
      <td>20</td>
      <td>Karen</td>
      <td>White</td>
      <td>kwhite88@gmail.com</td>
      <td>555.789.4561</td>
      <td>357 Fillmore Dr</td>
      <td>Denver</td>
      <td>CO</td>
      <td>80202</td>
      <td>2021-05-12</td>
    </tr>
    <tr>
      <th>20</th>
      <td>21</td>
      <td>Christopher</td>
      <td>Lopez</td>
      <td>clopez@yahoo.com</td>
      <td>555 456 7890</td>
      <td>159 Pierce Ave</td>
      <td>Boston</td>
      <td>MA</td>
      <td>02108</td>
      <td>2020-11-30</td>
    </tr>
    <tr>
      <th>21</th>
      <td>22</td>
      <td>Nancy</td>
      <td>Lee</td>
      <td>nlee@hotmail.com</td>
      <td>5559876543</td>
      <td>753 Hayes Blvd</td>
      <td>Portland</td>
      <td>Oregon</td>
      <td>97201</td>
      <td>2021-02-14</td>
    </tr>
    <tr>
      <th>22</th>
      <td>23</td>
      <td>Daniel</td>
      <td>Gonzalez</td>
      <td>dgonzalez@gmail.com</td>
      <td>(555) 123-7890</td>
      <td>951 Grant St</td>
      <td>Las Vegas</td>
      <td>NV</td>
      <td>89101</td>
      <td>2020-08-08</td>
    </tr>
    <tr>
      <th>23</th>
      <td>24</td>
      <td>Margaret</td>
      <td>Harris</td>
      <td>mharris@yahoo.com</td>
      <td>555-321-6789</td>
      <td>357 Sherman Rd</td>
      <td>Detroit</td>
      <td>MI</td>
      <td>48226</td>
      <td>2021-04-25</td>
    </tr>
    <tr>
      <th>24</th>
      <td>25</td>
      <td>Matthew</td>
      <td>Clark</td>
      <td>mclark@outlook.com</td>
      <td>555.654.9870</td>
      <td>159 Sheridan Dr</td>
      <td>Nashville</td>
      <td>TN</td>
      <td>37201</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>26</th>
      <td>26</td>
      <td>Betty</td>
      <td>Lewis</td>
      <td>blewis23@gmail.com</td>
      <td>555 159 7532</td>
      <td>753 MacArthur Boulevard</td>
      <td>Baltimore</td>
      <td>MD</td>
      <td>21202</td>
      <td>2020-07-01</td>
    </tr>
    <tr>
      <th>27</th>
      <td>27</td>
      <td>Steven</td>
      <td>Robinson</td>
      <td>srobinson@yahoo.com</td>
      <td>555-951-7532</td>
      <td>951 Hooker St</td>
      <td>Louisville</td>
      <td>KY</td>
      <td>40202</td>
      <td>2021-06-17</td>
    </tr>
    <tr>
      <th>28</th>
      <td>28</td>
      <td>Dorothy</td>
      <td>Walker</td>
      <td>dwalker@hotmail.com</td>
      <td>5553579514</td>
      <td>357 Halsted Ave</td>
      <td>Milwaukee</td>
      <td>WI</td>
      <td>53202</td>
      <td>2020-09-30</td>
    </tr>
    <tr>
      <th>29</th>
      <td>29</td>
      <td>Anthony</td>
      <td>Perez</td>
      <td>NaN</td>
      <td>555.753.9512</td>
      <td>159 Ashland Dr</td>
      <td>Albuquerque</td>
      <td>NM</td>
      <td>87102</td>
      <td>2021-01-28</td>
    </tr>
    <tr>
      <th>30</th>
      <td>30</td>
      <td>Lisa</td>
      <td>Hall</td>
      <td>lhall@gmail.com</td>
      <td>(555) 951-7530</td>
      <td>753 Morgan St</td>
      <td>Kansas City</td>
      <td>MO</td>
      <td>64101</td>
      <td>2020-10-15</td>
    </tr>
  </tbody>
</table>
</div>




```python
# Checked product_id and product name, and show no duplicate rows for same product

products.head()
products.sort_values('product_name')

products.duplicated().sum()
products['product_name'].duplicated().sum()
products['product_id'].duplicated().sum()
```




    np.int64(0)



# Discussion Questions

### 1. What are the key advantages of using Pandas for data cleaning compared to other methods?

#####        * Pandas has many built in functions that allow for summary viewing instead of line-by-line

### 2. How would your approach to handling missing values differ if the missing data was not random but had a pattern or meaning?

#####        * Would assign a value based on the data i was dealing with or keep as null if null values had meaning.

### 3. What types of data quality issues might not be immediately visible through simple DataFrame inspection methods?

#####        *formatting (upper or lowercase)
#####        *If there ar 0 valeues in rows that need to be divided by

### 4. How would you document your data cleaning process to ensure reproducibility?

#####        * show function used and what i am trying to analyze

### 5. In what scenarios might it be better to remove rows with missing values rather than imputing them?

#####        * When dealing with a large dataset where 1 record does not affect the analysis
#####        * 0 values in rows that need to use for calulations (divide by 0)


```python

```
