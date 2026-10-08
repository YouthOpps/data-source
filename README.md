# YouthOpps Data Source

Public, source-isolated snapshots written by [data-pipeline](https://github.com/YouthOpps/data-pipeline).

```text
catalog.json                       # Derived website index
sources/<source-id>/metadata.json  # Publisher, adapter, collection state
sources/<source-id>/opportunities.json  # Canonical opportunities
```

Each GitHub Action processes one publisher and writes its own files together with the rebuilt `catalog.json` in **one commit**. A shared concurrency group serializes writers. Source snapshots are retained if collection fails, so a failed request never replaces valid published data. The website reads a commit-pinned `catalog.json`; country and category filters are derived from the canonical records.

Contributions to source adapters belong in [data-pipeline](https://github.com/YouthOpps/data-pipeline). Use GitHub Discussions or Issues first; contact@youthopps.org is the fallback contact.
