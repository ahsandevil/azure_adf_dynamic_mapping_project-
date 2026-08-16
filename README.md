# Azure Data Engineering Learning Project

## Overview

This project documents my hands-on learning journey in Azure Data Engineering, covering SQL Server, Azure Data Factory, incremental data ingestion, data flows, business dimensions, CI/CD concepts, GitHub version control, and production-ready pipeline design.

The goal of this project is to understand how data engineering solutions are designed and implemented from source ingestion through transformation, loading, monitoring, and version control.

---

## Technologies & Services

- Azure SQL Database
- Azure Data Factory
- Self-Hosted Integration Runtime (SHIR)
- Azure Logic Apps
- GitHub
- Git branching & version control
- Azure Data Flows
- Delta Lake concepts
- Azure DevOps concepts

---

## 1. SQL Server Fundamentals

Covered the fundamentals of working with Azure SQL, including:

- Azure SQL Server and Database setup
- Server authentication
- SQL Server fundamentals
- Tables and relationships
- Primary Keys
- Foreign Keys
- Unique constraints
- Basic SQL operations

---

## 2. Azure Data Factory

Built data ingestion pipelines using Azure Data Factory.

### Integration Runtime

Learned the role of Integration Runtime in data movement and processing.

For cloud-to-cloud data movement, Azure-managed Integration Runtime can be used.

For moving data from an on-premises/local environment to Azure, a Self-Hosted Integration Runtime can be installed and configured on the local machine.

### Self-Hosted Integration Runtime

Configured SHIR to enable ADF to access local/on-premises files.

Architecture:

Local Machine
→ Self-Hosted Integration Runtime
→ Azure Data Factory
→ Azure Data Services

---

## 3. Linked Services

Created linked services to connect ADF with data sources and destinations.

For on-premises/local files, the Self-Hosted Integration Runtime is used instead of Azure AutoResolve Integration Runtime.

---

## 4. Dynamic Mapping

Explored dynamic mapping in ADF.

When separate Copy Data activities are used for different files, imported/static mapping can be sufficient.

Dynamic mapping becomes useful when a single reusable Copy Data activity needs to process multiple files with different structures.

---

## 5. Incremental Data Ingestion

Implemented the concept of incremental ingestion using watermark-based processing.

Instead of processing the complete dataset every time, the pipeline identifies the previously processed point and loads only the new data.

General pattern:

1. Read previous watermark
2. Identify new records
3. Copy/process new data
4. Determine latest watermark
5. Update watermark

This helps reduce unnecessary processing and improves pipeline efficiency.

---

## 6. Parent-Child Pipeline Architecture

Explored production-oriented pipeline design using parent and child pipelines.

The parent pipeline controls and executes reusable child pipelines.

Pipeline parameters can be passed dynamically from the parent pipeline to the child pipeline.

This approach helps create reusable and maintainable ingestion workflows.

---

## 7. Error Handling & Alerts

Implemented pipeline failure handling using Azure Logic Apps.

Architecture:

ADF Pipeline
→ Pipeline Failure
→ Web Activity
→ Logic App
→ Notification / Email

The goal is to automatically notify when a pipeline execution fails.

---

## 8. Upsert

Learned the concept of Upsert:

**Upsert = Update + Insert**

If a record already exists:

`UPDATE`

If a record does not exist:

`INSERT`

Upsert is useful when processing datasets containing both new records and changes to existing records.

---

## 9. Azure Data Flow

Worked with Mapping Data Flows for transformation and data processing.

Topics explored:

- Derived Columns
- Conditional Split
- Data transformation
- Dynamic expressions
- Alter Row
- Upsert patterns

### Alter Row

Used Alter Row policies to define how records should be handled when writing data to a sink.

---

## 10. Business Dimensions

Created a Business Dimension layer to store business-oriented views.

The purpose is to separate technical ingestion logic from business-facing data structures and views.

Architecture:

Raw / Source Data
→ Transformation
→ Business Dimension
→ Business Views

---

## 11. Dataset vs Inline Dataset

Explored the difference between standard datasets and inline datasets.

### Standard Dataset

A reusable dataset object created separately in ADF.

Useful when the same source or destination is used across multiple pipelines or data flows.

### Inline Dataset

Dataset configuration defined directly inside the Data Flow.

Useful for simpler or one-off scenarios.

---

## 12. Time To Live (TTL)

