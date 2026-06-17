# telecom-kpi-etl-pipeline
Automated ETL pipeline built with Python, Pandas, and SQLAlchemy to extract, clean, and bulk-load telecommunication reference data (GSM, LTE, NR, MOCN) into MSSQL Server.

# Telecom KPI & Reference Data ETL Pipeline

[![Python Version](https://img.shields.io/badge/python-3.8%2B-blue.svg)](https://www.python.org/)
[![Database](https://img.shields.io/badge/Database-MSSQL%20Server-red.svg)](https://www.microsoft.com/en-us/sql-server)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

An automated, robust ETL (Extract, Transform, Load) pipeline built with **Python**, **Pandas**, and **SQLAlchemy** to process and synchronize multi-technology telecommunication network reference data (GSM, LTE, NR, MOCN Tracker, and Sector mappings) into a centralized **Microsoft SQL Server (MSSQL)** database.

## 🚀 Key Features

- **Automated Data Extraction:** Scans and extracts raw data dynamically from multiple file formats (`.csv`, `.xlsx`, `.xlsb`) within a target directory using optimized regex pattern matching.
- **Dynamic Schema Validation:** Queries target MSSQL table metadata in real-time to detect column mismatches, ensuring data integrity before loading.
- **Smart Data Preprocessing & Self-Healing:**
  - Standardizes column names automatically (lowercasing, removing dates, replacing spaces/dashes with underscores).
  - Handles string truncation safely based on `CHARACTER_MAXIMUM_LENGTH` from the database to prevent overflow errors.
  - Automatically coerces corrupted/missing date formats into valid `YYYY-MM-DD` standard or `NULL`.
- **High-Performance Bulk Insert:** Implements `pyodbc`'s `fast_executemany` safely via SQLAlchemy event listeners to achieve high-speed data loading.
- **Secure Configuration:** Zero hardcoded credentials. Managed completely via environment variables (`.env`).

---

## 🛠️ Tech Stack & Architecture

- **Language:** Python
- **Core Libraries:** Pandas, NumPy, SQLAlchemy, PyODBC, Python-Dotenv
- **Database Server:** Microsoft SQL Server (MSSQL)
- **File Engines:** Openpyxl (Excel), Pyxlsb (Binary Excel)

---

## 📋 Prerequisites & Installation

### 1. Clone the Repository
```bash
git clone [https://github.com/yourusername/telecom-kpi-etl-pipeline.git](https://github.com/yourusername/telecom-kpi-etl-pipeline.git)
cd telecom-kpi-etl-pipeline
