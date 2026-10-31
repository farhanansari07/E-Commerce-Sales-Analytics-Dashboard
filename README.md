# E-Commerce Customer Shopping Behavior Analysis

An end-to-end data analytics project that explores customer shopping
behavior using **Python, PostgreSQL, and Power BI**. The project covers
data inspection, cleaning, feature engineering, database loading, and
dashboard-based analysis.

## Project Overview

Understanding customer purchasing patterns helps businesses make better
decisions about product categories, promotions, customer engagement, and
the overall shopping experience.

This project analyzes a customer shopping behavior dataset containing
**3,900 records and 18 original columns**. Python is used to clean and
prepare the data, PostgreSQL is used to store the processed dataset, and
Power BI is used to build an interactive dashboard.

## Tech Stack

  Technology         Purpose
  ------------------ -------------------------------------------------
  Python             Data preparation and analysis
  Pandas             Data manipulation and cleaning
  Jupyter Notebook   Exploratory analysis and workflow documentation
  PostgreSQL         Relational data storage
  SQLAlchemy         Database connectivity
  psycopg2           PostgreSQL driver
  Power BI           Interactive data visualization

## Repository Structure

``` text
E-Commerce-Sales-Analytics-Dashboard/
│
├── Customer_Shopping_Behavior_Analysis.ipynb
├── customer_shopping_behavior.csv
└── customer_behavior_dashboard.pbix
```

## Dataset

The dataset contains **3,900 customer shopping records** with the
following original attributes:

-   Customer ID and age
-   Gender and location
-   Purchased item and product category
-   Purchase amount (USD)
-   Size, color, and season
-   Review rating
-   Subscription status
-   Shipping type
-   Discount and promo-code usage
-   Previous purchases
-   Payment method
-   Purchase frequency

The data includes customer demographics, transaction details, product
preferences, and purchasing patterns.

## Data Preparation and Analysis

The workflow implemented in the Jupyter Notebook includes:

1.  **Data loading:** Importing the CSV dataset into a Pandas DataFrame.
2.  **Data inspection:** Reviewing column types, dataset dimensions,
    summary statistics, and missing values.
3.  **Missing-value treatment:** Filling the 37 missing values in
    `Review Rating` using the median rating within each product
    category.
4.  **Column standardization:** Converting column names to lowercase
    snake_case and renaming the purchase amount field for easier use.
5.  **Feature engineering:**
    -   Creating an `age_group` column using quartile-based age
        segmentation.
    -   Creating `purchase_frequency_days` by mapping purchase-frequency
        labels to approximate day intervals.
6.  **Redundancy check:** Comparing `discount_applied` and
    `promo_code_used`; because the values match throughout this dataset,
    the duplicate `promo_code_used` column is removed.
7.  **Database loading:** Connecting to PostgreSQL and loading the
    processed DataFrame into the `customer` table in the
    `customer_behavior` database.

## Database Setup

The notebook uses PostgreSQL to store the cleaned dataset.

### 1. Create a database

Create a PostgreSQL database named:

``` sql
CREATE DATABASE customer_behavior;
```

### 2. Install Python dependencies

``` bash
pip install pandas sqlalchemy psycopg2-binary jupyter
```

### 3. Configure the connection

Update the notebook to read database credentials from environment
variables or another secure configuration method. Do not commit
passwords or other credentials to GitHub.

Example connection setup:

``` python
import os
from sqlalchemy import create_engine
from sqlalchemy.engine import URL

connection_url = URL.create(
    drivername="postgresql+psycopg2",
    username=os.environ["DB_USER"],
    password=os.environ["DB_PASSWORD"],
    host=os.getenv("DB_HOST", "localhost"),
    port=int(os.getenv("DB_PORT", "5432")),
    database="customer_behavior"
)

engine = create_engine(connection_url)
```

The notebook writes the cleaned DataFrame to a PostgreSQL table named
`customer`.

## Power BI Dashboard

The repository includes `customer_behavior_dashboard.pbix`, a Power BI
report built for exploring the customer shopping behavior dataset.

Open the `.pbix` file using **Microsoft Power BI Desktop** to view and
interact with the report. If the report uses a local PostgreSQL
connection, configure the corresponding data-source credentials and
refresh the data as needed.

## Getting Started

1.  Clone this repository:

    ``` bash
    git clone https://github.com/farhanansari07/E-Commerce-Sales-Analytics-Dashboard.git
    ```

2.  Move into the project directory:

    ``` bash
    cd E-Commerce-Sales-Analytics-Dashboard
    ```

3.  Install the required Python packages:

    ``` bash
    pip install pandas sqlalchemy psycopg2-binary jupyter
    ```

4.  Make sure the CSV file is in the project directory and configure
    PostgreSQL credentials securely.

5.  Launch Jupyter Notebook:

    ``` bash
    jupyter notebook
    ```

6.  Open `Customer_Shopping_Behavior_Analysis.ipynb` and run the
    notebook cells in order.

7.  Open `customer_behavior_dashboard.pbix` in Power BI Desktop to
    explore the dashboard.

## Key Learnings

-   Data inspection and preprocessing with Pandas
-   Handling missing values using group-wise statistical imputation
-   Feature engineering and customer segmentation
-   Identifying redundant attributes in a dataset
-   Connecting Python applications to PostgreSQL using SQLAlchemy
-   Preparing structured data for business intelligence and
    visualization
-   Building a workflow that connects Python, a relational database, and
    Power BI

## Future Improvements

-   Add documented SQL queries for deeper customer and product analysis.
-   Include dashboard screenshots and descriptions of its key visuals.
-   Add automated data validation and a repeatable data-refresh
    workflow.
-   Expand the analysis with customer segmentation and cohort-based
    insights.

## Author

**Farhan Ansari**

-   GitHub: [@farhanansari07](https://github.com/farhanansari07)
-   Project Repository: [E-Commerce Sales Analytics
    Dashboard](https://github.com/farhanansari07/E-Commerce-Sales-Analytics-Dashboard)

------------------------------------------------------------------------

If you find this project useful, consider giving the repository a ⭐.
