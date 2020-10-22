THELMA Production Compute / Networking
==============================

Servers
-------

### Production

|         Application         | Number of Servers |  CPU  |  RAM  |                Storage                |                                       Notes                                        |
| :-------------------------: | :---------------: | :---: | :---: | :-----------------------------------: | :--------------------------------------------------------------------------------: |
|      THELMA Front-End       |         2         |   4   |  16   | 250 GB (OS - 50 GB, Storage - 200 GB) |                                                                                    |
| ArchivesSpace - Application |         2         |   2   |   8   | 150 GB (OS - 50 GB, Shared - 100 GB)  |                   Shared storage can be NFS share or equivalent                    |
|        Archivematica        |         3         |   8   |  32   | 4.05 TB (OS - 50 GB, Storage - 4 TB)  | Storage is used to store ingests. Maximum ingest size is 1 TB. Needs to be shared. |
|         ELK Cluster         |         3         |   4   |  32   | 250 GB (OS - 50 GB, Storage - 200 GB) |                                                                                    |
|        MySQL Cluster        |         3         |   4   |  16   | 250 GB (OS - 50 GB, Storage - 200 GB) |                                     MySQL 5.7                                      |

### Non-Prod

|         Application         | Number of Servers |  CPU  |  RAM  |                Storage                |                                           Notes                                           |
| :-------------------------: | :---------------: | :---: | :---: | :-----------------------------------: | :---------------------------------------------------------------------------------------: |
|      THELMA Front-End       |         1         |   4   |  16   | 250 GB (OS - 50 GB, Storage - 200 GB) |                                                                                           |
| ArchivesSpace - Application |         1         |   2   |   8   | 150 GB (OS - 50 GB, Shared - 100 GB)  |                       Shared storage can be NFS share or equivalent                       |
|        Archivematica        |         1         |   8   |  32   | 1.05 TB (OS - 50 GB, Storage - 1 TB)  | Storage is used to store ingests. Maximum test ingest size is 250 TB. Needs to be shared. |
|         ELK Cluster         |         1         |   4   |  32   | 250 GB (OS - 50 GB, Storage - 100 GB) |                                                                                           |
|        MySQL Cluster        |         1         |   4   |  16   | 250 GB (OS - 50 GB, Storage - 100 GB) |                                         MySQL 5.7                                         |

Networking
----------

1 x Load Balancer per Environment

Storage
-------

### Production

HDD Storage

- 250 GB - OS Drives
- 500 GB - Extra drives

Shared Storage (NFS / Shared HDD)

- 4 TB Shared for Ingests

Long Term Storage 

- Next 12 Months - 400 TB
- Yearly Growth - 300 TB -> 1.3 PB (Please provide options for both)

### Non-Prod

HDD Storage

- 250 GB - OS Drives
- 500 GB - Extra drives

Shared Storage (NFS / Shared HDD)

- 1 TB Shared for Ingests

Long Term Storage

- 5 TB
