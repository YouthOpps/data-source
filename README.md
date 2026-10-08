# YouthOpps Data Source

Public JSON snapshots written exclusively by authorized [data-pipeline](https://github.com/YouthOpps/data-pipeline) publication Actions, except exceptional manual administrator recovery. Develop adapters and open PRs in data-pipeline; agents must not directly commit, push or open PRs here. This repository has no GitHub Actions.

## Published files

```text
datas/<source-id>/data.json       # Last successfully validated nonempty opportunities
datas/<source-id>/metadata.json   # Authoritative result of the latest attempt
```

`data.json` is an array of actual publisher opportunities validated by its self-contained [source adapter](https://github.com/YouthOpps/data-pipeline/tree/main/adapters). No root catalog, source index or aggregate manifest is published.

Each metadata document identifies the source and publisher attribution and records:

- `status`: `success` or `fail`.
- `message`: a concise explanation of the outcome.
- `last_attempt_at`: the latest attempt in UTC ISO-8601.
- `last_success_at`: the last successful nonempty validated retrieval in UTC ISO-8601.
- On failure, a sanitized actionable `error` and the failure stage when known.

A failed attempt updates metadata while preserving all last-good data and the previous success timestamp. An adapter with no successful publication does not create an empty published folder. Each Action writes only its own adapter's files. Serialized publication protects concurrent updates; a failure to persist status must be reported as a failed run.

## Layout migration and consumers

Historical `sources/<source-id>/opportunities.json` files move to `datas/<source-id>/data.json`, preserving valid records and successful collection timestamps. Metadata outcomes `ok` and `error` become `success` and `fail`. The former root `catalog.json` is removed. A layout migration is not a new successful retrieval.

The [website](https://github.com/YouthOpps/youthopps.github.io) consumes a pinned data-source submodule and currently expects the old catalog. Its consumer code must adopt the new layout and outcome values before advancing that pin. Coordinate its automatic submodule updater before production migration. Consumer discovery belongs to the website's approved design; this repository does not provide an aggregate index.

Use [Discussions](https://github.com/orgs/YouthOpps/discussions) and [pipeline issues](https://github.com/YouthOpps/data-pipeline/issues). Private contact: contact@youthopps.org.
