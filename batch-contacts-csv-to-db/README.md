# Mule Project `batch-contacts-csv-to-db`

The Mule project `batch-contacts-csv-to-db` demonstrates a batch job implementation. Rather than addressing a specific use case, it serves as a comprehensive example to showcase potential capabilities. The project utilizes the SFTP Connector to monitor a directory for new or updated files, specifically expecting CSV files containing contact data. When it detects such a file, the system reads the contact data and performs a bulk insert into a database using a Batch Job component. After the Batch Job completes, it sends a summary report via Gmail.

## Documentation

The **documentation** folder contains:

- An [Overview](documentation/Overview.md) document, which provides additional details on the Mule application `batch-contacts-csv-to-db` and its implementation and is recommended as the starting point.
- A [Getting Started](documentation/Getting-Started.md) document, which lists the prerequisites and provides details on setting up and running the Mule application `batch-contacts-csv-to-db`.

## Resources

The **resources** folder contains supporting files for setting up and running the Mule application, including sample contact data and the SQL script used to create the PostgreSQL contacts table. See the [resources README](resources/README.md) for additional details.

---

Copyright © 2026 Alan Belisle. Licensed under the [Apache License 2.0](/LICENSE).
