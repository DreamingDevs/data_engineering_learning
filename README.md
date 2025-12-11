# Microsoft Fabric

**Date:** 10 Dec 2025

- OneLake Security
    - Supports Contributor, Reader, Restricted (ReadWrite for specific schemas
- Anomaly detector (Preview) for Fabric Real Time Intelligence (RTI) detects unusal patterns and outliers from streaming data of Eventhouse tables.
    - Wide range of models for detection and can be tuned for sensitivity
    - Billing to Fabric CU for query execution, not based on data volume

---

**Date:** 08 Dec 2025

- EON stores Database backups as Iceberg tables which can be made available in Fabric OneLake through shortcuts which are available in OneLake catalog which can be then discovered and queried.

---

**Date:** 07 Dec 2025

### Lakehouse Materialized views
- Lakehouse Schema (Preview)- Once enabled cannot be disabled. For old LH, create new LH.
    - Materialized views in LH can be created using Spark SQL.
    - Materialized views pre-compute costly aggregations.
    - Schedule refreshes can be defined by us, but fabric is intelligent to refresh only when changes are present.
    - Fabric shows lineage of materialized views.
 
### CDC Copy Job
- Copy job can handle incremental inserts, updates and deletes when source tables are CDC enabled
    - Inserts, Updates and Hard deletes are supported for CDC enabled tables
    - Inserts and updates are supported for normal tables which have watermark columns
 
### Dataverse ingest into Fabric
- Dataverse tables can be directly ingested to Fabric workspace without ETL/ELT
    - CDC can be used to copy data from Dataverse LH data to destinations using Copy Job

---

**Date:** 06 Dec 2025

- Mirroring Google BigQuery in Microsoft Fabric (Preview)

### AWS S3 secure access using Entra and VPC

- Register a service principal in Microsoft Entra ID.
- Configure an OIDC trust relationship between Entra and AWS IAM.
- Create an IAM role and policy that grants the required S3 permissions.
- Configure EC2 instance with VPC endpoint / network path to S3.
- Install and configure the on-premises data gateway in EC2 network.
- Verify that the gateway can reach the S3 endpoint privately.
- Create a Fabric connection that uses your Entra service principal–based integration.
- When creating the Amazon S3 shortcut, select the connection and the on-premises data gateway.
- Browse to the VPC-protected bucket or folder and complete the shortcut creation.
  
---

**Date:** 05 Dec 2025

 - Fabric notebooks support Workspace identity
 - OneLake data (including Shortcuts) available in Azure Foundry for knowledge sources
 - OneDrive and Sharepoint Shortcuts (preview) to get data into OneLake

---

**Date:** 03 Dec 2025

## Variable Sets

- Workspace level item, scoped per workspace
- Bucket to hold the variables and value sets, set active to a value set
- Environment specific value sets
- Can be consumed by other items in workspace
- CI/CD compatible
- It is not a secret store

---

**Date:** 29 Nov 2025

## User Data Functions

- Host and execute own code, exposed as UDF functions, also exposed as APIs
- Can use Public Python libraries, Custom own python packages, Fabric Connections in the code of UDF
- Reusability across workspaces in many fabric items like notebooks, pipelines, Power BI etc.
- Fabric portal editor, VS code as well
- Consumes Fabric capacity
- Notebook cells are local to notebook, however UDF are standalone and hosted in server
- Can be invoked across multiple workspaces and capacities

---

**Date:** 29 Nov 2025

## JDBC Driver for Data engineering

- Regular JDBC is not data engineering friendly
- New JDBC Driver designed to connect to Spark workloads, can submit Spark SQL from Java apps also
- Start spark session, configure its resources. Can talk to spark clusters.
- Follows JDBC standard and support Spark SQL data types (Array, Map, Struct)
- It can read anything which spark can read
- Allows all flows from Microsoft Entra Authentication
- Connection pooling, auto-reconnect, circuit breaker, result-set prefetching, proxy support
- Cannot work with regular Databases

---

**Date:** 26 Nov 2025

## Spark optimizations
- Disable v-order for optimizing writes
- Enable auto compaction for reducing lot of files
- Enable Fast optimization
- Enable native execution engine
- Configure WriteHeavy, Readheavy profile
- Check spark actions usage

 ---
 
**Date:** 25 Nov 2025

## Data Virtualization in Fabric SQL (Preview)
- Data Virtualization (Preview) for Fabric SQL Databases, enable to query and ingest OneLake data (CSV, Parquet, JSON)
- No duplication of data
- Combine OPENROWSET and External Tables with BULK operations

## Copy Job (General Availability)
- Supports full / Incremental / CDC data refreshes
- Deletes can only be handled in CDC refresh (source DB should have CDC enabled)
- Inserts / Updates only be handled in Incremental data refresh
- Full will overwrite the entire table
- Incremental - 3CUs, Full - 1.5 CU

 ---
 
**Date:** 23 Nov 2025

## Open Mirroring Overview
- Mirrored database creates OneLake landing zone and creates Delta tables with read-only sql endpoint.
- files Without __rowMarker__ are always inserts, otherwise inserts, updates, deletes (PK would be required for upserts)
- The _metadata.json file (defining key columns, formats, etc.) is mandatory for update/insert behavior.
- Can add new columns
- Rename and changing data types needs full table recreation

---

**Date:** 22 Nov 2025

## Copilot in Microsoft Fabric — Key Capabilities & Considerations

- Pipeline development through natural language (NLP)
- Error categorization and explanation
- Root-cause analysis for failures
- Recommended corrective actions
- Automatic pipeline documentation and summaries
- Build/Explain dynamic pipeline expressions
- Copilot runs on your Fabric capacity; heavy usage may affect consumption and performance.
- Admin controls for enabling/disabling Copilot, managing data sent to Azure OpenAI, and defining data residency rules.

---


