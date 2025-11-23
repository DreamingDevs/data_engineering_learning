Microsoft Fabric

23 Nov, 2025
Open Mirroring
  - Created mirrored database
  - Upload initial parquet, CSV files (without __rowMArker__) to OneLake landing zone
  - Mirroring ingests the data and make it available in Delta format and read-only SQL analytics endpoint
  - If file got __rowMarker__, then it uses for incremental upsert, delete, insert and updates. _metadata.json is important for updates and inserts.
  - Adding new columns is simple. Renaming, changeing data types is difficult, need to reprocess all the files.
  - Previously PK is must, if incremental is required, then PKs and __rowMarker__ are required.
