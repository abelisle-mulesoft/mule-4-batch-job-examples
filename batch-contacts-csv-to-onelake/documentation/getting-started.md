# Getting Started with Mule Project `batch-contacts-csv-to-onelake`

## Prerequisites

As described in the [Overview document](overview.md), the Mule project `batch-contacts-csv-to-onelake` monitors a directory on an SFTP server for new or updated CSV files. When a file is detected, the application processes the records and delivers the successfully processed output to Microsoft OneLake.

Running the Mule project with the existing implementation requires the following configuration information:

1. **SFTP Server Configuration**:

   - Hostname or IP address.
   - Port number.
   - Username.
   - Password.
   - Working directory containing the following subdirectories:
     - `archive` — Contains archived source and staged files, as well as error files generated for records that fail during the Batch Job.
     - `failed` — Contains files moved by the error handler when an error or failure occurs outside the Batch Job.
     - `new` — Monitored by the Mule application for new or updated files using the SFTP Connector.
     - `staged` — Contains temporary processed files staged on the SFTP server before delivery to OneLake.

2. **Microsoft Fabric Configuration**:

   - Microsoft Entra ID service principal:
     - Tenant ID.
     - Client ID.
     - Client secret.
   - Microsoft OneLake:
     - Workspace name.
     - Lakehouse name.

3. **Secure Properties Encryption Key**:

   - Encryption key.

## Getting Started

1. Clone the repository and import the project `batch-contacts-csv-to-onelake` into Anypoint Studio.

   ```sh
   git clone https://github.com/abelisle-mulesoft/mule-4-batch-job-examples.git
   ```

2. Create the application and secure properties files for the target environment from the provided templates. For example, for an environment named `dev`:

   - Copy `src/main/resources/properties/app-props.template.yaml` to `src/main/resources/properties/app-props-dev.yaml`.
   - Copy `src/main/resources/properties/secure-props.template.yaml` to `src/main/resources/properties/secure-props-dev.yaml`.

3. Edit the application properties file `src/main/resources/properties/app-props-dev.yaml`.

   At a minimum, configure the following properties for the target environment:

   - **SFTP Connector Configuration**:
     - `sftp.host` — SFTP server hostname or IP address.
     - `sftp.port` — SFTP server port number.
     - `sftp.username` — SFTP server username.
     - `sftp.working_dir` — Base path on the SFTP server containing the `archive`, `failed`, `new`, and `staged` subdirectories.

   - **Azure Data Lake Storage Connector Configuration**:
     - `onelake.workspace` — Name of the OneLake workspace.
     - `onelake.lakehouse` — Name of the OneLake lakehouse.

   The following properties can optionally be adjusted for the target environment or processing requirements:

   - **Batch Job Components Configuration**:
     - `batch.job.block_size` — Number of records included in each block when splitting the source data for processing.

   - **SFTP Connector Configuration**:
     - `sftp.archive_dir` — Subdirectory within `sftp.working_dir` where the application archives the source and staged files, as well as error files generated for records that fail during the Batch Job, for example, `archive/`.
     - `sftp.failed_dir` — Subdirectory within `sftp.working_dir` where the error handler moves files when an error or failure occurs, for example, `failed/`.
     - `sftp.new_dir` — Subdirectory within `sftp.working_dir` monitored for new or updated files, for example, `new/`.
     - `sftp.staged_dir` — Subdirectory within `sftp.working_dir` where temporary processed files are staged on the SFTP server before delivery to OneLake, for example, `staged/`.

   - **Azure Data Lake Storage Connector Configuration**:
     - `onelake.base_path` — Base path where files are uploaded in OneLake.

4. Edit the secure properties file `src/main/resources/properties/secure-props-dev.yaml`.

   First, encrypt the credentials and other sensitive information for the target environment using the [MuleSoft Secure Properties Tool](https://docs.mulesoft.com/mule-runtime/latest/secure-configuration-properties#secure_props_tool). The project’s `Secure Properties Configuration` uses the following encryption settings:

   - **Tool:** secure-properties-tool-j17.jar
   - **Algorithm:** AES
   - **Mode:** CBC
   - **Use random IVs:** No/Disabled

   > [!WARNING]
   > The encryption settings must match the `Secure Properties Config` element defined in `global.xml`. Changes to these settings require corresponding changes to that configuration.

   Add the encrypted values to the corresponding properties in `secure-props-dev.yaml`:

   - **SFTP Connector Configuration**:
     - `sftp.password` — SFTP server password.

   - **Azure Data Lake Storage Connector Configuration**:
     - `azure.client_id` — Microsoft Entra ID service principal client ID.
     - `azure.client_secret` — Microsoft Entra ID service principal client secret.
     - `azure.tenant_id` — Microsoft Entra ID tenant ID.

   The same encryption key used to encrypt these values must be provided to the Mule application at runtime using the `SECURE_PROPERTIES_KEY` property.

   > [!WARNING]
   > The encryption key must not be stored in the repository or in the application's properties files.

5. Compile and run the project in Anypoint Studio as a smoke test.

   The sample file [contact-data-100.csv](../../sample-data/contact-data-100.csv) can optionally be uploaded to the `new` subdirectory on the SFTP server to validate the configuration. Successful processing can be confirmed by verifying that the processed CSV file is delivered to the configured OneLake location and that the corresponding source and staged files are archived on the SFTP server.

---

Copyright © 2026 Alan Belisle. Licensed under the [Apache License 2.0](/LICENSE).
