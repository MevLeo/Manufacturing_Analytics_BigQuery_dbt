# 🏭 Manufacturing Analytics Data Pipeline

## 📌 Overview 

This project demonstrates an end-to-end data pipeline built using **ELT architecture** on a manufacturing dataset.

The pipeline transforms raw production data into analytics-ready datasets, enabling business insights such as production efficiency, defect rates, and overall equipment effectiveness (OEE).

---

## 🧱 Architecture

This project follows the **Medallion Architecture**:

```
Bronze → Silver → Gold
```

### 🔸 Bronze Layer (Raw Data)

* Source data loaded into BigQuery
* No transformations applied
* Tables:

  * production_events
  * machines
  * operators
  * products
  * quality_inspections

---

### 🔹 Silver Layer (Cleaned Data)

* Data cleaning and validation

* Handling:

  * Null values
  * Duplicates (ROW_NUMBER)
  * Data standardization

* Tables:

  * silver_production_clean
  * silver_machines_clean
  * silver_operators_clean
  * silver_products_clean
  * silver_quality_inspections_clean

---

### 🔶 Gold Layer (Business Logic & KPIs)

Analytics-ready models including key manufacturing metrics:

#### 📊 Fact Table

* `gold_production_metrics`

  * defect_rate
  * quality_rate
  * OEE (Overall Equipment Effectiveness)
  * total_defects

#### 📈 Aggregated Table

* `gold_machine_daily`

  * daily production
  * average OEE
  * defect trends

---

## ⚙️ Tech Stack

* **Data Warehouse:** Google BigQuery
* **Transformation Tool:** dbt (Data Build Tool)
* **Language:** SQL
* **Architecture:** ELT + Medallion

---

## 🚀 Key Features

* ✅ End-to-End ELT Pipeline
* ✅ Data Quality Testing (dbt tests)
* ✅ Incremental Models for scalability
* ✅ Partitioning & Clustering (BigQuery optimization)
* ✅ KPI Calculation (OEE, defect rate, performance)
* ✅ Modular & Maintainable dbt project structure

---

## ⚡ Advanced Engineering

### 🔁 Incremental Processing

* Only new data is processed
* Improves performance and reduces cost

### 📦 Partitioning

* Partitioned by `production_timestamp`

### 🧩 Clustering

* Clustered by:

  * machine_id
  * operator_id

---

## 📊 Example KPIs

* **Defect Rate**
* **Quality Rate**
* **OEE (Overall Equipment Effectiveness)**
* **Production Throughput**
* **Machine Performance**

---

## 🧪 Data Quality

Implemented using dbt tests:

* `not_null`
* `unique`
* Range validation (for KPIs)

---

## ▶️ How to Run

```bash
# Run all models
dbt run

# Run only gold layer with dependencies
dbt run --select gold+

# Run tests
dbt test

# Full refresh (rebuild everything)
dbt run --full-refresh
```

---

## 📂 Project Structure

```
models/
│
├── bronze/
├── silver/
│   ├── silver_production_clean.sql
│   ├── silver_machines_clean.sql
│   ├── silver_operators_clean.sql
│   ├── silver_products_clean.sql
│   └── silver_quality_inspections_clean.sql
│
└── gold/
    ├── gold_production_metrics.sql
    └── gold_machine_daily.sql
```

---

## 🎯 Business Value

This pipeline enables:

* Monitoring production efficiency
* Identifying defective processes
* Comparing machine/operator performance
* Supporting data-driven decision making

---

## 💡 Future Improvements

* Implement Slowly Changing Dimensions (SCD Type 2)
* Add orchestration (e.g., Airflow)
* Build dashboards (Power BI / Looker)
* Add anomaly detection

---

## 👤 Author

Mohsen
Data Analyst / BI Developer

---

## ⭐ Final Note

This project demonstrates practical skills in:

* Data Modeling
* ELT Pipelines
* Cloud Data Warehousing
* Business Analytics

---

> “Turning raw data into actionable insights.”

