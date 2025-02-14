
# IBM DevOps Deploy Components - Overview

This plug-in manipulates components on the IBM DevOps Deploy server. For example, the steps in this plug-in can create components, add components to teams, and add properties to components.

### Compatibility

This plug-in requires version 6.0 or later of IBM DevOps Deploy.

This plug-in is supported to run on all operating systems that are supported by the IBM DevOps Deploy agent, including z/OS with UNIX System Services.

### Installation

No special steps are required for installation. See [Installing plug-ins in DevOps Deploy](https://community.ibm.com/community/user/wasdevops/blogs/laurel-dickson-bull1/2022/06/13/install-plugins "Installing plug-ins in DevOps Deploy").

### History

#### Version 71

Update for API changes in server.

#### Version 70

``${p:sourceConfigType}`` option has been added to the Create Components Source Config Type property. Specify this property within the process configuration to resolve a source config type that is not listed. Resolved MissingPropertyException in the Remove Tag from Component step.

#### Version 69

* RFE 100937 Added Create Multiple Components step to create multiple components using json.
* RFE 100937 Altered Add Component To Team step to allow adding multiple components to a team.

#### Version 68

Support property file encryption.

#### Version 67

Fixes APAR PI57417. Plug-in now checks the agent settings for acceptance of self signed certificates.

#### Version 66

* Added a step to add a tag to a component.
* Added a step to remove a tag from a component.

#### Version 65

This release of the plug-in includes steps to delete components and to get component applications.

#### Version 64

This release of the plug-in includes a fix for a compatibility defect with IBM DevOps Deploy version 6.1.0.4 and later.


|Back to ...||Latest Version|IBM DevOps Deploy Components ||||
| :---: | :---: | :---: | :---: | :---: | :---: | :---: |
|[All Plugins](../../index.md)|[Deploy Plugins](../README.md)|[78.1132354](https://raw.githubusercontent.com/UrbanCode/IBM-UCD-PLUGINS/main/files/uDeploy-Component/ucd-uDeploy-Component-78.1132354.zip)|[Readme](README.md)|[Usage](usage.md)|[Steps](steps.md)|[Downloads](downloads.md)|
