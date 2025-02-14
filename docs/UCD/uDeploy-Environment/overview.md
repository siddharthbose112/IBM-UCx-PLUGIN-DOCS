
# IBM DevOps Deploy Environments - Overview


This plug-in includes steps that create and manage environments on the IBM DevOps Deploy server.

### Compatibility

This plug-in requires version 6.0 or later of IBM DevOps Deploy.

This plug-in is supported to run on all operating systems that are supported by the IBM DevOps Deploy agent, including z/OS with UNIX System Services.

### Installation

No special steps are required for installation. See [Installing plug-ins in IBM DevOps Deploy](https://community.ibm.com/community/user/wasdevops/blogs/laurel-dickson-bull1/2022/06/13/install-plugins "Installing plug-ins in IBM DevOps Deploy").

### History

#### Version 79

RFE 121148 Removed isSecure property from Set Component Environment Property to support property definition type.

#### Version 78

Plug-in name changed.

#### Version 77

Update for API changes in server.

#### Version 76

Fixed typo in Create Multiple Environments description.

#### Version 75

* RFE 100937 Added Create Multiple Environments step to create multiple environments using json.
* RFE 100937 Altered Add Environment to Team step to allow for multiple environments.

#### Version 74

RFE 83705Added Create Environment from Template step.

#### Version 73

Support property file encryption.

#### Version 72

Version 72 includes a fix for APAR PI45948, Set environment property step may fail if run simultaneously.

#### Version 68

* This version includes a step that retrieves basic information about an environment.
* The Create Environment step can now provision environments with blueprints.
* You can specify an environment profile when you create an environment.

|Back to ...||Latest Version|IBM DevOps Deploy Environments ||||
| :---: | :---: | :---: | :---: | :---: | :---: | :---: |
|[All Plugins](../../index.md)|[Deploy Plugins](../README.md)|[89.1159271](https://raw.githubusercontent.com/UrbanCode/IBM-UCD-PLUGINS/main/files/uDeploy-Environment/ucd-uDeploy-Environment-89.1159271.zip)|[Readme](README.md)|[Usage](usage.md)|[Steps](steps.md)|[Downloads](downloads.md)|
