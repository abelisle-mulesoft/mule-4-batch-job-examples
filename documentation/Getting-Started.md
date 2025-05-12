# Getting Started with Mule Project `batch-contacts-csv-to-db`

## Prerequisites

As discussed in the [Overview](Overview.md) document, the Mule project `batch-contacts-csv-to-db` monitors a directory for a new or updated file on an SFTP server. When it finds a new or updated file, it reads the contact data and bulk inserts it into a database table. Upon completing the Batch Job, it sends a summary report via Gmail. To run the Mule project `batch-contacts-csv-to-db` without changing those resources, you will need the following information before setting it up:

1. SFTP Server Configuration:
   - Hostname or IP address.
   - Port number.
   - Username.
   - Password.
   - Working directory, which is the default path on the SFTP server where we typically create the following subdirectories: 
     - `new`, which is the subdirectory that the Mule application `batch-contacts-csv-to-db` monitors for new and updated files using the SFTP Connector.
     - `processed`, which is the subdirectory where the Mule application `batch-contacts-csv-to-db` moves files once they are processed. It also writes errors that occurred in the Batch Job to another file in this subdirectory. 
     - `failed`, which is the subdirectory where the error handler within the Mule application `batch-contacts-csv-to-db` moves files if an error or failure occurs.
2. Database Configuration:
   - Hostname or IP address.
   - Port number.
   - Username.
   - Password.
   - Database name.
   - Additionally, if not using a PostgreSQL database:
      - Database vendor or type - e.g., Oracle, MS SQL Server, PostgreSQL.
      - JDBC driver.
      - JDBC URL.
      - JDBC driver class name.
      - Database instance or service name. 

3. Gmail Configuration:
   - Gmail username.
   - Gmail app password - see note below.
   - Gmail email address, which is used to indicate the sender - e.g. Max Mule <max.mule@gmail.com>.
   - Email main recipient (i.e., TO field) - Warning: as currently configured, the Mule application `batch-contacts-csv-to-db` only supports a single main recipient. You could update it to support multiple recipients, though.

> [!NOTE]
> As discussed in the article [Connect to Gmail with Email Connector Examples - Mule 4](https://docs.mulesoft.com/email-connector/latest/email-gmail), you must [configure an app password](https://support.google.com/accounts/answer/185833) in your Gmail account to send emails to a Gmail account via Mule 4 Email Connector.

## Getting Started

1. Download or clone this repo, and import the project **anypoint-studio-projects/batch-contacts-csv-to-db** into your Anypoint Studio workspace.
    ```sh
    git clone https://github.com/abelisle-mulesoft/mule-4-batch-job-examples.git
    ```

2. Asuming you are working in the `dev` environment, copy the properties template `src/main/resources/properties/mule-props.template.yaml`  to `src/main/resources/properties/mule-props-dev.yaml`. 

3. Edit the properties file `src/main/resources/properties/mule-props-dev.yaml` 
    - At a minimum, configure the following properties to match your environment:
        - `env.name` - the name of the environment (e.g., dev).
        - **SFTP Connector Configuration**:
          - `sftp.host` - SFTP server hostname or IP address.
          - `sftp.port` - SFTP server port number (e.g., 21).
          - `sftp.username` - SFTP server username.
          - `sftp.password` - SFTP server password.
          - `sftp.working_dir` - The base path on the SFTP server that contains the `new`, `failed`, and `processed` subdirectories.
        - **Database Connector Configuration**:
          - `postgres_db.host` - Database hostname or IP address.
          - `postgres_db.port` - Database port number (e.g., 5432).
          - `postgres_db.username` - Database username.
          - `postgres_db.password` - Database password.
          - `postgres_db.db_name` - Database name (e.g., postgres).
        - **Email Connector Configuration**:
          - `gmail.server.username` - Gmail username
          - `gmail.server.password` - Gmail app password
          - `gmail.address.from` - Email address to use as the sender, which must match the Gmail address. 
          - `gmail.address.to` - Recipient's email address.
    - Optionally, update the following properties to meet your requirements:
       - **Batch Job Components Configuration**.
          - `batch.job.block_size` - Number of records to include in each block when splitting the source data for processing.
          - `batch.aggregator.main.size` - Size of each array of records the main aggregator processes.
        - **SFTP Connector Configuration**:
          - `sftp.new_dir` - The subdirectory within the `sftp.working_dir` monitored for new and updated files (e.g., `new`).
          - `sftp.failed_dir` - The subdirectory within the `sftp.working_dir` where processed files are moved (e.g., `failed`).
          - `sftp.processed_dir` - The subdirectory within the `sftp.working_dir` where the error handler moves files if an error or failure occurs (e.g., `processed`).

4. Compile and run the project in Anypoint Studio as a smoke test. 
    - Optionally, upload the sample file [Contact_Data_100.csv](../resources/Contact_Data_100.csv) to your SFTP server within the `new` subdirectory to test and validate your configuration. As a reminder, the Mule application `batch-contacts-csv-to-db` sends a summary report via Gmail upon completion of the batch job. In other words, your configuration and settings are valid if you receive the summary email report.
