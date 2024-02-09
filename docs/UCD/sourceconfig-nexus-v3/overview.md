
# Nexus Repository Manager V3 - Overview

The Nexus Repository Manager V3 plug-in provides steps to integration UrbanCode Deploy with Nexus Repository Manager V3.

This plug-in includes the following step:

* Import Version

### Compatibility

This plug-in requires IBM UrbanCode Deploy version 6.0 or later. Please note that this plugin was written against the Nexus Repository Manager V3 REST API, and will not work with V2. For Nexus Repository Manager V2 support, please see the [Nexus Source Config Plugin](https://urbancode.github.io/IBM-UCx-PLUGIN-DOCS/UCD/nexus-source-config/).

This plug-in runs on all operating systems that UrbanCode Deploy supports.

### Installation

No special steps are required for installation. See [Installing plug-ins in UrbanCode Deploy](https://community.ibm.com/community/user/wasdevops/blogs/laurel-dickson-bull1/2022/06/13/install-plugins "Installing plug-ins in UrbanCode Deploy").

### History

#### Version 5

* RFE-URBANCODE-I-598: Updated plugin to support multiple application files import from a Raw   repository in Nexus.
* Updated deprecated library HttpClientBuilder to HttpClientBuilder2.
* Updating Jettison library to 1.5.4 for CVE-2023-1436.

#### Version 4

* Updated dependencies for log4j and jettison.

#### Version 3

* A version's importing field will be correctly set and marked as finished importing when creating versions that aren't copied to codestation.


#### Version 2

* Fixing CVE:CVE-2019-4233.

#### Version 1

Initial release of this plug-in.


|Back to ...||Latest Version|Nexus Repository Manager V3 ||||
| :---: | :---: | :---: | :---: | :---: | :---: | :---: |
|[All Plugins](../../index.md)|[Deploy Plugins](../README.md)|[5.1164218](https://raw.githubusercontent.com/UrbanCode/IBM-UCD-PLUGINS/main/files/sourceconfig-nexus-v3/ucd-sourceconfig-nexus-v3-5.1164218.zip)|[Readme](README.md)|[Usage](usage.md)|[Steps](steps.md)|[Downloads](downloads.md)|
