# Bank Time Series Regulatory Data

## About

### Time Series Frequency

Most all public bank regulatory data is time series data with a quarterly frequency. Some data, particularly for smaller financial institutions' data is semi-annual. 

### Publishing frequency

Regulatory agencies receive data on a rolling basis. Bulk data downloads are updated approximately monthly, while "webservice" feeds are updated soon after bank regulatory filings are submitted and validated.

### Data Fields and Data Dictionaries

Time series are published by field name (an "MDRM"), the ID of the reporting institution, and the reporting date (typically quarterly). 

The data release date is not included in the datasets themselves, but can be inferred from the data publication data.

The data dictionaries describing MDRM fields is available at: [https://www.federalreserve.gov/apps/mdrm/pdf/MDRM.zip](https://www.federalreserve.gov/apps/mdrm/pdf/MDRM.zip), and is updated daily.

## Institution Identifiers

### Overview

#### Federal Reserve and FFIEC Institution Identifiers

Federal Reserve institution identifiers are known as "RSSD" Ids. Bank regulatory data referenced on this page uses these RSSDs as the primary identifiers for financial institutions.

#### Matching RSSD Identifiers to Institution Names

TBD

## Taxonomies

"CDR Taxonomies," also known as "Call Report Taxonomies," represent the relationship of data points within bank regulatory data among each other.

### Details

As noted earlier, bank regulatory time series data points are characterized by:

- The ID of the reporting institution (RSSD)
- The time period represented by the data point
- The data series reported (MDRM)
- The release date of the data

Within these dimensions, for each reporting quarter, taxonomies are published by the FFIEC that indicate the "Schedule", "Section", "Line", and in some cases, "Column" of the data.

These hierarchical categories facilitate an analysts' understanding of the financial condition of an organization.

For example, in the FFIEC 031 report:
```
Schedule: RC-B (Report of Condition - Part B - Securities)
    Line: 1
        Column C: The Amortized Cost of Available-for Sale Treasury Securities (MDRM: RCFD1286)
        Column D: The Fair Value of Available-for-Sale Treasury Securities (MDRM: RCFD1287)

```

Current and historical forms may be downloaded from the FFIEC:
- [FFIEC 031](https://www.ffiec.gov/forms031.htm): Consolidated Reports of Condition and Income for a Bank with Domestic and Foreign Offices
- [FFIEC 041](https://www.ffiec.gov/forms041.htm): Consolidated Reports of Condition and Income for a Bank with Domestic Offices Only  
- [FFIEC 051](https://www.ffiec.gov/forms051.htm): Consolidated Reports of Condition and Income for a Bank with Domestic Offices Only and Total Assets Less than $5 Billion

Note that a data series may be shared by one or more of the above reports.

### Download Locations

While taxonomies may be reviewed from the PDFs above, the PDFs do not provide a machine data format for purposes of programmatic data analysis.

Machine-data versionf of the taxonomies may be downloaded from [https://cdr.ffiec.gov/public/DownloadTaxonomy.aspx](https://cdr.ffiec.gov/public/DownloadTaxonomy.aspx)

Taxonomies are provided in XBRL format, which typically requires commercial software for processing. In lieu of this commercial software, a Python-based tool for converting CDR taxonomies to JSON format is available [here](https://github.com/call-report/public-python-scripts/cdr-taxonomy-processor).


## Sources

### Time Series 2001 - present

#### Bulk Data Downloads

- Historical data is provided from 2001 until the present day by the Federal Financial Institutions Examination Council (FFIEC).

- Bulk data downloads are generated from the rolling filings on monthly basis, typically released mid-month. 
  
- Data is provided in XBRL and CSV format.

- The permanent lnk to download bulk regulatory data is available at [https://cdr.ffiec.gov/public/PWS/DownloadBulkData.aspx](https://cdr.ffiec.gov/public/PWS/DownloadBulkData.aspx)

### Webservice Access

TBD

### Timeseries 1978 - 2010

- Historical bank regulatory data is provided by the Federal Reserve Bank of Chicago (the "Chicago" dataset) at two links: 
  - 1976-2000: [https://www.chicagofed.org/banking/financial-institution-reports/commercial-bank-data-complete-1976-2000](https://www.chicagofed.org/banking/financial-institution-reports/commercial-bank-data-complete-1976-2000)

  - 2000-2010: [https://www.chicagofed.org/banking/financial-institution-reports/commercial-bank-data-complete-2001-2010](https://www.chicagofed.org/banking/financial-institution-reports/commercial-bank-data-complete-2001-2010)


- Note that the "Chicago" dataset overlaps with the FFIEC dataset; if combining the two datasets, for overlapping data points, to utilize the FFIEC dataset in lieu of the Chicago dataset.
- Data is provided in SAS XPORT format. (Python import script is TBD.)