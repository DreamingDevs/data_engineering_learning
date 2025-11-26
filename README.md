# Microsoft Fabric  

**Date:** 26 Nov 2025

## Spark optimizations
- Disable v-order for optimizing writes
- Enable auto compaction for reducing lot of files
- Enable Fast optimization
- Enable native execution engine
- Configure WriteHeavy, Readheavy profile
- Check spark actions usage

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
- A mirrored database is provisioned in Fabric, automatically generating a OneLake landing zone for file ingestion.
- Upload initial Parquet or CSV files into the landing zone.  
  Without `__rowMarker__`, all rows are treated as **initial inserts**.
- Fabric mirroring ingests the files and materializes them as **Delta tables**, with a **read-only SQL analytics endpoint** for querying.
- When files include `__rowMarker__`, the engine applies **incremental inserts, updates, upserts, and deletes**.  
  The **`_metadata.json`** file (defining key columns, formats, etc.) is mandatory for update/insert behavior.
- **Adding new columns** → Supported; older rows get `NULL` for new columns. **Renaming columns or changing data types** → Not supported in-place; requires **full table recreation and reprocessing** of all files.
- Earlier versions required a **PK** always. For incremental processing, **PK + `__rowMarker__`** are required so the engine can identify and apply changes correctly.

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


