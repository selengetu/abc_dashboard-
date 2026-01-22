# ABC Data Platform 

Production data platform powering Various dashboards, reporting, and integrations**.  
Built on **Laravel, Supabase, Prefect, and external APIs** to provide reliable, auditable business data.

---

## Table of Contents

- [Overview](#overview)
- [Architecture](#architecture)
- [Tech Stack](#tech-stack)
- [Repository Structure](#repository-structure)
- [Core Features](#core-features)
- [ETL Pipelines](#etl-pipelines)
- [Dashboards](#dashboards)
- [Integrations](#integrations)

---

## Overview

The **ABC Data Platform** centralizes operational, financial, and project data from multiple systems into a single source of truth used for:

- Executive dashboards
- Pipeline & profitability tracking
- Contract and invoice reporting
- KPI monitoring

The system is designed for **data accuracy, auditability, and scalability**.
<img width="1473" height="741" alt="Screenshot 2025-12-19 at 9 48 52 PM" src="https://github.com/user-attachments/assets/e3e65d89-05a4-445b-9590-a888aa5a72fd" />


---

## Architecture
-External Systems
-(Google Sheets, Fieldwire, QBO)
↓
ETL / Sync Layer (Prefect + Python)
↓
Snowflake
↓
dbt (Transformation)
↓
Supabase (PostgreSQL)
↓
Laravel Application
↓
Dashboards & Admin UI

# Tech Stack

### Backend & Data
- Laravel (PHP)
- Supabase (PostgreSQL)
- Prefect (ETL orchestration)
- Python (ETL & integrations)

### Frontend
- Blade Templates
- DataTables
- Chart.js / ApexCharts
- Select2 / Flatpickr

### Integrations
- Google Sheets API
- Fieldwire API
- Supabase REST API

- ## Core Features

- Contract master data management
- Pipeline tracking
- Profitability analysis
- KPI dashboard customization (per user)
- Rate management
- User & access management
- Webhook-based task updates

---
<img width="913" height="707" alt="Screenshot 2025-12-19 at 9 49 12 PM" src="https://github.com/user-attachments/assets/4e8acffa-8c49-4411-8dfa-b9c27e422876" />

## ETL Pipelines

### Contracts Sync

- **Flow name:** `contracts-sync`
- **Source:** Google Sheets (PLPA Master → Contracts tab)
- **Target:** Supabase table `Contract`

**Behavior**
- Full refresh
- Preserves manual records (`is_custom = 1`)
- Batch inserts via Supabase REST API
- Optional CSV snapshot for auditing

**Transformations**
- Header normalization
- Data validation & cleaning
- Numeric coercion
- UTC upload timestamps

ETL scripts are located under `/etl`.

---

## Dashboards

### Available Dashboards
- Pipeline
- Profitability
- Rates
- Users
- KPI Library

### KPI Customization
- User-specific KPI selection
- Layouts stored in `kpi_layouts`
- Persisted per dashboard tab

---

## Integrations

### Google Sheets
- OAuth authentication
- Primary source for contract master data

### Fieldwire
- Webhook-based task updates
- Task → contract linkage
- Status & completion tracking

---

## Local Development

### Prerequisites
- PHP 8.x
- Composer
- Node.js
- Python 3.10+
- Supabase project access
