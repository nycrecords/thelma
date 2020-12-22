Azure Storage Tier
==================

* Status: Proposed
* Deciders: Joel Castillo (@joelbcastillo), Alexandra Dolan-Mescal (@alexandradm), Praveen Panchal, Sylvia Kollar
* Date: 2020-12-21

Context and Problem Statement
-----------------------------

DORIS is using Azure to store both long-term archival quality files and access copies of born-digital and digitized archival holdings. Due to the size of our collections we have decided to use a combination of hot (frequent access), cool (infrequent access), and archive (rarely accessed) storage tiers to save cost while still maintaining access to the data. As an archive, our data must be stored in such a way as to protect from data loss.

The purpose of this document is to document the decision made as to what combination of storage tiers will be used to manage the DORIS Digital Archive (THELMA).

Decision Drivers
----------------

* Redundancy
* Cost of Storage
* Availability
* Ease of Access

Decision Outcome
----------------

Create two separate storage accounts:

1) THELMA Reference - Stores access copies of data in Zone-Redundant Storage using the Cool or Hot access tiers.
2) THELMA Archive - Stores master files of data in GRS Storage using the Archive access tiers.

### Positive Consequences

* Multiple storage accounts allows DORIS to prioritize availability and durability across different collections.
  * Access Copies will have High Availability within a single region.
  * Master Files will have durability across multiple regions.
* DORIS will be able to save costs by applying lifecycle rules for data stored in each storage account to automate the migration of data between access tiers.

### Negative Consequences

* DORIS will need to manage multiple storage accounts.
* THELMA will need to be built to be able to use multiple storage accounts to manage data in the archive.

Pros and Cons of the Options
----------------------------

### 1. Locally Redundant Storage (LRS)

LRS replicates data three times within a single physical location in the primary region. It provides 99.999999999% (11 nines) durability of objects over a given year. LRS supports Hot, Cool, and Archive storage. LRS is the best option for data that can easily be reconstructed or regenerated.

#### Pros

* Lowest-cost redundancy option for storage in Azure
* Protects against server rack and hard drive failures
* Supports all storage access tiers (Hot, Cool, and Archive)

#### Cons

* Does not protect agains the loss of a data center (natural disaster, network connectivity, power outages). Data may not be recoverable in this case

### 2. Zone Redundant Storage (ZRS)

ZRS replicates data across three availability zones in the primary region. Each availability zone is a separate physical location with independent power, cooling and networking. It provides 99.9999999999% (12 nines) durability of objects over a given year. ZRS is best for data that requires consistent access and availability in a single region.

#### Pros

* Protects against loss of a data center in a region (i.e supports high availability)
* Supports Hot and Cool storage access tiers

#### Cons

* Does not protect against the loss of a region
* Does not support Archive storage access tier

### 3. Geo-Redundant Storage (GRS)

GRS replicates using LRS in both the primary and secondary region. The secondary region is hundreds of miles away from the primary region. It provides 99.99999999999999% (16 nines) durability of objects over a given year. GRS is best for data that needs to be stored securely (even if access to that data takes a longer period of time).

#### Pros

* Protects against loss of an entire region (e.g. a data center in that region) and supports disaster recovery
* Protects agains the loss of a rack or drive in a data center
* Supports Hot, Cool, and Archive storage access tiers
* Lowest cost regional redundancy option

#### Cons

* Secondary region is not available for read access
* Azure Storage RPO (Recovery Point Objective) is generally 15 minutes, but there is no SLA for it. If data is written to the primary region there is a chance it does not replicate to the secondary region if there is an outage within the RPO window

### 3. Geo-Zone-Redundant Storage (GZRS)

GZRS replicates using ZRS in the primary region and LRS in the secondary region. The secondary region is hundreds of miles away from the primary region. It provides 99.99999999999999% (16 nines) durability of objects over a given year. GZRS is best for data that needs to be stored securely and needs high availability.

#### Pros

* Protects against loss of an entire region
* Supports Hot and Cool storage access tiers

#### Cons

* Secondary region is not available for read access
* Does not support Archive storage access tier
* Azure Storage RPO (Recovery Point Objective) is generally 15 minutes, but there is no SLA for it. If data is written to the primary region there is a chance it does not replicate to the secondary region if there is an outage within the RPO window.

### 3. Read-Access Geo-Redundant Storage (RA-GRS)

RA-GRS replicates using LRS in the primary and secondary region. The secondary region is hundreds of miles away from the primary region. It provides 99.99999999999999% (16 nines) durability of objects over a given year. RA-GRS is best for data that needs to be stored securely and needs high availability.

#### Pros

* Protects against loss of an entire region
* Supports Hot, Cool and Archive storage access tiers

#### Cons

* Azure Storage RPO (Recovery Point Objective) is generally 15 minutes, but there is no SLA for it. If data is written to the primary region there is a chance it does not replicate to the secondary region if there is an outage within the RPO window.

### 5. Read-Access Geo-Zone-Redundant Storage (GZRS)

GZRS replicates using ZRS in the primary region and LRS in the secondary region. The secondary region is hundreds of miles away from the primary region. It provides 99.99999999999999% (16 nines) durability of objects over a given year. GZRS is best for data that needs to be stored securely and needs high availability.

#### Pros

* Protects against loss of an entire region
* Supports Hot and Cool storage access tiers

#### Cons

* Does not support Archive storage access tier
* Azure Storage RPO (Recovery Point Objective) is generally 15 minutes, but there is no SLA for it. If data is written to the primary region there is a chance it does not replicate to the secondary region if there is an outage within the RPO window.


Links
-----

* [Microsoft Documentation - Access Tiers](https://docs.microsoft.com/en-us/azure/storage/blobs/storage-blob-storage-tiers?tabs=azure-portal)
* [Microsoft Documentation - Data Redundancy](https://docs.microsoft.com/en-us/azure/storage/common/storage-redundancy?toc=/azure/storage/blobs/toc.json#redundancy-in-the-primary-region)
