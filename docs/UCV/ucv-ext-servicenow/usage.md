
# ServiceNow - Usage

To use the ServiceNow plugin, the plugin must be loaded and an instance created before you can configure the plugin integration and use plugin automation tasks. You define configuration properties in the user interface or in a JSON file.

See the **Automation Tasks** tab for information on using automation tasks.

## Integration type

The ServiceNow plug-in supports scheduled events integration which are listed in the following table.

| Name | Description |
| --- | --- |
| syncIncidentData | Queries the ServiceNow repository for Incidents |
| syncChangeData | Queries the ServiceNow repository for Change request |
| syncProblemData | Queries the ServiceNow repository for Problems |
| ServiceNowWaitChangeTask | Checking all release Event task waiting field status |
| ServiceNowWaitRequests | Checking all release Event task waiting field status |

## Integration

There are two methods to integrate the plugin:

* Using the user interface
* Using a JSON file

### Using the user interface

The tables in the Configuration properties topic describe the properties used to define the integration.

To install the plug-in, perform the following steps:

1. In **Velocity**, click **Settings** > **Integrations** > **Available**
2. In the **Action** column for the ServiceNow plug-in, click **Install**.

To integrate the plug-in, perform the following steps:

1. In **Velocity**, click **Settings** > **Integrations** > **Installed**.
2. In the **Action** column for the ServiceNow plug-in, click **Add Integration**.
3. On the Add Integration page enter values for the fields used to configure the integration and define communication.
4. Click **Add**.

### Using a JSON file

The JSON file contains the information for creating a value stream and integrating with the ServiceNow server. The following table describes the information for the creating a DevOps Velocity value stream map.

1. From a value stream page, download the value stream map. The value stream map is a JSON file used to define integrations.
2. Edit the JSON file to include the plugin configuration properties.
3. Save and upload the JSON file. This replaces the current JSON file with the new content.
4. View the new integration on the Integrations page.

## OAuth

OAuth 2.0 Authentication: 

    Implemented OAuth 2.0 authentication for secure communication with third-party services.

* OAuth 2.0 client credentials flow added for ServiceNow API integration. 
* Refresh token mechanism introduced for automatic token renewal when the access token expires.

### How to integrate using OAuth
To integrate OAuth 2.0, follow these steps:

Provide the required credentials:

* Client ID
* Client Secret
* Username
* Password

### How to Retrieve Client ID and Client Secret in ServiceNow
Navigate to OAuth Settings:

* In your ServiceNow instance, click on All in the navigation pane.
* Go to System OAuth and select Application Registry.
* Retrieve Client ID and Generate Client Secret:

Select the application you registered.
* The Client ID will be displayed on this page.
* The Client Secret will be generated when you submit the registration.

Use for Integration:
* After creating the application, click on it to view the Client Secret. Use both the Client ID and Client Secret when integrating ServiceNow with OAuth 2.0.

Confirmation:
* Once integrated successfully, you will see a log message confirming that OAuth 2.0 is being used:
"Authentication via OAuth2.0: Using client credentials to obtain access token."

## Automation Tasks

The following automation tasks are available in the ServiceNow plugin:

* ServiceNow – Create Change Request and Change Task
* ServiceNow – Update Change Request and Change Task
* ServiceNow – Wait Change Request
* ServiceNow – Wait Change Task

### ServiceNow – Create Change Request and Change Task
Use this step to create a ServiceNow change request and change task.

| Name | Description | Required |
| --- | --- | --- |
| Short Description | A short description of the ServiceNow change request.| Yes |
| Request type | The type of request type for the ServiceNow application. For example: Standard, Normal, and Emergency.| Yes |
| Assignment group | The assignment group for the ServiceNow application. | Yes |
| Additional properties | A list of additional properties for the change request in the format for each list item is {“property”:”value”}. For example: {“short_description”:”Created by DevOps Velocity”}. Separate each list item with a comma (,). See the ServiceNow API documentation for additional properties. | No |
| Create change task | To create change task , provide necessary properties.
Example:[{“short_description”:”createtask”,”change_task_type”:”planning”,”description”:”changetask”,”start_date”:”2024-01-30 08:05:04″,”end_date”:”2024-01-31 08:05:13″,”outputProperty”:”example”}]. Here outputProperty holds sys_id of change task created.
To create multiple change task provide comma separated objects.
Example: [{},{},{}].
To create under existing change request mention “parent”:”CHG0030008″,”change_request”:”CHG0030008″ along with other properties. | No |
| Output property | The name of the property that the sys_id of the created change request is saved. | No |

