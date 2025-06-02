🏢 Netflix-ETL-Pipeline-Using-Databricks

This project is designed to ingest, transform, and analyze Netflix data using **Azure Data Factory (ADF)**, **Azure Data Lake Storage Gen2 (ADLS)**, **Azure Databricks**, **Azure Synapse Analytics**, and **Power BI**. The pipeline follows a **Medallion Architecture (Bronze, Silver, Gold)** to ensure data reliability, consistency, and high-quality reporting.

---

📁 Project Architecture

**Medallion Architecture Layers:**

- **Bronze Layer**: Raw data is ingested from GitHub using Azure Data Factory with dynamic parameterization and validation, then stored in ADLS with minimal to no transformation.
- **Silver Layer**: Cleaned and transformed data using Azure Databricks notebooks. Applied filtering, parsing, and logic-based enhancements.
- **Gold Layer**: Final aggregated and enriched data published to Azure Synapse Analytics and exported to Power BI for business analysis and reporting.

---

⚙️ Tech Stack

- **Azure Data Factory (ADF)**: For GitHub-based data ingestion and orchestration workflows using dynamic and parameterized pipelines.
- **Azure Data Lake Storage Gen2 (ADLS)**: For structured storage following the Medallion architecture.
- **Azure Databricks**: For scalable data processing using **PySpark**, **Autoloader**, and **Delta Lake**.
- **Azure Synapse Analytics**: For enterprise data modeling and enabling Power BI connectivity.
- **Power BI**: For dashboarding and reporting using curated Gold-layer data.
- **Delta Lake**: Implemented versioning, Time Travel, and Delta logs for efficient data lineage and history tracking.

---

🔄 Data Flow

**Data Ingestion (ADF + GitHub)**

- GitHub source connected via ADF linked services.
- Parameterized ADF pipelines ingest the data and store it in the Bronze container.
- Validation steps integrated using `If-Else`, `ForEach`, and other control activities.

**Bronze to Silver (Databricks)**

- Raw files from the Bronze layer read using **Databricks Autoloader** for incremental loading.
- Data transformations such as filtering, joins, and column standardization performed using parameterized notebooks.
- Output written to the Silver container in **Delta format**.

**Silver to Gold (Databricks → Synapse)**

- Further transformation and business logic applied on Silver data.
- Final curated tables written to Gold container.
- External Delta tables and views created in **Azure Synapse Analytics** for enterprise querying.

**Reporting (Power BI)**

- Power BI connected to Synapse and Gold Delta tables.
- Interactive dashboards created to visualize insights like:
  - Title distribution by country and type (movie/show)
  - Genre popularity
  - Year-wise content growth on Netflix

---

🧱 Components

**Azure Data Factory (ADF)**  
- Pipelines dynamically parameterized for ingestion.
- Activities: `Copy`, `Get Metadata`, `If`, `ForEach`, `Execute Pipeline`.
- Used for orchestration and validation.

**Azure Data Lake Storage (ADLS)**  
- Containers: `bronze/`, `silver/`, `gold/` implementing Medallion architecture.
- Stores raw, cleansed, and curated data.

**Azure Databricks**  
- **Autoloader** for incremental file ingestion.
- Notebooks created with dynamic parameterization.
- Transformations using PySpark and Delta Lake APIs.
- Utilized Delta Time Travel and Delta logs for data versioning.

**Azure Synapse Analytics**  
- External Delta tables created from Gold data.
- Enables Power BI connectivity and advanced analytics.

**Power BI**  
- Visualizations and dashboards built using Gold and Synapse datasets.
- Used for deriving actionable insights and business reporting.

---

📌 Summary

This project demonstrates a **real-time, modular, and scalable data engineering solution** using Azure tools. It showcases dynamic pipeline development, Delta Lake implementation with version control, efficient data orchestration, and enterprise-grade reporting via Synapse and Power BI. It reflects a **production-ready cloud data platform** aligned with industry best practices.
