# Qserv ingest schema

## Compatibility

| Schema Version | Qserv version | Replication Client version|  Notes     |
|----------------|---------------|---------------------------|------------|
| v0             | < 2022.1.1-rc1|     NA                    | Compatibility not clear/unknown |
| v8             | >= 2022.1.1-rc1  |      8                    |            |
| v9             | >= 2022.9.1-rc1  |      9                    |      Added format to set the separator      |

## General informations

This repository contains schema configuration related to the qserv database instance at CC-IN2P3.

There are 6 relevant catalogs available at CC-IN2P3 (under `/sps/lsst/groups/qserv/dataloader/stable`).

Four have been ingested:

- dp01_dc2_catalogs
- skysim5000_v1.1.1_parquet
- cosmoDC2_v1.1.4_image
- idf-dp0.2-catalog-chunked2

The two following catalogs have not been ingested:

- dc2_dr6_object_v2
- dc2_object_run2_2i_dr6_wfd

The schema configurations in this repository are covering the above catalogs.

## Repository structure

The repository structure is the following:

```
├── CHANGELOG.md
├── README.md
├── cosmoDC2_v1.1.4_image
│   ├── v0
│   ├── v8
│   └── v9
├── dc2_dr6_object_v2
│   └── v0
├── dc2_object_run2_2i_dr6_wfd
│   ├── dpdd
│   ├── v0
│   ├── v8
│   └── v9
├── dp01_dc2_catalogs
│   ├── v0
│   ├── v8
│   └── v9
├── idf-dp0.2-catalog-chunked
│   ├── v8
│   └── v9
└── skysim5000_v1.1.1_parquet
    ├── v8
    └── v9
```

For each catalog different version of the schema are available and identified by directory `v<x>` (e.g. `v0`, `v8`): this allow to unambiguously identify the schema and synchronise them with the qserv ingest release.

Starting from Qserv version `2022.1.1-rc1`, the version number is the same of the `Replication Client version`, as shown in the above [table](#Compatibility).

We set the `v0` as the version used before qserv `2022.1.1-rc1` because compatibility with replication client is either not clear or unknown.

Note, for `dc2_object_run2_2i_dr6_wfd` also a DPDD-like schema is available under `dc2_object_run2_2i_dr6_wfd/dpdd`.

## Use a schema

To use the schema in this repository you must clone the repository (a version is available in `/sps/lsst/groups/qserv/dataloader/qserv-ingest-schema`):

```
git clone https://github.com/in2p3-dp0/qserv-ingest-schema.git
```

and copy all the json schema files to the corresponding directory on `/sps/lsst/groups/qserv/dataloader/stable`.

## Update a schema

If one or more catalog's schema need to be update, the following procedure must be followed:

1. create a new branch from the main, e.g. `git checkout -b skysim_v9`
2. create the corresponding directory, e.g. `mkdir skysim5000_v1.1.1_parquet/v9`
3. make the modification to the schema and commit/push it
4. update the changelog  mentioning the changes and update the compayibility table in this README
5. create a pull request to the main branch.
