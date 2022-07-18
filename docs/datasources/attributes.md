# Metadata and Structural Attributes of Federal Reserve Regulated Institutions

Non-financial information about financial institutions regulated by the Federal Reserve is often referred to as "structural" or "attribute" data.

For purposes of identifying the financial institutions to which a time series referred - or to filter time series data by particular attributes of financial institutions - the structural/attribute data may be merged or joined with the time series data.

## The Basics

Each and every financial company, branch, related institution, and subsidiary regulated by the Federal Reserve is assigned an "RSSD", an integer number no longer than 10 characters.

The RSSD number itself does not contain any semantic data - the number, or digit positions do not represent any data that describes the institution itself.

### Mergers, Acquisitions, and Resolutions

The RSSD assigned a bank branch, institution, or other organizational component remains the same throughout any merger or acquisition transaction, as long as the respective entity is a "survivor" of the transaction.

Once an RSSD is utilized for an entity, the RSSD is not reused.

### Relationship to Other Regulators Identification Schemes

While the RSSD is the most prevelant and comprehsive identification scheme (with repect to the count and breadth of institutions covered), other Federal regulatory agencies use other institution identification schemes:

#### Federal Deposit Insurance Corporation (FDIC)

For depository institutions (banks), the FDIC uses "certificate" numbers; this number represents the number assigned to the deposit insurance certificate granted to the bank. For all financial data reported by the FDIC, this ID, indicated at the `CERT` field, is the primary institution ID.

The Federal Reserve's attribute data does includes a crosswalk to the FDIC certificate number.

##### Bank Branches

For bank branches, the FDIC also assigns a _branch number_, whose value is a sequential integer, and a _UNINUM_, a unique integer number assigned to the branch by the FDIC.

There is no publically available crosswalk between the FDIC branch _UNINUM_ and the _RSSD_ assigned by the Federal Reserve to the respective branch.

#### Office of the Comptroller of the Currency (OCC)

The Office of the Comptroller of the Currency (OCC) also uses a separate ID numbering scheme, known as the `OCC ID`.

## Data Acqusition and Analysis

### The `ATTRIBUTES` Files

The Federal Reserve tracks changes to the corporate structure of financial institutions, their branches, subsidiaries, related entities, and holding companies, ("entities") on a continuous basis in an internal transaction table known as the `ATTRIBUTES` record.


Each row in this table indicates an initial or changed structural charactistic, such as (but not limited to):

- The type and charter of the respective entity
- The termination date of a now-closed entity
- The physical location of the entity
- The "parent" company that owns the entity

From their internal source data, the Federal Reserve publishes daily extracts at this [link](https://www.ffiec.gov/npw/FinancialReport/DataDownload)

#### Data Dictionaries

Data Dictionaries and other supporting resources are avialable on [github.com/call-report/data-resources](https://github.com/call-report/data-resources)

#### Analysis Note

Note that the Federal Reserve does not publish the full record of the `ATTRIBUTES` file on its public website; this data is only available via a Freedom of Information Act (FOIA) request. 

Without the full record, an analyst cannot track the progression of changes and updates to an organization's attribute record - the daily extracts publicly provided by the Federal Reserve only indicate the last recorded set of attributed for the respective institution.

#### Active Attributes

Lists the daily extract of the `ATTRIBUTES` record for all institutions that are going concerns (active, and in business).

#### Closed Attributes

Lists the daily extract of the `ATTRIBUTES` record for all institutions that are no longer going concerns.

#### Branches

Lists characteristics of bank branches; note that this bank branch information does not include a crosswalk to the FDIC's `UNINUM`. This lack of a crosswalk is an impediment to matching the FDIC's Summary of Deposits data with the FDIC's Branch Data

#### Transformations

Lists mergers and acquisitions of one financial institution to another, through providing the RSSD IDs of the survivor and non-acquired institution.

This list of relationships (graph edges) can be utilized to construct a graph that represents each institutions' relationship to one another.

#### Relationships

Lists each entity's relationship to another, with repspect to if an institution is owned or owns another institution.

##### Important Note when Analyzing Relationship Data

Note that institutions may not 100% own other institutions; a child subsidiary of an institution may be owned by more than one parent entity.