### ServiceNow – Update Change Request and Change Task
Use this step to update a ServiceNow change request in DevOps Velocity.

| Name | Description | Required |
| --- | --- | --- |
| Change Request Number | Enter the change request number.
Note: Either change request number or property reference must be provided | No |
| Change request system id from property reference.	Enter the property reference to system id.
Note: Either change request number or property reference must be provided | No |
| Change request properties | Enter properties for the change request to be updated in the format for each list item is {“property”:”value”}. For example: {“short_description”:”change request description”,”planned_end_date”:”2024-01-31 07:52:53″,”planned_start_date”:”2024-01-30 07:52:47″}. Separate each list item with a comma (,). See the ServiceNow API documentation for additional properties. | No |
| Update change task | To update change task , provide necessary properties.
to create change task
Example:[{“sys_id”:”abcd123″,”change_task_type”:”planning”,”state”:”1″}].
property reference can be given to sys_id
Example:[{“sys_id”:”${example}”,”change_task_type”:”planning”,”state”:”1″}]
to update change task
Example:[{“short_description”:”createtask”,”change_task_type”:”planning”,”description”:”changetask”,”start_date”:”2024-01-30 08:05:04″,”end_date”:”2024-01-31 08:05:13″,”outputProperty”:”example”}]
To update multiple change task provide comma separated objects. Example: [{},{},{}] | No |

### ServiceNow – Wait Change Request
Use this task to wait ServiceNow change request in DevOps Velocity.

| Name | Description | Required |
| --- | --- | --- |
| Change Request Number | Enter the change request number.
Note: Either change request number or property reference must be provided | No |
| Change request system id from property reference. | Enter the property reference to system id.
Note: Either change request number or property reference must be provided | No |
| Field | The change request field to wait for a match. | Yes |
| Value | The value to match with the change request field. | Yes |

### ServiceNow – Wait Change Task
Use this step to create a ServiceNow wait change task.

| Name | Description | Required |
| --- | --- | --- |
| Change task system id from property reference.| Enter the property reference to system id.| Yes |
| Change Request Number | Enter the change request number.
Note: Either change request number or property reference must be provided | No |
| Change request system id from property reference.| Enter the property reference to system id.
Note: Either change request number or property reference must be provided | No |
| field	| Enter the change task field to wait for a match | Yes |
| Value	| Enter the value to match the change task field | Yes |

## Adding automation tasks to a release
After the plugin is integrated automated tasks are available to add as a task within a release.

* Verify that the ServiceNow server is connected to DevOps Velocity.
* On the Create Task page, select the automation task from the Type field drop-down list.
* Complete the properties required for the task.
* Click Save.
## Configuration Properties

The following tables describe the properties used to configure the integration. Each table contains the field name when using the user interface and the property name when using a JSON file.

* The General Configuration Properties table describes configuration properties used by all plugin integrations.
* The ServiceNow Configuration Properties table describes the ServiceNow configuration properties that define the connection and communications with the ServiceNow server. When using the JSON method to integrate the plugin these properties are coded within the properties configuration property.

Some properties might not be displayed in the user interface, to see all properties enable the **Show Hidden Properties** field.

### General Configuration Properties

| Name | Description | Required | Property Name |
| --- | --- | --- | --- |
| NA | The version of the plugin that you want to use. To view available versions, click the Version History tab. If a value is not specified, the latest version is used. | No | image |
| Integration Name | An assigned name to the value stream. | Yes | name |
| Logging Level | The level of Log4j messages to display in the log file. Valid values are: all, debug, info, warn, error, fatal, off, and trace. | No | loggingLevel |
| NA | List of configuration properties used to connect and communicate with ServiceNow server. Enclose the properties within braces. | Yes | properties |
|  | The name of the tenant. | Yes | tenant_id |
| NA | Unique identifier assigned to the plugin. The value for the ServiceNow Server plugin is ucv-ext-servicenow | Yes | type |
| DevOps Velocity User Access Key | An auto-generated user access key provides credentials for communicating with the **Velocity** server. | Yes | NA |

