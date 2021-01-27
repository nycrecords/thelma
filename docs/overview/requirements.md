# THELMA Feature Requirements

## Trusted Digital Repository

1. Individual / Bulk Ingest of Data (Media and Metadata)

2. Create SIP/AIP/DIP Bags of Media and Metadata

3. Create Open Format Versions of Media

4. Send DIP to Digital Archive Site

### Content Versioning

Create new bag when items are updated from the digital archive site by staff.

Archivematica has functionality to Re-ingest data to add metadata / re-process for transition.

It looks like it isn't possible to re-ingest / recreate the AIP to add new data, just modify the original data.

It should be possible to store multiple AIPs with the same accession number which would allow us to link them in the storage platform.

Work Required:

- Research how to re-ingest Archivematica data

Estimates:

- 2 Weeks research (requires demo environment)

### Redundant Storage

See [ADR#01 - Azure Storage Tier](../../adr/01_azure_storage_tier.md)

### Fixity Checks with Notification of Changes

The purpose of fixity checks is to ensure that data stored in the preservation vault stays in good condition.

This is built into Archivematica - [Fixity Checking - Archivematica Storage Service](https://www.archivematica.org/en/docs/storage-service-0.17/fixity/#fixity-docs)

Work Required

- Setup automatic fixity checking weekly using the [Fixity Application](https://github.com/artefactual/fixity)

Estimate: 1 Week for development of a cloud function to run this automatically and generate an email report.

### SIP Creates Multiple Derivative Sizes (Based on Transfer Type)

Allow the Archives to create different types of derivatives during processing (different resolutions, thumbnails, etc.).

Archivematica has [processing configuration](https://www.archivematica.org/en/docs/archivematica-1.12/admin-manual/installation-setup/customization/dashboard-config/#process-config) to allow ingest to be handled differently.

Work Required:

- Generate processing configurations for different collection and media types

Estimate:

- 1 Week Research on Creating Processing Configurations and Microservices
- 1 Week Development of Processing Configuration

Note: New processing configurations would require appdev involvement.

Estimate: 1 week for research on how to create processing configurations

### Add Watermark to Derivatives (Based on Transfer Type)

When generating DIPs, ability to watermark derivatives to protect data from being taken.

Archivematica has a microservice for processing images with Imagemagick. We should be able to write a script that processes the images and creates watermarks on them.

Work Required:

- Develop script to use Imagemagick to watermark images
- Setup processing capabilities for Imagemagick during the Archivematica Normalization step.

Estimates:

- 1 Week Research on Imagemagick and Archivematica Normalization
- 1 Week Development of watermarking script

## Staff Workflows

### Bulk Upload Metadata to Create Records

this should kick off the creation of record, with media then attached by filename (unique identifier)

Bulk upload will 

### Create and Edit Individual Metadata Record

per asset type

### Attach Media

link/unlink media (single or multiple) to existing metadata record. default primary would be first image attached

### Select Primary Image

select still thumbnail from video; select which image is primary for multi-image, PDF?

### Batch Update Metadata

by collection, from search results (with select all/select options)

### Feature Items/Exhibits/Collections on Homepage



### NYC ID login for Staff

login with nycid

### Staff Homepage

recently updated/added? user list, total number of items

### Data Model: Asset Types

will likely need a few different metadata schemas based on object type, built off of basic TDR fields and DublinCore. fields will need validation (i.e. ISO 8601 for dates) - lots of work to be done here

### Data Model: Entities

table for entities - LOC NAF and local naming convention. link to names records in ArchivesSpace?

### Data Model: Collections

basic metadata schema (DACS) for collections, linking to ArchivesSpace resource records

### Data Model: Events

DA cases / mayoral events (tbd with archives team)

### Edit Homepage / About Page Text

WYSIWIG for each section of public facing editable text

### Different Features based on User Status

presumably only want admins to have access to some features

### Make Items Public / Not Public



### User Administration



### Create Exhibits



title, subtitle, add items in order, drag and drop items and sections, text boxes"

### Upload and Share Reference Scans for Patrons

so that patrons can identify what they want digitized by DP - a third type of storage item, possibly temporary. only a DIP via Archivematica?

## Public Access

### Homepage 

intro text, logo, title, highlighted exhibits, collections, items? recently added?

### Browse all items, with filters

filter by: date, collection, creator, subject tags, media format

### View collections/collection

landing page for all (with filters?) and individual page

### View item

media viewers for images, av, and pdfs. If a record has multiple images attached, how do we 
want the viewer to handle that?

### View pages as book

mirador book viewer?

### Basic and advanced search 

keywords, common metadata fields

### View digital exhibits/exhibit

landing page for all (with filters?) and individual page

### User login

public to be able to log in to save items NYCID has third party integration logins

### Cart sets

add items and collections to sets, with ability to name sets. ability to request high 
resolution?

### Cart research appt

link to set up research request based on items in cart 

### annotation feature?

### About page

basic text page

### purchase prints link

link to nyc.gov forms

### license video link

new form for licensing AV
