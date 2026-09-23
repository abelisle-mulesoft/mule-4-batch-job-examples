# Mule Project `batch-contacts-csv-to-db`

The Mule project `batch-contacts-csv-to-db` implements a batch job. It does not implement a particular use case but serves as a comprehensive example that illustrates the art of the possible. Using the SFTP Connector, it monitors a directory for a new or updated file. It expects a CSV file that contains contact data. When it finds a new or updated file, it reads the contact data and bulk inserts it into a database within a Batch Job component. Upon completing the Batch Job, it sends a summary report via Gmail.

The folder **documentation** contains:

- An [Overview](documentation/Overview.md) document, which I recommend reading first as it provides additional details on the Mule application `batch-contacts-csv-to-db` and its implementation.
- A [Getting Started](documentation/Getting-Started.md) document, which lists the prerequisites and provides details on setting up the Mule application `batch-contacts-csv-to-db` to run it.

