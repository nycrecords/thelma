# THELMA Terraform
- [THELMA Terraform](#thelma-terraform)
    - [Introduction](#introduction)
    - [What is THELMA?](#what-is-thelma)
    - [Components](#components)
        - [ArchivesSpace](#archivesspace)
            - [Technical Details](#technical-details)
            - [Resources](#resources)
        - [DSpace](#dspace)
            - [Resources](#resources)
        - [Archivematica](#archivematica)
        - [Hyku / Fedora](#hyku--fedora)
        - [Koha](#koha)
    - [Cloud Hosting](#cloud-hosting)
    - [Contributing](#contributing)

## Introduction
This repository contains the terraform scripts to build out the NYC Municipal Archives THELMA Digital Platform using AWS / Azure.

## What is THELMA?
THELMA is the digital content management system for the NYC Municipal Archives and Library. Using open-source components, it is a full pipeline of tools to assist in the long-term preservation and storage of the assets of the Municipal Library and Archives. Additionally, it provides a public access interface to allow researchers to access our digitized holdings from anywhere in the world. 

## Components
### ArchivesSpace
> [ArchivesSpace](http://archivesspace.org/) is the next-generation web-based archives information management system, designed by archivists and supported by diverse archival repositories.

The NYC Municipal Archives uses ArchivesSpace to maintain its up-to-date collection inventories for its holdings. 

#### Technical Details

#### Resources
- [Github Repository (archivesspace/archivesspace)](https://github.com/archivesspace/archivesspace)
- [ArchivesSpace Technical Documentation](http://archivesspace.github.io/archivesspace/)
- [ArchivesSpace Wiki](https://archivesspace.atlassian.net/wiki)

### DSpace
DSpace is a turnkey repository application used to provide durable access to digital resources. The Municipal Library uses DSpace to serve its digital collections for Government Reports. 

DSpace is currently used to facilitate the submission process for government reports but will eventually be used as a search interface as well.

To search for current government reports, please visit the NYC [Government Publications Portal](http://a860-gpp.nyc.gov)
#### Resources
- [CityOfNewYork/DSpace](https://github.com/cityofnewyork/dspace)
- [DSpace/DSPace](https://github.com/dspace/dspace)
- [CityOfNewYork/DORIS-Publications-Portal](https://github.com/cityofnewyork/doris-publications-portal)
### Archivematica

### Hyku / Fedora
TODO

### Koha
TODO

## Cloud Hosting
The Municipal Archives and Library are currently in the process of identifying where to host our digital platform. As a result, this repository will contain terraform scripts for Amazon Web Services, Microsoft Azure, and Google Cloud Platform as we evaluate our options. 

## Contributing
TODO