### ServiceNow Configuration Properties

| Name | Type | Description | Required | Project Name |
| --- | --- | --- | --- | --- |
| Access Token | Secure | The access token used to authenticate with the ServiceNow server. You can use either this property or the Password property to authenticate with the server. | No | accessToken |
| Password | Secure | The password used to authenticate with the ServiceNow server. You can use either this property or the Access Token property to authenticate with the server. | No | password |
| URL | String | The URL of the ServiceNow server. | Yes | baseUrl |
| User Name | String | The user name used to authenticate with the ServiceNow server. | Yes | username |
| Proxy Server | String | The URL of the proxy server including the port number. | No | proxyServer |
| Proxy User Name | String | The user name used to authenticate with the proxy server. | No | proxyUsername |
| Proxy Password | String | The password used to authenticate with the proxy server. | No | proxyPassword |
| Page Size | String | The number of issues retrieved per page. | No | pageSize |

## Example

The following example can be used as as template to include the ServiceNow plug-in integration into the JSON file. Copy and paste the template into the JSON file and make the appropriate changes.

```
integrations": [
{
"type": "ucv-ext-servicenow",
"name": "Plug-in
for ServiceNow",
"tenant_id": "*tenant\_id*",
"logginglevel": "info",
"properties": {

"ucvAccessKey": "*DevOpsvelocity\_user\_accesskey*",
"baseUrl": "*url\_servicenow\_server*",

"username": "*user\_name*",
"password": "*pass\_word*",
"proxyServer": "*proxy\_server\_url*",

"proxyUsername": "*proxy\_server\_user\_name*",
"proxyPassword": "*proxy\_server\_password*"

}``
}``
]

```

## Example using access key.

```
integrations": [
{
"type": "ucv-ext-
servicenow",
"name": "Plug-in for ServiceNow",
"tenant_id": "*tenant\_id*",
"logginglevel": "info",

"properties": {
"ucvAccessKey": "*DevOpsvelocity\_user\_accesskey*",
"baseUrl":
"*url\_servicenow\_server*",
"username": "*user\_name*",
"accessToken": "*access\_token*",

"proxyServer": "*proxy\_server\_url*",
"proxyUsername": "*proxy\_server\_user\_name*",

"proxyPassword": "*proxy\_server\_password*"
}``
}``
]

```


|Back to ...||Latest Version|ServiceNow |||
| :---: | :---: | :---: | :---: | :---: | :---: |

|[All Plugins](../../index.md)|[Velocity Plugins](../README.md)|[1.1.8-File 1 ](https://raw.githubusercontent.com/UrbanCode/IBM-UCV-PLUGINS/main/files/ucv-ext-servicenow/ucv-ext-servicenow%3A1.1.8.tar.7z.001)[and 1.1.8-File 2](https://raw.githubusercontent.com/UrbanCode/IBM-UCV-PLUGINS/main/files/ucv-ext-servicenow/ucv-ext-servicenow%3A1.1.8.tar.7z.002)|[Readme](README.md)|[Overview](overview.md)|[Downloads](downloads.md)|
|[All Plugins](../../index.md)|[Velocity Plugins](../README.md)|[1.1.6-File 1 ](https://raw.githubusercontent.com/UrbanCode/IBM-UCV-PLUGINS/main/files/ucv-ext-servicenow/ucv-ext-servicenow%3A1.1.6.tar.7z.001)[and 1.1.6-File 2](https://raw.githubusercontent.com/UrbanCode/IBM-UCV-PLUGINS/main/files/ucv-ext-servicenow/ucv-ext-servicenow%3A1.1.6.tar.7z.002)|[Readme](README.md)|[Overview](overview.md)|[Downloads](downloads.md)|