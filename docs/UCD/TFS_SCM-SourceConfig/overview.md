
# Microsoft TFS_SCM (Team Foundation Server) - Overview

The Microsoft TFS\_SCM (Team Foundation Server) source configuration plug-in automates importing version artifacts from a Team Foundation Server.


### Step palette

To access this plug-in in the palette, click **Source and Repositories** > **Team Foundation ServerSCM**.

### Compatibility

The IBM DevOps Deploy source configuration plug-in for Microsoft Team Foundation ServerSCM works with Team Foundation Server, Team Explorer Everywhere, and Visual Studio Online. This plug-in supports Team Foundation Server 2010, 2012, 2013, 2015 and 2017.

This plug-in requires version 6.0.1 or later of IBM DevOps Deploy.

This plug-in supports agents that are running on Microsoft Windows.

### Installation

Microsoft .NET Framework 3.5 must be installed on the agent computer where the plug-in is installed.

No special steps are required for installing the plug-in. See [Installing plug-ins in DevOps Deploy](https://community.ibm.com/community/user/wasdevops/blogs/laurel-dickson-bull1/2022/06/13/install-plugins "Installing plug-ins in DevOps Deploy").

### History

#### Version 17

* Upadted log4j dependencies.


#### Version 9

* APAR PI89045: add support for setting isFinished flag flag when importing versions.

#### Version 8

* Fixes APAR PI87707, a regression where the user who requested a manual version import was not being tracked.

#### Version 7

* RFE 108136Workspace and Workspace Local Folder are now optional fields. This allows for a clean directory on each import. If these properties are left empty, a new temporary workspace will be created with its mapped folder in the agents working directory. The temporary workspace and folder are removed after completion.

#### Version 6

* Added short output logging.
* Updated plugin.xml descriptions and ordering.
* The tf Path property can be empty if supplied on the PATH environment variable.

#### Version 5

* Support property file encryption.

#### Version 4

* Version 4 includes a fix for APAR PI57417. The plug-in now checks the agent settings for acceptance of self-signed certificates.

#### Version 3

* Version 3 includes support for Team Foundation Server 2015, Team Explorer Everywhere, and Visual Studio Online.

#### Version 2

* Fixes running a process after creating a version.
* APAR PI34268the path to the executable was incorrect unless the user appended tf.exe to the end of the path.

#### Version 1

* Initial release of the TFS source configuration plugin.

|Back to ...||Latest Version|Microsoft TFS_SCM (Team Foundation Server) |||||
| :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: |
|[All Plugins](../../index.md)|[Deploy Plugins](../README.md)|[17.1154009](https://raw.githubusercontent.com/UrbanCode/IBM-UCD-PLUGINS/main/files/TFS_SCM-SourceConfig/ucd-TFS_SCM-SourceConfig-17.1154009.zip)|[Readme](README.md)|[Troubleshooting](troubleshooting.md)|[Settings](settings.md)|[Usage](usage.md)|[Downloads](downloads.md)|
