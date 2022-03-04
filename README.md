# Qserv ingest schema


This repository contains schema configuration related to the qserv database instance at CC-IN2P3.


There are 5 relevant catalogs available at CC-IN2P3 (under `/sps/lsst/groups/qserv/dataloader/stable`).

Three have been ingested: 

- dp01_dc2_catalogs
- skysim5000_v1.1.1_parquet
- cosmoDC2_v1.1.4_image


The two following catalogs have not been ingested: 

- dc2_dr6_object_v2
- dc2_object_run2_2i_dr6_wfd


The schema configurations in this repository are covering the above catalogs. 


## Repository structure

The repository structure is the following:


```
├── README.md
├── cosmoDC2_v1.1.4_image
│   ├── CHANGELOG.md
│   ├── v0
│   └── v1
├── dc2_dr6_object_v2
│   └── v0
├── dc2_object_run2_2i_dr6_wfd
│   ├── CHANGELOG.md
│   ├── dpdd
│   ├── v0
│   └── v1
├── dp01_dc2_catalogs
│   ├── CHANGELOG.md
│   ├── v0
│   └── v1
└── skysim5000_v1.1.1_parquet
    ├── CHANGELOG.md
    ├── v0
    └── v1
```


For each catalog different version of the schema are available and identified by directory `v<x>` (e.g. `v0`, `v1`): this allow to unambiguously identify the schema and synchronise them with the qserv ingest release.

Note, for `dc2_object_run2_2i_dr6_wfd` also a DPDD-like schema is available under `dc2_object_run2_2i_dr6_wfd/dpdd`.

We set the `v0` as the version used before qserv `2022-01-01.rc1` and `v1` the version used starting with qserv `2022-01-01.rc1`.

For each catalog, the CHANGELOG return also the compatibility between the schema and qserv ingest, e.g. 

| Schema Version | Qserv version   | Notes      |
|----------------|-----------------|------------|
| v0             | < 2022-01-01.rc1|            |
| v1             | 2022-01-01.rc1  |            |

## Use a schema

To use the schema in this repository you must clone the repository (a version is available in `/sps/lsst/groups/qserv/dataloader/qserv-ingest-schema`):

```
git clone https://github.com/in2p3-dp0/qserv-ingest-schema.git
```

and copy all the json schema files to the corresponding directory on `/sps/lsst/groups/qserv/dataloader/stable`.


## Update a schema

If one or more catalog's schema need to be update, the following procedure must be followed: 

1. create a new branch from the main, e.g. `git checkout -b skysim_v2`
2. create the corresponding directory, e.g. `mkdir skysim5000_v1.1.1_parquet/v2`
3. make the modification to the schema and commit/push it
4. update the changelog  mentioning the changes and the compatibility with qserv ingest version, e.g. 


| Schema Version | Qserv version | Notes      |
|----------------|---------------|------------|
| v0             | < 2022-01-01.rc1|          |
| v1             | 2022-01-01.rc1|            |
| v2             | 2022-04-01.rc1|            |


5. create a pull request to the main branch 



