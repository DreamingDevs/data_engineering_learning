# Microsoft Fabric  

**Date:** 25 Nov 2025

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

### Where Copilot Can Be Used

#### 1. Data Pipelines (Data Factory)
- Pipeline development through natural language (NLP)
- Error categorization and explanation
- Root-cause analysis for failures
- Recommended corrective actions
- Automatic pipeline documentation and summaries
- Build/Explain dynamic pipeline expressions

#### 2. Notebooks (Data Engineering / Data Science)
- Coding assistant for starter code and iterative development
- Error analysis and explanation
- Auto-generated documentation and comments
- Context-aware code suggestions based on data, schema, and notebook state

### Additional Considerations

- **Consumes Fabric Capacity:**  
  Copilot runs on your Fabric capacity; heavy usage may affect consumption and performance.

- **Tenant-Level Governance:**  
  Admin controls for enabling/disabling Copilot, managing data sent to Azure OpenAI, and defining data residency rules.

- **Non-Deterministic Behavior:**  
  Generated outputs may vary across sessions due to the nature of LLMs.

---


