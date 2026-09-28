# Chronic Disease Analytics System: OLTP to OLAP

**Author:** Nicolette Mtisi  
*Originally completed as a team project ("Trio Analytics"). This repository is my copy of the work.*  
**Tools:** PostgreSQL · SQL · Dimensional Modeling · ETL · Tableau

## Overview
This database solution tracks, analyzes and responds to **chronic disease trends** in urban populations. It covers the full data lifecycle, from **transactional data capture (OLTP)** to **analytical insight (OLAP)**, so that healthcare providers, researchers and policymakers can make data-driven decisions.

## Business Problem
Chronic diseases such as diabetes, hypertension, asthma and heart disease are rising, especially in cities, driven by lifestyle, the environment and gaps in access to care. Health organizations need a reliable system to monitor diagnosis rates, treatment plans, hospital visits, medication use and patient outcomes. With it, they can target interventions and allocate resources where they're needed most.

## Architecture
```
 OLTP (normalized, schema: public)          ETL (SQL)            OLAP (star schema, schema: warehouse)
 ─────────────────────────────────   ─────────────────────►   ──────────────────────────────────────
 person · disease · disease_type                                         dim_person
 location · medicine · indication                                        dim_disease
 race · diseased_patient                    clean, join,          dim_date ── fact_disease_diagnosis ── dim_medicine
 race_disease_propensity                    reshape, load                    dim_location
                                                                         dim_race
```

**1. OLTP database:** 9 normalized tables built for data integrity and efficient day-to-day transactions.

**2. OLAP data warehouse:** a **star schema** with a central `fact_disease_diagnosis` table at the grain of *one patient diagnosis event*. Its six dimensions are `dim_date`, `dim_disease`, `dim_person`, `dim_location`, `dim_medicine` and `dim_race`.

**3. ETL:** SQL scripts extract data from the OLTP schema, then clean, join and reshape it and load it into the warehouse.

**4. Analytics:** SQL queries run directly on the dimensional model, and the data is ready for BI tools like Tableau. See the presentation for the dashboards.

## Example Analytical Questions
- Which diseases are most common within each race group?
- How effective are medicines by disease type?
- Which cities have the highest average disease severity?
- What is the propensity for each disease by race?

The project also shows **integrity constraints** at work, for example updating a patient record after treatment completes. The presentation discusses how the design would scale on **AWS** (a batch plus real-time Lambda architecture) and **Snowflake**, and compares relational and NoSQL storage.

## How to Run
1. Install **PostgreSQL** and connect with pgAdmin, DBeaver or `psql`.
2. Run `chronic_disease_analytics.sql` from start to finish. It will:
   - create and populate the OLTP tables
   - create the `warehouse` schema and dimensional tables
   - run the ETL into the star schema
   - run the analytical queries

## Business Value
- **Targeted interventions:** find high-risk populations and geographic hotspots.
- **Resource optimization:** allocate care based on how common and how severe diseases are.
- **Treatment effectiveness:** support evidence-based decisions about therapies and medications.
- **Policy support:** give policymakers data for public health initiatives.

## Data Disclaimer
All data in this project is **synthetic**, generated only to demonstrate the system's analytical capabilities. It is not real clinical data.

## Files
| File | Description |
|------|-------------|
| `chronic_disease_analytics.sql` | OLTP schema, sample data, warehouse schema, ETL and analytical queries |
| `chronic_disease_analytics_presentation.pptx` | Slides: ER diagram, dimensional model, dashboards and cloud architecture |

## Links
- 📝 [Medium write-up](https://medium.com/@nicmtisi/chronic-care-analytics-revolutionizing-urban-health-with-data-d34cb11726d7)
- 🌐 [Portfolio](https://nic-stack.github.io/NicoletteMtisi/) · [LinkedIn](https://www.linkedin.com/in/nicolette-mtisi)
