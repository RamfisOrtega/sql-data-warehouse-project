# 🚚 Logistics Data Warehouse

A modern data warehouse built with **SQL Server** to consolidate logistics data from two source systems — an ERP and a CRM — enabling analytical reporting on shipment performance, carrier efficiency, and customer fulfilment.

---

## 📋 Project Overview

| | |
|---|---|
| **Architecture** | Medallion (Bronze → Silver → Gold) |
| **Database** | SQL Server Express |
| **Tool** | SQL Server Management Studio (SSMS) |
| **Source data** | CSV flat files (ERP + CRM) |
| **Deployment** | Local / Docker (optional) |
| **Version control** | Git / GitHub |

---

## 🎯 Objectives

### Phase 1 — Data Engineering
Consolidate raw data from two source systems into a clean, analytics-ready data warehouse.

### Phase 2 — BI Analytics & Reporting
Develop SQL-based analytics to deliver logistics insights that support strategic decision-making.

---

## 🗂️ Data Sources

| System | Role | Contains |
|---|---|---|
| **ERP** | Operations & Inventory | Products, shipments, carriers, routes, delivery status |
| **CRM** | Customer & Sales | Customers, orders, sales reps, regions |

---

## 🏗️ Architecture

Data flows through three layers. Each layer has a single responsibility.
```
┌─────────────┐     ┌─────────────┐     ┌─────────────┐
│   BRONZE    │────▶│   SILVER    │────▶│    GOLD     │
│  Raw Layer  │     │Clean Layer  │     │Analytical   │
│             │     │             │     │   Model     │
│ CSV loaded  │     │ Cleansed &  │     │ Integrated  │
│  as-is, no  │     │standardised │     │ fact+dim    │
│ transforms  │     │             │     │  tables     │
└─────────────┘     └─────────────┘     └─────────────┘
      ▲
 Source CSVs
 (ERP + CRM)
```

| Layer | Schema | Purpose |
|---|---|---|
| 🟤 Bronze | `bronze.*` | Raw ingestion — data loaded exactly as received |
| ⚪ Silver | `silver.*` | Cleansed — NULLs resolved, duplicates removed, formats standardised |
| 🟡 Gold | `gold.*` | Analytical model — unified fact and dimension tables for reporting |

---

## 📊 Analytical Domains

| Domain | Key Metrics |
|---|---|
| **Shipment Performance** | On-time delivery rate, average transit time, delays by route and carrier |
| **Carrier Efficiency** | Performance ranking, cost vs speed, failure rates |
| **Customer Fulfilment** | Orders fulfilled on time by customer segment and region |
| **Product & Order Trends** | Most shipped products, order volumes over time |
| **Regional Analysis** | Delivery performance and costs by geography |

---

## 📁 Repository Structure
```
logistics-data-warehouse/
│
├── datasets/                  # Source CSV files
│   ├── erp/
│   └── crm/
│
├── scripts/
│   ├── bronze/                # Raw ingestion scripts
│   ├── silver/                # Cleansing & standardisation scripts
│   └── gold/                  # Analytical model scripts
│
├── docs/
│   ├── data_model.md          # ERD and table descriptions
│   └── data_dictionary.md     # Field definitions (business + technical)
│
└── README.md
```

---

## 🚀 Getting Started

### Prerequisites
- SQL Server Express
- SQL Server Management Studio (SSMS)
- Docker *(optional — for isolated environment)*

### Setup

**1. Clone the repository**
```bash
git clone https://github.com/your-username/logistics-data-warehouse.git
cd logistics-data-warehouse
```

**2. Run Bronze layer — ingest raw CSVs**
```sql
-- Execute in SSMS
scripts/bronze/load_bronze.sql
```

**3. Run Silver layer — cleanse and standardise**
```sql
scripts/silver/load_silver.sql
```

**4. Run Gold layer — build analytical model**
```sql
scripts/gold/load_gold.sql
```

> ⚠️ Run scripts in order. Each layer depends on the one before it.

---

## 🚫 Out of Scope

- Real-time or streaming ingestion
- Historical data tracking (SCD / Type 2 dimensions)
- BI visualisation tools (Power BI, Tableau)
- Cloud deployment
- Automated ETL pipelines

---

## 📄 Documentation

| Document | Description |
|---|---|
| `docs/data_model.md` | ERD and layer-by-layer table descriptions |
| `docs/data_dictionary.md` | Field-level definitions for business and technical audiences |

---

## 🛠️ Tech Stack

![SQL Server](https://img.shields.io/badge/SQL%20Server-CC2927?style=flat&logo=microsoft-sql-server&logoColor=white)
![Docker](https://img.shields.io/badge/Docker-2496ED?style=flat&logo=docker&logoColor=white)
![Git](https://img.shields.io/badge/Git-F05032?style=flat&logo=git&logoColor=white)
![GitHub](https://img.shields.io/badge/GitHub-181717?style=flat&logo=github&logoColor=white)
