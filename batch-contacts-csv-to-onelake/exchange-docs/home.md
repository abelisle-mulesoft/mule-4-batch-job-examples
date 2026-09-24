# Batch Contacts CSV to OneLake

This Mule application demonstrates a batch processing implementation that reads contact data from CSV files and delivers the processed data to Microsoft OneLake.

The application uses an SFTP server for file ingestion and staging, processes records using a Mule Batch Job, handles failed records separately, and uses the Azure Data Lake Storage Connector to deliver successfully processed data to Microsoft OneLake.

For detailed implementation information and setup instructions, refer to the documentation included with the project.
