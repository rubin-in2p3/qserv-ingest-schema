# qserv-dataloader
Configuration files and utilities related to the qserv database instance at CC-IN2P3


There are only 5 relevant directories in /sps/lsst/groups/qserv/dataloader :
- cosmoDC2_v1.1.4_image
- dc2_dr6_object_v2
- dc2_object_run2_2i_dr6_wfd
- dp01_dc2_catalogs
- skysim5000_v1.1.1


## Procedure (Draft)

The schemas need to be unambiguously identified and synchronised with the qserv ingest release.

The repository structure should be as:

```
├── README.md
├── cosmoDC2_v1.1.4_image
│   ├── Changelog.md
│   ├── v0
│   └── v1
├── dc2_object_run2_2i_dr6_wfd
│   ├── Changelog.md
│   ├── v0
│   └── v1
├── dc2_object_run2_2i_dr6_wfd_dpdd
│   ├── Changelog.md
│   ├── v0
│   └── v1
├── dp01_dc2_catalogs
│   ├── Changelog.md
│   ├── v0
│   └── v1
└── skysim5000_v1.1.1
    ├── Changelog.md
    ├── v0
    └── v1
```

Old versions of the schema should be kept and then for each modification a new directory containing all the modified schemas must be created and named v<X>, e.g v1, v2, etc.

Also, for each catalog, a changelog must be written and must mention the changes and the compatibility with qserv ingest version, e.g. 


| Schema Version | Qserv version | Notes      |
|----------------|---------------|------------|
| v0             | < 2022-01-01.rc1|          |
| v1             | 2022-01-01.rc1|            |

We set the `v0` as the version used before qserv `2022-01-01.rc1` and `v1` the version used starting with qserv `2022-01-01.rc1`.
From now on all the new versions have to be started from the last version available.
