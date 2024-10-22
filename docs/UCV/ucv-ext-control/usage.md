
# Control - Usage

To use the Control plug-in, the plug-in must be loaded and an instance created before you can configure the plug-in integration. Configuration properties are defined using the product user interface or a JSON file.

## Integration type

The Control plug-in supports scheduled events integration which are listed in the following table.

| Name | Description |
| --- | --- |
| syncControlPullRequestsEvent | Queries the Control repository for pull requests. |
| syncControlCommitsEvent | Queries the Control repository for commits. |

## Integration

There are two methods to integrate the plug-in:

* Using the user interface
* Using a JSON file

The tables in the Configuration properties topic describe the properties used to define the integration.

### Using the user interface

1. From the Plugins page, click **Settings** > **Integrations** > **Plugins**.
2. Under the **Action** column for the plug-in, click **Add Integration**.
3. On the Add Integration page enter values for the fields used to configure the integration and define communication.
4. Click **Save**.

### Using a JSON file

The JSON file contains the information for creating a value stream. Within the JSON file is a section for integrations. It is in this section that plug-in properties can be defined.

1. From a value stream page, download the value stream map. The value stream map is a JSON file used to define integrations.
2. Edit the JSON file to include the plug-in configuration properties.
3. Save and upload the JSON file. This replaces the current JSON file with the new content.
4. View the new integration on the Integrations page.

## Configuration properties

The following tables describe the properties used to configure the integration. Each table contains the field name when using the user interface and the property name when using a JSON file.

* The General Configuration Properties table describes configuration properties used by all plug-in integrations.
* The Control Configuration Properties table describes the Control configuration properties that define the connection and communications with the Control server. When using the JSON method to integrate the plug-in these properties are coded within the `properties` configuration property.

### General Configuration Properties table

| Name | Description | Required | Property Name |
| --- | --- | ---| --- |
| NA | The version of the plug-in that you want to use. To view available versions, click the **Version History** tab. If a value is not specified, the latest version is used. | No | image |
| Integration Name | An assigned name to the value stream. | Yes | name |
| Logging Level | The level of Log4j messages to display in the log file. Valid values are: all, debug, info, warn, error, fatal, off, and trace. | No | loggingLevel |
| NA | List of configuration properties used to connect and communicate with the Control server. Enclose the properties within braces. | Yes | properties |
|  | The name of the tenant. | Yes | tenant_id |
| NA | Unique identifier assigned to the plug-in. The value for the Control plug-in is `ucv-ext-control` | Yes | type |

### Control Configuration Properties table

| Name | Type | Description | Required | Project Name |
| --- | --- | --- | --- | --- |
| API URL | String | The URL to the REST API for the Control instance. | Yes | apiUrl |
| DevOps Velocity User Access Key | String | The user access key generated from DevOps Velocity used to authenticate with the DevOps Velocity server. | Yes | ucvAccessKey |
| Owner | String | The owner name of the Control repository. | Yes | owner |
| Repositories | Array | List of Control repositories. | Yes | repositories |
| Branch | String | Control repositories branch, The branch to pull commits from. | No | branch |
| Personal access token | String | The Personal Access Token used to authenticate with Control repositories. | Yes | token |
| Additional branches | Array | Additional branches to collect commits from besides the main one, leave blank if not needed. | No | otherBranches |
| Proxy Server | String | The URL of the proxy server including the port number. | No | proxyServer |
| Proxy User Name | String | The user name used to authenticate with the proxy server. | No | proxyUsername |
| Proxy Password | String | The password used to authenticate with the proxy server. | No | proxyPassword |

### JSON code example

The following example can be used as a template to define the integration within the JSON file for a value stream. Copy and paste the template into the JSON file and make the appropriate changes.

```json

"integrations":[ {
    "type":"ucv-ext-control",
    "tenant_id":"tenant-id",
    "name":"control-integration-name",
    "properties":{
        "owner":"owner-name",
        "repositories":[ 
            "repo1",
            "repo2",
            "repo3"
        ],
        "apiUrl":"control-api-url",
        "token":"generated-token",
        "ucvAccessKey":"generated-access-key",
        "proxyServer": "*proxy_server_url*",
        "proxyUsername": "*proxy_server_user_name*",
        "proxyPassword": "*proxy_server_password*"
    }
} ]

```

|Back to ...||Latest Version|Control |||
| :---: | :---: | :---: | :---: | :---: | :---: |
|[All Plugins](../../index.md)|[Velocity Plugins](../README.md)|[1.0.2-File 1 ](https://raw.githubusercontent.com/UrbanCode/IBM-UCV-PLUGINS/main/files/ucv-ext-control/ucv-ext-control%3A1.0.2.tar.7z.001)[and 1.0.2-File 2](https://raw.githubusercontent.com/UrbanCode/IBM-UCV-PLUGINS/main/files/ucv-ext-control/ucv-ext-control%3A1.0.2.tar.7z.002)|[Readme](README.md)|[Overview](overview.md)|[Downloads](downloads.md)|
