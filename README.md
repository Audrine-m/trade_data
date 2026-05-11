# Python API Data Extraction and CSV Export Project

## Overview

This project demonstrates how to:

* Fetch data from APIs using Python
* Work with JSON data
* Convert JSON data into Pandas DataFrames
* Clean and organize datasets
* Export datasets into CSV format
* Prepare datasets for further data analysis

The project uses both a custom GitHub-hosted JSON dataset and public APIs from DummyJSON.

---

# Technologies Used

* Python
* Pandas
* Requests
* Jupyter Notebook

---

# Project Workflow

## 1. Import Required Libraries

The project begins by importing the required Python libraries.

```python
import requests
import pandas as pd
```

### Purpose

* `requests` is used to fetch data from APIs.
* `pandas` is used for data cleaning and analysis.

---

# 2. Fetch Trading Data from GitHub

A JSON dataset is fetched directly from a GitHub repository.

```python
url = "https://raw.githubusercontent.com/Audrine-m/trade_data/refs/heads/main/MOCK_DATA.json"
r = requests.get(url)
MOCK_DATA = r.json()
Trading_data = MOCK_DATA["Trading_data"]
```

### What Happens Here?

1. A request is sent to the GitHub-hosted JSON file.
2. The response is converted into JSON format.
3. The `Trading_data` section is extracted.

---

# 3. Fetch Product Data from DummyJSON API

The project also retrieves product information from the DummyJSON API.

```python
product_url = "https://dummyjson.com/products"
product_data = requests.get(product_url)
dummy_data = product_data.json()
products = dummy_data["products"]
```

### Purpose

This step demonstrates how to work with public APIs and extract nested JSON data.

---

# 4. Fetch Cart Data from DummyJSON API

Cart information is collected from another endpoint.

```python
carts_url = "https://dummyjson.com/carts"
carts_data = requests.get(carts_url)
data = carts_data.json()
carts = data["carts"]
```

### Purpose

This section demonstrates how to access and organize multiple datasets from APIs.

---

# 5. Convert JSON Data into Pandas DataFrames

The extracted datasets are converted into DataFrames.

```python
df = pd.DataFrame(Trading_data)
df_products = pd.DataFrame(products)
df_carts = pd.DataFrame(carts)
```

### Why Use DataFrames?

Pandas DataFrames make it easier to:

* Analyze data
* Clean datasets
* Filter records
* Export files
* Perform statistical operations

---

# 6. Clean and Reset Indexes

The project removes unnecessary index columns before exporting the datasets.

```python
if 'index' in df.columns:
    df = df.drop(columns=['index'])

df.reset_index(drop=True, inplace=True)
```

### Purpose

This ensures:

* Clean CSV files
* No duplicate index columns
* Better compatibility with Excel and analysis tools

---

# 7. Export Data to CSV Files

The cleaned datasets are exported as CSV files.

```python
df.to_csv("trading_data.csv", index=False)
df_products.to_csv("products.csv", index=False)
df_carts.to_csv("carts.csv", index=False)
```

### Output Files

The project generates:

* `trading_data.csv`
* `products.csv`
* `carts.csv`

---

# Skills Demonstrated

This project demonstrates practical data analytics skills including:

* API integration
* JSON handling
* Data cleaning
* Data transformation
* Data export
* Working with Pandas
* Basic ETL (Extract, Transform, Load) processes

---

# How to Run the Project

## 1. Clone the Repository

```bash
git clone https://github.com/yourusername/your-repository-name.git
```

## 2. Navigate into the Project Folder

```bash
cd your-repository-name
```

## 3. Install Required Libraries

```bash
pip install pandas requests
```

## 4. Run the Notebook

Open the Jupyter Notebook and run all cells.

---

# Future Improvements

Possible improvements for this project include:

* Data visualization using Matplotlib or Seaborn
* SQL database integration
* Automated data pipelines
* API error handling
* Dashboard creation using Power BI or Streamlit
* Data validation checks

---

# Conclusion

This project provides a beginner-friendly introduction to working with APIs and data processing in Python. It demonstrates how raw JSON data can be transformed into structured CSV datasets that are ready for analysis and reporting.
