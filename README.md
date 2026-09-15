# Supply-Chain-Delivery-Profitability-Analysis
data analytics project supply chain delivery &amp; profitability analysis using Python

## Overview

This project analyzes supply chain and order data to understand **delivery performance, order delays, operational bottlenecks, and profitability**.

Using Python, Pandas, NumPy, Matplotlib, and Seaborn, the project cleans and analyzes **180K+ supply-chain records**, creates meaningful operational metrics, identifies major delay patterns, and builds a **Random Forest classification model** to predict late-delivery risk.

The goal is to turn raw supply-chain data into **actionable business insights** that can help improve delivery performance and operational efficiency.

---

## Project Objectives

* Analyze overall supply-chain delivery performance.
* Identify major causes and patterns of delivery delays.
* Compare delays across shipping modes, customer segments, departments, regions, and order status.
* Analyze the relationship between delivery performance and profitability.
* Identify time-based patterns in delivery delays.
* Build a machine-learning model to predict **Late Delivery Risk**.

---

## Dataset

**Dataset:** `DataCoSupplyChainDataset.csv`

The original dataset contains:

* **180,519 records**
* **53 columns**

The dataset includes information about:

* Orders
* Customers
* Products
* Sales
* Profit
* Shipping
* Delivery status
* Shipping mode
* Customer segments
* Departments
* Order regions
* Order dates
* Shipping dates

## After data cleaning and feature selection, the working dataset was reduced to **172,765 records and 20 relevant columns**.

## Tools & Technologies

| Tool                 | Purpose                                   |
| -------------------- | ----------------------------------------- |
| **Python**           | Data analysis and modeling                |
| **Pandas**           | Data cleaning and manipulation            |
| **NumPy**            | Numerical operations and feature creation |
| **Matplotlib**       | Data visualization                        |
| **Seaborn**          | Statistical visualization                 |
| **Scikit-learn**     | Machine learning                          |
| **Imbalanced-learn** | SMOTE for class balancing                 |
| **Jupyter Notebook** | Development environment                   |

---

## Project Workflow

``text
Raw Dataset
     ↓
Data Understanding
     ↓
Data Cleaning & Preprocessing
     ↓
Feature Engineering
     ↓
Exploratory Data Analysis
     ↓
Delay & Bottleneck Analysis
     ↓
Profitability Analysis
     ↓
Late Delivery Risk Modeling
     ↓
