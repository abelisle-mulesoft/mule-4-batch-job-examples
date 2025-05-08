# Mule Project `batch-contacts-csv-to-db`

The Mule project `batch-contacts-csv-to-db` implements a batch job. It does not implement a particular use case but serves as a comprehensive example that illustrates the art of the possible. Using the SFTP Connector, it monitors a directory for a new or updated file. It expects a CSV file that contains contact data. When it finds a new or updated file, it reads the contact data and bulk inserts it into a database within a Batch Job component. Upon completing the Batch Job, it sends a summary report via Gmail.

Please refer to the [Overview document](/documentation/Overview.md) for more information and an overview of its implementation.
