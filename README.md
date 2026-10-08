# YouthOpps Data Source

Public JSON snapshots written by [data-pipeline](https://github.com/YouthOpps/data-pipeline).

```text
catalog.json                            # Unified website index
sources/<source-id>/metadata.json       # Publisher and collection state
sources/<source-id>/opportunities.json  # Canonical opportunities
```

Each enabled source has one `fetch-<source-id>` GitHub Action **in data-pipeline**. It validates and writes its source files and rebuilt `catalog.json` in a single commit when data changes. Shared concurrency serializes writes; a failed collection preserves the previous snapshot. JSON files are indented with two spaces and end with a newline.

This repository has **no GitHub Actions**. The [website](https://github.com/YouthOpps/youthopps.github.io) consumes it as a pinned Git submodule. The website's hourly `check new data` Action updates its own submodule reference when this repository changes.

Contribute source adapters in [data-pipeline](https://github.com/YouthOpps/data-pipeline). Prefer GitHub Discussions and Issues; contact@youthopps.org is the private-contact fallback.
