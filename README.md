# Data Warehouse and Analytics Project

Welcome to the **Data Warehouse and Analytics Project** repository! 🚀  
This project demonstrates a comprehensive data warehousing and analytics solution, from building a data warehouse to generating actionable insights. Designed as a portfolio project, it highlights industry best practices in data engineering and analytics.

---
## 🏗️ Data Architecture

The data architecture for this project follows Medallion Architecture **Bronze**, **Silver**, and **Gold** layers:

## [Data Architecture]
![Screenshot 2025-05-18 113359](https://github.com/user-attachments/assets/fb081bdb-c666-4eab-a2f4-3e7f3b0fd7cd)




1. **Bronze Layer**: Stores raw data as-is from the source systems. Data is ingested from CSV Files into SQL Server Database.
2. **Silver Layer**: This layer includes data cleansing, standardization, and normalization processes to prepare data for analysis.
3. **Gold Layer**: Houses business-ready data modeled into a star schema required for reporting and analytics.

---

## 📖 Project Overview

This project involves:

1. **Data Architecture**: Designing a Modern Data Warehouse Using Medallion Architecture **Bronze**, **Silver**, and **Gold** layers.
2. **ETL Pipelines**: Extracting, transforming, and loading data from source systems into the warehouse.
3. **Data Modeling**: Developing fact and dimension tables optimized for analytical queries.
4. **Analytics & Reporting**: Creating SQL-based reports and dashboards for actionable insights.

🎯 This repository is an excellent resource for professionals and students looking to showcase expertise in:
- SQL Development
- Data Architect
- Data Engineering  
- ETL Pipeline Developer  
- Data Modeling  
- Data Analytics  

---

## 🛠️ Important Links & Tools:

Everything is for Free!
- **[Datasets](datasets/):** Access to the project dataset (csv files).
- **[SQL Server Express](https://www.microsoft.com/en-us/sql-server/sql-server-downloads):** Lightweight server for hosting your SQL database.
- **[SQL Server Management Studio (SSMS)](https://learn.microsoft.com/en-us/sql/ssms/download-sql-server-management-studio-ssms?view=sql-server-ver16):** GUI for managing and interacting with databases.
- **[Git Repository](https://github.com/):** Set up a GitHub account and repository to manage, version, and collaborate on your code efficiently.
- **[DrawIO](https://www.drawio.com/):** Design data architecture, models, flows, and diagrams.
- **[Notion](https://www.notion.com/):** All-in-one tool for project management and organization.
- **[Notion Project Steps](https://thankful-pangolin-2ca.notion.site/SQL-Data-Warehouse-Project-16ed041640ef80489667cfe2f380b269?pvs=4):** Access to All Project Phases and Tasks.

---

## 🚀 Project Requirements

### Building the Data Warehouse (Data Engineering)

#### Objective
Develop a modern data warehouse using SQL Server to consolidate sales data, enabling analytical reporting and informed decision-making.

#### Specifications
- **Data Sources**: Import data from two source systems (ERP and CRM) provided as CSV files.
- **Data Quality**: Cleanse and resolve data quality issues prior to analysis.
- **Integration**: Combine both sources into a single, user-friendly data model designed for analytical queries.
- **Scope**: Focus on the latest dataset only; historization of data is not required.
- **Documentation**: Provide clear documentation of the data model to support both business stakeholders and analytics teams.

---

### BI: Analytics & Reporting (Data Analysis)

#### Objective
Develop SQL-based analytics to deliver detailed insights into:
- **Customer Behavior**
- **Product Performance**
- **Sales Trends**

These insights empower stakeholders with key business metrics, enabling strategic decision-making.  

For more details, refer to [docs/requirements.md](docs/requirements.md).

## 📂 Repository Structure
```
data-warehouse-project/
│
├── datasets/                           # Raw datasets used for the project (ERP and CRM data)
│
├── docs/                               # Project documentation and architecture details
│   ├── etl.drawio                      # Draw.io file shows all different techniquies and methods of ETL
│   ├── data_architecture.drawio        # Draw.io file shows the project's architecture
│   ├── data_catalog.md                 # Catalog of datasets, including field descriptions and metadata
│   ├── data_flow.drawio                # Draw.io file for the data flow diagram
│   ├── data_models.drawio              # Draw.io file for data models (star schema)
│   ├── naming-conventions.md           # Consistent naming guidelines for tables, columns, and files
│
├── scripts/                            # SQL scripts for ETL and transformations
│   ├── bronze/                         # Scripts for extracting and loading raw data
│   ├── silver/                         # Scripts for cleaning and transforming data
│   ├── gold/                           # Scripts for creating analytical models
│
├── tests/                              # Test scripts and quality files
│
├── README.md                           # Project overview and instructions
├── LICENSE                             # License information for the repository
├── .gitignore                          # Files and directories to be ignored by Git
└── requirements.txt                    # Dependencies and requirements for the project
```
---

# 📊 Data Catalog – Gold Layer

The **Gold Layer** represents the business-level, analytics-ready data in our architecture. It consists of **dimension tables** and **fact tables**, structured to support dashboards, KPIs, and advanced analytical use cases.

---

## 🧑‍🤝‍🧑 `gold.dim_customers`

**Purpose:**  
Stores customer details enriched with demographic and geographic data.

| Column Name      | Data Type     | Description                                                                 |
|------------------|---------------|-----------------------------------------------------------------------------|
| `customer_key`   | INT           | Surrogate key uniquely identifying each customer.                           |
| `customer_id`    | INT           | Unique identifier assigned to each customer.                                |
| `customer_number`| NVARCHAR(50)  | Alphanumeric identifier for external tracking.                              |
| `first_name`     | NVARCHAR(50)  | Customer's first name.                                                      |
| `last_name`      | NVARCHAR(50)  | Customer's last name.                                                       |
| `country`        | NVARCHAR(50)  | Country of residence (e.g., 'Australia').                                   |
| `marital_status` | NVARCHAR(50)  | Marital status (e.g., 'Married', 'Single').                                 |
| `gender`         | NVARCHAR(50)  | Gender (e.g., 'Male', 'Female', 'n/a').                                     |
| `birthdate`      | DATE          | Date of birth (format: YYYY-MM-DD).                                         |
| `create_date`    | DATE          | Timestamp of customer record creation.                                      |

---

## 📦 `gold.dim_products`

**Purpose:**  
Contains product information and attributes for categorization and analysis.

| Column Name           | Data Type     | Description                                                                 |
|------------------------|----------------|-----------------------------------------------------------------------------|
| `product_key`          | INT            | Surrogate key for each product record.                                      |
| `product_id`           | INT            | Unique internal product identifier.                                         |
| `product_number`       | NVARCHAR(50)   | Alphanumeric product code.                                                  |
| `product_name`         | NVARCHAR(50)   | Product name with key attributes (type, color, size).                       |
| `category_id`          | NVARCHAR(50)   | Identifier for product category.                                            |
| `category`             | NVARCHAR(50)   | Broad classification (e.g., 'Bikes', 'Components').                        |
| `subcategory`          | NVARCHAR(50)   | Detailed classification within the category.                                |
| `maintenance_required` | NVARCHAR(50)   | Indicates if maintenance is required ('Yes', 'No').                         |
| `cost`                 | INT            | Base product cost in whole currency units.                                  |
| `product_line`         | NVARCHAR(50)   | Product series (e.g., 'Road', 'Mountain').                                  |
| `start_date`           | DATE           | Launch date of the product.                                                 |

---

## 💰 `gold.fact_sales`

**Purpose:**  
Stores transactional sales data linked to products and customers.

| Column Name     | Data Type     | Description                                                                 |
|------------------|----------------|-----------------------------------------------------------------------------|
| `order_number`   | NVARCHAR(50)   | Unique order identifier (e.g., 'SO54496').                                  |
| `product_key`    | INT            | Foreign key linking to `dim_products`.                                      |
| `customer_key`   | INT            | Foreign key linking to `dim_customers`.                                     |
| `order_date`     | DATE           | Date the order was placed.                                                  |
| `shipping_date`  | DATE           | Date the order was shipped.                                                 |
| `due_date`       | DATE           | Date payment was due.                                                       |
| `sales_amount`   | INT            | Total value of the sale (in whole units).                                   |
| `quantity`       | INT            | Number of product units ordered.                                            |
| `price`          | INT            | Price per product unit.                                                     |

---

✅ **Note:** All foreign keys (`product_key`, `customer_key`) refer to corresponding dimension tables to support a star schema structure.



## 🌟 About Me

- **Name-Vaibhav Anand**
- **email_id-anandvaibhav02@gmail.com**

Let's stay in touch! Feel free to connect with me on the following platforms:

