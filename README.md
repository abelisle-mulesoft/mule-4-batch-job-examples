# Mule 4 Batch Job Examples

This repository contains examples that demonstrate how to implement batch processing in Mule 4.

The examples provide a progression from a foundational batch processing implementation to a more advanced integration:

- `batch-contacts-csv-to-db` provides a foundational example that processes contact data from CSV files and persists the records to a PostgreSQL database. The implementation focuses on core Mule batch processing concepts while intentionally limiting integration complexity.
- `batch-contacts-csv-to-onelake` provides a more advanced example that processes the same contact data and delivers the results to Microsoft OneLake. The implementation demonstrates additional integration patterns for large-file processing, staging, failed-record handling, Microsoft Entra ID authentication, and OneLake delivery.

Both examples use the same fictitious contact datasets, allowing the implementations to be compared using a common input data model.

## Repository Content

- **[batch-contacts-csv-to-db](batch-contacts-csv-to-db/)** — Foundational Mule Batch example using PostgreSQL as the target system.
- **[batch-contacts-csv-to-onelake](batch-contacts-csv-to-onelake/)** — Advanced Mule Batch example using Microsoft OneLake as the target system.
- **[sample-data](sample-data/)** — Shared fictitious contact datasets used by both examples.

## Technology Stack

The examples were implemented and tested using:

### Common

- MuleSoft Anypoint Studio 7.26
- Mule runtime 4.12.0

### Batch CSV to Database

- PostgreSQL 11.9
- PostgreSQL JDBC Driver 42.7.5

### Batch CSV to OneLake

- Microsoft Fabric OneLake
- Microsoft Entra ID
- MuleSoft Azure Data Lake Storage Connector

---

Copyright © 2026 Alan Belisle. Licensed under the [Apache License 2.0](LICENSE).
