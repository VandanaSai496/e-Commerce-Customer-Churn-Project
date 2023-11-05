# E-Commerce Customer Churn Prediction Project

## Project Overview_
**
E-commerce platforms are bustling digital markets, with customers buzzing around like busy bees. However, sometimes bees find new gardens, leaving the old one behind. 
This project, revolving around a vibrant e-commerce hub named Olist from Brazil, seeks to spot the bees planning to buzz away before they make the move.

By peering into the digital trails of customer interactions, purchases, and personal details, we aim to craft a crystal ball—a predictive model. 
This model seeks to unveil which customers might bid goodbye, helping us devise nifty strategies to keep them buzzing in our garden.

In this endeavor, we'll dig into the tales told by data, seeking patterns that hint at a customer's intent to stay or stray. With this foresight, we aim to create a buzz, offering tailored shopping experiences 
to keep our digital garden a lively and thriving marketplace.

Join us on this exciting venture to keep the market bustling, using the magic of data to foster enduring customer bonds.**

## Table of Contents
1. [Data Collection](#data-collection)
2. [Data Cleaning and Preparation](#data-cleaning-and-preparation)
3. [Exploratory Data Analysis](#exploratory-data-analysis)
4. [Data Modeling](#data-modeling)
5. [Evaluation](#evaluation)
6. [Deployment](#deployment)
7. [Dashboard Creation and Visualization](#dashboard-creation-and-visualization)
8. [Recommendations & Insights](#recommendations-&-insights)
9. [Documentation and Presentation](#documentation-and-presentation)

## Data Collection

Once upon a digital dawn, in the heart of the vibrant marketplace of Olist, lay a treasure trove of tales waiting to be told.
These tales were etched in strings of data, woven through every click, every purchase, and every digital whisper shared by the patrons of this virtual bazaar.
Our quest was clear - to collect these digital tales, analyze the yarn of interactions, and seek the prophecies of customer churn. 

But first, we needed to gather the threads of data that would guide our way through the maze of customer behaviors.

With sturdy baskets of SQL and Python in our hands, we ventured into the vast fields of databases where data grains were ripe for the picking. 
The fields were vast, with rows and columns stretching as far as the eye could see. Our baskets soon filled with rich data grains—each row a narrative, each column a characteristic.

We embarked on gathering:
1. **Demographic Tales**: Uncovering age, gender, and location, revealing the diverse faces of our marketplace.
2. **Account Chronicles**: Delving into account activities, tracing the rhythm of purchases and preferences.
3. **Service Narratives**: Exploring chosen services, painting a canvas of customer experiences.

In the bustling digital marketplace of Olist, every click and purchase holds a story. Our quest begins with gathering these digital tales to uncover the whispers of customer churn. 
Armed with tools like SQL and Python, we ventured into the vast realm of databases.

If this data was stored in a SQL database: 

# Create a query to extract and combine necessary data from the tables
WITH combined_data AS (
    -- Join orders table with customers, payments, and reviews tables
    SELECT o.order_id, o.customer_id, o.order_status, o.order_purchase_timestamp,
           c.customer_unique_id, c.customer_zip_code_prefix,
           p.payment_type, p.payment_value,
           r.review_score
    FROM orders o
    JOIN customers c ON o.customer_id = c.customer_id
    JOIN payments p ON o.order_id = p.order_id
    JOIN reviews r ON o.order_id = r.order_id
)
--Execute the query to create a combined dataset
SELECT * FROM combined_data;

--Moving to python! Import the necessary libraries: 
import pandas as pd
import sqlalchemy as db

##Create a connection to your database
engine = db.create_engine('database-url')

--Define the SQL query (as above)
query = """
    WITH combined_data AS (
        -- ... (same query as above)
    )
    SELECT * FROM combined_data;
"""

--Load data into a pandas DataFrame
combined_data = pd.read_sql(query, engine)

Now, 'combined_data' is a data frame containing all the data you need for your analysis

If the data was in a Client Server, Third-Party Administrators, Data Centers, Cloud Services, we can use APIs, here's how we get the data from APIs: 

# Through APIs
import requests
import json

--Define the API endpoint and parameters
url = 'https://api.example.com/data'
params = {
    'api_key': 'your_api_key',
    'other_param': 'value'
}

--Make the HTTP request
response = requests.get(url, params=params)

--Check for a valid response
if response.status_code == 200:
    # Parse the JSON data from the response
    data = response.json()
else:
    print(f'Failed to retrieve data: {response.status_code}')

Since APIs return data in JSON Format, we can parse those JSON's through python using pandas library and retrieve it in a structured format: 

import pandas as pd

--Convert the JSON data to a pandas DataFrame
df = pd.DataFrame(data)

Now, 'df' is a DataFrame containing the data from the API

# Through FileSystems
For now, we have all the data in the Filesystem Format (Excel or CSV), we don't have to go through these steps. Here's the dataset: https://www.kaggle.com/datasets/olistbr/brazilian-ecommerce/data
Go ahead and download this and now the fun begins. 

With these data grains in our basket, we were ready to sift through them, hoping to unveil patterns and prophecies of customer loyalty and wanderlust, setting the stage for our analytical adventure.

## Data Cleaning and Preparation
- Description of the data cleaning and preparation process.
- Tools used: Excel, SQL, Python (pandas).

** 1) Let's load the data from CSV into pandas dataFrames **

import pandas as pd

# Load each CSV file into a separate DataFrame
olist_customers_df = pd.read_csv('olist_customers_dataset.csv')
olist_geolocation_df = pd.read_csv('olist_geolocation_dataset.csv')
olist_order_items_df = pd.read_csv('olist_order_items_dataset.csv')
olist_order_payments_df = pd.read_csv('olist_order_payments_dataset.csv')
olist_order_reviews_df = pd.read_csv('olist_order_reviews_dataset.csv')
olist_orders_df = pd.read_csv('olist_orders_dataset.csv')
olist_products_df = pd.read_csv('olist_products_dataset.csv')
olist_sellers_df = pd.read_csv('olist_sellers_dataset.csv')
olist_product_category_name_translation_df = pd.read_csv('product_category_name_translation.csv')

# Now each DataFrame contains the data from the respective CSV file

**
2) Let's Examine the Data: **

customers_df.head()
customers_df.info()











## Exploratory Data Analysis
- Description of the exploratory data analysis process, including visualizations.
- Tools used: Python (matplotlib, seaborn, plotly).

## Data Modeling
- Description of the data modeling process, including the machine learning algorithms used.
- Tools used: Python (scikit-learn, statsmodels).

## Evaluation
- Description of the model evaluation, including metrics and model tuning.
- Tools used: Python (scikit-learn).

## Deployment
- Description of the deployment process.
- Tools used: AWS, Azure, Google Cloud, Flask.

## Dashboard Creation and Visualization
- Description of the dashboard creation and visualization process.
- Tools used: Tableau, Power BI, Python (Dash, Bokeh).

## Recommendations & Insights
- Description of the recommendations and insights derived from the analysis.

## Documentation and Presentation
- Description of how the project was documented and presented, including links to presentations, reports, and code repositories.

## Getting Started
- Instructions on how to replicate or contribute to the project, including required software and dependencies.

## Contributing
- Information on how others can contribute to the project.

## Contact
- Your contact information.
vandanasai496@gmail.com