Explored the concept of Time To Live (TTL) and how it can be used to control how long data or cached information remains available.

---

## 13. Delta Lake

Started exploring Delta Lake concepts and how data engineering architectures can work with files instead of relying entirely on traditional relational tables.

Key idea:

Files can be treated as the primary data layer while still supporting structured data engineering patterns.

---

## 14. GitHub & Version Control

Connected the Azure Data Factory project with GitHub.

Practiced:

- Repository integration
- Branch creation
- Branch management
- Version control
- Tracking changes
- Working with different development branches
- Managing ADF changes through source control

This provides a foundation for collaborative development and CI/CD practices.

---

## 15. Data Governance

Explored Microsoft Purview and the concept of data governance.

Microsoft Purview helps organizations understand and manage data assets, including data lineage, discovery, and governance.

---

## Architecture

High-level architecture explored in this project:

Source / Local Files
        ↓
Self-Hosted Integration Runtime
        ↓
Azure Data Factory
        ↓
Incremental Ingestion
        ↓
Data Flow / Transformations
        ↓
Azure SQL / Data Lake
        ↓
Business Dimensions & Views
        ↓
Business Consumption

With monitoring:

ADF
 ↓
Web Activity
 ↓
Logic App
 ↓
Alert / Email

And version control:

ADF
 ↓
GitHub
 ↓
Branches
 ↓
Version Control

---

## Key Learning Outcomes

Through this project, I gained hands-on exposure to:

- Azure SQL fundamentals
- Azure Data Factory
- Self-Hosted Integration Runtime
- Data ingestion
- Incremental loading
- Watermark concepts
- Dynamic mapping
- Mapping Data Flows
- Conditional transformations
- Upsert patterns
- Parent-child pipelines
- Error handling
- Logic Apps
- Business dimensions and views
- GitHub integration
- Branching and version control
- Data governance concepts
- Delta Lake fundamentals
- Production-oriented pipeline design

---

## Next Steps

Continue building on these concepts with:

- Advanced Delta Lake
- Medallion architecture
- CI/CD
- Azure DevOps
- Automated deployments
- Advanced monitoring
- Data quality frameworks
- Production-grade data pipelines
  <img width="1837" height="907" alt="Screenshot 2026-08-15 143434" src="https://github.com/user-attachments/assets/731ccd8a-1531-4b8c-acf3-fe23324d1aee" />
  <img width="1037" height="677" alt="Screenshot 2026-08-15 170700" src="https://github.com/user-attachments/assets/beea6dfe-b184-431b-b33b-34de5ca88f0b" />
  <img width="1558" height="656" alt="Screenshot 2026-08-16 030828" src="https://github.com/user-attachments/assets/d9d0f042-dbb6-4824-9e98-edfa3475f0c1" />
  <img width="1040" height="618" alt="Screenshot 2026-08-16 030906" src="https://github.com/user-attachments/assets/63dbfa88-1446-4382-b0fa-3cdfffc9a9b8" />
  <img width="982" height="582" alt="Screenshot 2026-08-16 152019" src="https://github.com/user-attachments/assets/6c9bd575-fab2-4ed2-9a93-c4f1e81e83e2" />
 <img width="1322" height="378" alt="Screenshot 2026-08-16 153347" src="https://github.com/user-attachments/assets/5bb61140-987e-46de-b405-189f7a8c87b7" />
 <img width="939" height="369" alt="Screenshot 2026-08-16 153404" src="https://github.com/user-attachments/assets/3eb73f6c-a70e-410d-ba25-e6da6ee8f102" />
 <img width="1024" height="338" alt="Screenshot 2026-08-16 182241" src="https://github.com/user-attachments/assets/ec8c61f3-ac08-479b-abc0-b8793514a2ae" />
 <img width="1148" height="434" alt="Screenshot 2026-08-16 210528" src="https://github.com/user-attachments/assets/409ab2ca-fc10-46de-9243-7c2a9b8bbb00" />
<img width="1148" height="434" alt="Screenshot 2026-08-16 210528" src="https://github.com/user-attachments/assets/a4f3ba04-e06c-497e-a118-ca63123ac7d9" />
<img width="1878" height="435" alt="Screenshot 2026-08-16 233759" src="https://github.com/user-attachments/assets/ecfc49a0-e09f-43d4-b9ac-9ab1b7173c74" />








