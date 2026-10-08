# YouthOpps Data Source

Source-isolated opportunity records produced by `YouthOpps/data-pipeline`.

```
sources/<source-id>/opportunities.json
sources/<source-id>/metadata.json
```

Each source is independently collected and atomically committed. `opportunities.json` contains canonical records; `metadata.json` includes collection status, origin, and timestamps. The website builds its catalog from these files while retaining the original country and category taxonomy.

Only the designated pipeline workflow should write source data. Do not modify generated records manually.
