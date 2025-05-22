# 🛠️ Project: E-Commerce Review Aggregation ETL

## 📝 Objective

Design and implement an end-to-end ETL pipeline that collects product review data from a public dataset, processes and transforms the data, and loads it into a PostgreSQL database. The pipeline should support analytical queries to derive insights such as product popularity, sentiment trends, and review volume.

---

## 🔗 Dataset

Use the following public dataset(Do it for one dataset only first):
**Amazon Fine Food Reviews**
📥 Source: [https://www.kaggle.com/datasets/snap/amazon-fine-food-reviews](https://www.kaggle.com/datasets/snap/amazon-fine-food-reviews)


**Consumer Reviews of Amazon Products**
📥 Source: [https://www.kaggle.com/datasets/datafiniti/consumer-reviews-of-amazon-products](https://www.kaggle.com/datasets/datafiniti/consumer-reviews-of-amazon-products)


**Flipkart Products**
📥 Source: [https://www.kaggle.com/datasets/PromptCloudHQ/flipkart-products](https://www.kaggle.com/datasets/PromptCloudHQ/flipkart-products)


**FakeStore API**
📥 Source: [https://fakestoreapi.com/products](https://fakestoreapi.com/products)


This dataset includes:

* Product ID and name
* User ID
* Review scores (1 to 5)
* Review titles and texts
* Timestamps

---

## ✅ Required Tasks

### 1. Extract

* Read the dataset in its original form (CSV file) using Python.
* Ensure the extraction process is automated and reusable, not hardcoded to a specific local file path.

---

### 2. Transform

Perform the following transformations using Python:

* Remove any **duplicate** records based on a logical combination of columns such as `UserID`, `ProductID`, and `ReviewText`.
* Clean **null or missing values**, especially in review content and ratings.
* Normalize **timestamp** or date formats to `YYYY-MM-DD`.
* Validate and constrain **rating values** to a 1–5 integer scale.
* Derive and add the following new fields:

  * `review_length`: Number of words or characters in the review body.
  * `sentiment_label`: Based on rating value

    * Rating ≥ 4 → `positive`
    * Rating = 3 → `neutral`
    * Rating ≤ 2 → `negative`

---

### 3. Load

* Design and create a PostgreSQL schema with at least two normalized tables:

  * `products(product_id, product_name)`
  * `reviews(review_id, product_id, user_id, rating, review_text, review_length, sentiment_label, review_date)`
* Use Python to load the cleaned and transformed data into the appropriate PostgreSQL tables.
* Ensure foreign key constraints are maintained between `reviews` and `products`.

---

### 4. Validation & Analysis

Create and execute SQL queries to verify the data load and to demonstrate insights:

* Top 10 products with the highest average rating.
* Distribution of sentiment labels (positive/neutral/negative).
* Average review length per rating score.
* Number of distinct users who submitted reviews per product.

---

## 📂 Deliverables

* Python scripts for:

  * Extracting and transforming data
  * Loading data into PostgreSQL
* SQL script for table creation
* SQL file or notebook with validation queries
* A `README.md` file that explains:

  * Environment setup
  * How to run the scripts
  * Transformation logic overview

---

## 🎁 Bonus (Optional Extension)

Extend the project to support integration from multiple data sources:

* Include at least two more product sources:
* Standardize data across platforms (e.g., unify product categories, rating scales, price formats).
* Add a `source` column to track where each product or review came from.
* Expand the PostgreSQL schema to support cross-source data with consistency.
* Write queries comparing product prices, rating trends, or review counts across platforms.
