# Microsoft Fabric  

**Date:** 29 Nov 2025

## JDBC Driver for Data engineering

- Regular JDBC is not data engineering friendly
- New JDBC Driver designed to connect to Spark workloads, can submit Spark SQL from Java apps also
- Start spark session, configure its resources. Can talk to spark clusters.
- Follows JDBC standard and support Spark SQL data types (Array, Map, Struct)
- It can rread anything which spark can read
- Allows all flows from Microsoft Entra Authentication
- Connection pooling
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
- Deletes can only be handled in CDC refresh
- Inseets / Updates only be handled in Incremental data refresh
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


