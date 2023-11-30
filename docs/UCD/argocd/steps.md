
# Argo CD - Process Steps

* [App Create](#app-create)
* [App Get](#app-get)
* [App Get](#app-rollback)
* [App Get](#app-set)
* [App Get](#app-sync)
* [Login](#login)


### App Create

Create an Argo CD application.


| Name | Type | Description                                                                                                          | Required |
| ---- | ---- | -------------------------------------------------------------------------------------------------------------------- | -------- |
| Argo CD Application Name | String | The name of the Argo CD application to create. | Yes |
| Additional application create flags | String | A list of flags to set when running the application create step.  For example: '--config=path'. Specify each flag on a new line.  If the flag takes an argument, put the argument on a separate line or use an equal '=' (not whitespace) between the flag and argument. | Yes |

### App Get

Get information about an Argo CD application.


| Name | Type | Description                                                                                                          | Required |
| ---- | ---- | -------------------------------------------------------------------------------------------------------------------- | -------- |
| Argo CD Application Name | String | The name of the Argo CD application to get information on. | Yes |
| Additional application get flags | String | A list of flags to set when running the application get step.  For example: '--config=path'. Specify each flag on a new line.  If the flag takes an argument, put the argument on a separate line or use an equal '=' (not whitespace) between the flag and argument. | Yes |


### App Rollback

Rollback an Argo CD application to a previous deployed version.


| Name | Type | Description                                                                                                          | Required |
| ---- | ---- | -------------------------------------------------------------------------------------------------------------------- | -------- |
| Argo CD Application Name | String | The name of the Argo CD application to rollback. | Yes |
| Argo CD Application History ID | String | The Argo CD application history ID to rollback to. | Yes |
| Additional application rollback flags | String | A list of flags to set when running the application rollback step.  For example: '--config=path'. Specify each flag on a new line.  If the flag takes an argument, put the argument on a separate line or use an equal '=' (not whitespace) between the flag and argument. | Yes |

### App Set

Set Argo CD application parameters.


| Name | Type | Description                                                                                                          | Required |
| ---- | ---- | -------------------------------------------------------------------------------------------------------------------- | -------- |
| Argo CD Application Name | String | The name of the Argo CD application to modify. | Yes |
| Additional application set flags | String | A list of flags to set when running the application set step.  For example: '--config=path'. Specify each flag on a new line.  If the flag takes an argument, put the argument on a separate line or use an equal '=' (not whitespace) between the flag and argument. | Yes |

### App Create

Sync an Argo CD application.


| Name | Type | Description                                                                                                          | Required |
| ---- | ---- | -------------------------------------------------------------------------------------------------------------------- | -------- |
| Argo CD Application Name | String | The name of the Argo CD application to sync. | Yes |
| Additional application sync flags | String | A list of flags to set when running the application sync step.  For example: '--config=path'. Specify each flag on a new line.  If the flag takes an argument, put the argument on a separate line or use an equal '=' (not whitespace) between the flag and argument. | Yes |
| Component Template | String | The name of the Argo CD application to sync. | Yes |


### Login

Login to an Argo CD instance.


| Name | Type | Description                                                                                                          | Required |
| ---- | ---- | -------------------------------------------------------------------------------------------------------------------- | -------- |
| Argo CD Server | String | The name or IP address of the Argo CD server to login to. | Yes |
| User Name | String | The username of an account to authenticate. | Yes |
| Password | String | The password of an account to authenticate. | Yes |
| Additional login flags | String | A list of flags to set when running the login step.  For example: '--config=path'. Specify each flag on a new line.  If the flag takes an argument, put the argument on a separate line or use an equal '=' (not whitespace) between the flag and argument. | Yes |


|Back to ...||Latest Version|Argo CD ||||
| :---: | :---: | :---: | :---: | :---: | :---: | :---: |
|[All Plugins](../../index.md)|[Deploy Plugins](../README.md)|[1.1164092](https://raw.githubusercontent.com/UrbanCode/IBM-UCD-PLUGINS/main/files/argocd/ucd-plugins-argocd-1.1164092.zip)|[Readme](README.md)|[Overview](overview.md)|[Usage](usage.md)|[Downloads](downloads.md)|
