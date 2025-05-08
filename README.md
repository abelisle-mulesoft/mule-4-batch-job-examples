# Mule 4 Batch Job Examples

As of this writing, this repository contains a single Batch Job example, the Contacts CSV File to Database example. I created this Mule application to explain and demonstrate how to implement a batch job in Mule 4. My goal was not to implement it to address a specific use case but to serve as a comprehensive example that illustrates the art of the possible. There are many examples across the web and in blog posts. Nevertheless, I am sharing this example as it is more comprehensive than most, if not all.  

> [!NOTE]
> I plan to add another example soon.

## Repository Content

- The folder **anypoint-studio-projects/batch-contacts-csv-to-db** includes the source code of the Mule application `batch-contacts-csv-to-db`. 
- The folder **documentation** contains an [Overview](documentation/Overview.md) document, which provides additional details on the Mule application `batch-contacts-csv-to-db` and its implementation.
- The folder **resources** includes miscellaneous resources for setting up the environment - e.g., sample contact data, script for setting up the database. This folder contains a [README](resources/_README.md) file that provides additional details.

## Technology Stack Overview

The assets and resources in this repository were implemented and tested using the following technology stack:

- MuleSoft Anypoint Studio 7.18
- Mule runtime 4.7.0
- PostgreSQL 11.9
- PostgreSQL JDBC Driver 42.7.5

Although not formally tested, you could easily use older or newer versions.
