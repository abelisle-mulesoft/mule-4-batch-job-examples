# Mule 4 Batch Job Examples

This repository contains examples that demonstrate how to implement batch processing in Mule 4.

- The `batch-contacts-csv-to-db` project offers a foundational example that processes contact data from CSV files and stores the records in a PostgreSQL database. This implementation emphasizes core Mule batch processing concepts and deliberately limits integration complexity.
- The `batch-contacts-csv-to-onelake` project presents a more advanced example that processes data from CSV files and delivers the results to Microsoft OneLake. This implementation demonstrates additional integration patterns, including large-file processing, staging, failed-record handling, Microsoft Entra ID authentication, and delivery to OneLake.

Both examples use the same fictitious contact datasets for demonstration and testing purposes.

## Repository Content

- **[batch-contacts-csv-to-db](batch-contacts-csv-to-db/)** — Foundational Mule Batch example using PostgreSQL as the target system.
- **[batch-contacts-csv-to-onelake](batch-contacts-csv-to-onelake/)** — Advanced Mule Batch example using Microsoft OneLake as the target system.
- **[sample-data](sample-data/)** — Fictitious contact datasets used for demonstration and testing.

## Documentation

The [Known Issues](known-issues.md) document describes known Mule runtime or tooling issues that affect the examples in this repository.

Each project includes supporting documentation to help understand, configure, and run the examples.

- [batch-contacts-csv-to-db/documentation](batch-contacts-csv-to-db/documentation/):
  - [Overview](batch-contacts-csv-to-db/documentation/overview.md) — Architecture, design considerations, and implementation details.
  - [Getting Started](batch-contacts-csv-to-db/documentation/getting-started.md) — Configuration and instructions for running the example.

- [batch-contacts-csv-to-onelake/documentation](batch-contacts-csv-to-onelake/documentation/):
  - [Overview](batch-contacts-csv-to-onelake/documentation/overview.md) — Architecture, design considerations, and implementation details.
  - [Getting Started](batch-contacts-csv-to-onelake/documentation/getting-started.md) — Configuration and instructions for running the example.
  - [Configure Microsoft Fabric](batch-contacts-csv-to-onelake/documentation/configure-microsoft-fabric.md) — Microsoft Entra ID and Fabric configuration required by the example.

## Technology Stack

The examples were implemented and tested using the following technology stack:

- Common
  - MuleSoft Anypoint Studio 7.26
  - Mule runtime 4.12.0

- Batch CSV to Database
  - PostgreSQL 11.9
  - PostgreSQL JDBC Driver 42.7.5

- Batch CSV to OneLake
  - Microsoft Fabric OneLake
  - Microsoft Entra ID
  - MuleSoft Azure Data Lake Storage Connector 1.0.11

---

Copyright © 2026 Alan Belisle. Licensed under the [Apache License 2.0](LICENSE).
