# Microsoft Fabric  
 
**Date:** 23 Nov 2025

## Open Mirroring Overview

- **Created mirrored database**  
  A mirrored database is provisioned in Fabric, automatically generating a OneLake landing zone for file ingestion.

- **Initial load using Parquet/CSV (no `__rowMarker__`)**  
  Upload initial Parquet or CSV files into the landing zone.  
  Without `__rowMarker__`, all rows are treated as **initial inserts**.

- **Mirroring ingestion**  
  Fabric mirroring ingests the files and materializes them as **Delta tables**, with a **read-only SQL analytics endpoint** for querying.

- **Incremental operations using `__rowMarker__`**  
  When files include `__rowMarker__`, the engine applies **incremental inserts, updates, upserts, and deletes**.  
  The **`_metadata.json`** file (defining key columns, formats, etc.) is mandatory for update/insert behavior.

- **Schema evolution**  
  - **Adding new columns** → Supported; older rows get `NULL` for new columns.  
  - **Renaming columns or changing data types** → Not supported in-place; requires **full table recreation and reprocessing** of all files.

- **Primary key requirements**  
  - Earlier versions required a **PK** always.  
  - For incremental processing, **PK + `__rowMarker__`** are required so the engine can identify and apply changes correctly.