Business Insights
```

---

## Data Cleaning & Preprocessing

The project performed several data-cleaning steps to prepare the dataset for analysis.

### Key steps:

* Checked dataset shape and column information.
* Checked duplicate records.
* Identified missing values.
* Removed unnecessary and redundant columns.
* Removed sensitive customer information.
* Removed columns containing only one value.
* Removed duplicate information such as `Benefit per order`, which was identical to `Order Profit Per Order`.
* Removed canceled orders from delivery-time analysis.
* Converted order and shipping date columns into proper datetime format.
* Removed unnecessary geographical and identifier columns.

## The cleaned dataset contains **172,765 records and 20 columns**.

## Feature Engineering

Several new features were created to measure operational performance.

### Important Features

**Order Processing Time**

```text
Shipping Date - Order Date
```

Measures how many days were required to process an order.

**Delay**

```text
Order Processing Time - Scheduled Shipment Days
```

Measures how many days an order was ahead of or behind its scheduled shipment time.

**Is_Delayed**

```text
Delay > 0
```

Classifies whether an order was delayed.

Additional time-based features:

* `order_month`
* `order_day`
* `order_hour`

These features were used to understand delivery patterns over different time periods.

---

## Exploratory Data Analysis

The project analyzes delivery performance across multiple business dimensions.

### Delivery Analysis

Delivery delays were analyzed by:

* Shipping Mode
* Customer Segment
* Department Name
* Order Region
* Order Status
* Order Type
* Month
* Day of Week
* Hour of Day

The analysis identified **94,523 delayed orders** based on the engineered `Is_Delayed` metric.

### Time-Based Analysis

The project also examines whether delivery delays vary depending on:

* Order month
* Day of the week
* Order hour

For example, the highest observed hourly delay percentage in the analysis was approximately **57.13% at hour 20**.

---

## Profitability Analysis

To understand the financial impact of orders, a `Profitability Flag` was created using `Order Profit Per Order`.

Orders were classified into:

* **Profit**
* **Loss**
* **Break-even**

Results:

| Category   |  Orders |
| ---------- | ------: |
| Profit     | 139,354 |
| Loss       |  32,295 |
| Break-even |   1,116 |

This allows delivery performance to be studied alongside order profitability.

---

## Bottleneck Analysis

The project identifies operational areas associated with higher delivery delays.

The analysis focuses on:

* **Shipping Mode**
* **Customer Segment**
* **Department Name**
* **Order Region**
* **Order Status**
* **Order Type**

This helps identify potential operational bottlenecks and areas where delivery processes can be improved.

---

## Machine Learning — Late Delivery Risk

A classification model was developed to predict:

```text
Late_delivery_risk
```

### Features Used

The model uses operational and categorical features such as:

* Type
* Days for shipment (scheduled)
* Category Name
* Customer Segment
* Department Name
* Order Region
* Shipping Mode
* Order Month
* Order Hour

Categorical variables were transformed using **frequency encoding** before modeling.

### Model

**Random Forest Classifier**

The dataset was divided using an **80/20 train-test split** with stratification.

### Model Performance

| Metric    |   Score |
| --------- | ------: |
| Accuracy  | **74%** |
| Precision | **79%** |
| Recall    | **75%** |

The model provides a baseline approach for identifying orders with a higher risk of late delivery.

---

## Key Findings

* The original dataset contained **180K+ supply-chain records**.
* After cleaning, **172,765 records** were retained for analysis.
* **94,523 orders** were identified as delayed using the engineered delay metric.
* Delivery performance varies across shipping, customer, regional, departmental, and order-status dimensions.
* Profitability analysis identified **139,354 profitable**, **32,295 loss-making**, and **1,116 break-even** orders.
* Time-based analysis revealed differences in delay percentages across hours, days, and months.
* The Random Forest model achieved **74% accuracy**, with **79% precision** and **75% recall** for the evaluated classification task.

---

## Business Value

The analysis can help supply-chain teams:

* Monitor delivery performance.
* Identify operational bottlenecks.
* Understand factors associated with late deliveries.
* Investigate profitability and loss patterns.
* Improve shipping and operational planning.
* Prioritize orders with higher late-delivery risk.

---

## Project Structure

```text
Supply-Chain-Analysis/
│
├── Supply_Chain_Analysis.ipynb
├── DataCoSupplyChainDataset.csv
├── README.md
└── images/
    └── visualizations/
```

---

## How to Run

### 1. Clone the repository

```bash
git clone <your-repository-link>
```

### 2. Open the project

Open the project folder in **Jupyter Notebook** or **VS Code**.

### 3. Install required libraries

```bash
pip install pandas numpy matplotlib seaborn scikit-learn imbalanced-learn
```

### 4. Add the dataset

Place:

```text
DataCoSupplyChainDataset.csv
```

in the project directory.

### 5. Run the notebook

Open:

```text
Supply_Chain_Analysis.ipynb
```

and run the cells sequentially.

---

## Skills Demonstrated

* Data Cleaning & Preprocessing
* Exploratory Data Analysis
* Feature Engineering
* Business Analysis
* Supply Chain Analytics
* Delivery Delay Analysis
* Profitability Analysis
* Bottleneck Analysis
* Data Visualization
* Categorical Feature Encoding
* Machine Learning Classification
* Model Evaluation

---

## Author

**Akhil Raj**
