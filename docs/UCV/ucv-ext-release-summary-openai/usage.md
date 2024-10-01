# GenAI Summary Release - OpenAI

##  Install Release Summary plug-in

### Prerequisites
1. IBM DevOps Velocity 5.0.8 or higher
2. Release Summary docker image 


### Offline Installation
1.  Pull release summary docker image
2.  In IBM DevOps Velocity, click **Settings > Integrations > Available**.
2.  Click **Load Plugin**, and enter `[RELEASE SUMMARY IMAGE NAME]:[LATEST_TAG]`. For example `ucv-ext-release-summary-ibm:1.0.3`
3. On the Add Integration page enter values for the fields used to configure the integration and define communication.
4. Click **Save**.

### Online Installation

1. From the Plug-ins page, click **Settings > Integrations > Plug-ins**.
2. Under the Action column for the plug-in, click **Add Integration**.
3. On the Add Integration page enter values for the fields used to configure the integration and define communication.
4. Click **Save**.

### LLM Service Configuration
Provide the following plug-in configuration options:

- **OpenAI API Key**: API key to authenticate and use with the OpenAI service

## Invoking the plug-in

The plug-in is invoked when you generate the Release Readiness Report after integrating with the Handlebar reporter plug-in. The data from the GenAI Summary Release – OpenAI plug-in is displayed in a section called Release Summary within the Release Readiness Report.

The plug-in exposes the following endpoints:
1. `/reporting-consumer/pluginEndpoint/[INTEGRATION ID]/generate` This endpoint starts the generation of release summary. It expect to provide as part of the body the following parameter:
  - `vsmid` id of the value stream to generate the summary
  - `releaseid` id of the release to generate the summary
  - `currentStageName` pipeline stage containing the release candidate
  - `targetStageName` targeted release stage
  - `allVersions` if true, it will generated the summary considering work items of all versions associated with the release 
  
  The following is a sample curl command:

    curl -i -X POST \
        -H "Content-Type:application/json" \
        -d \
        '{
            "vsmid" : "6641e92d735e31769cb2f7cc",
            "releaseid" : "669548dc6d0a6b58e6a0add4",
            "targetStageName" : "PROD",
            "currentStageName" : "DEV"
        }' \
    'https://.../reporting-consumer/pluginEndpoint/669e12a21e0e8a001b70ec35/generate'
    
  
**Note**: Change the `669e12a21e0e8a001b70ec35` with the integration id of the created integration.

2. `../reporting-consumer/pluginEndpoint/[INTEGRATION ID]/emulate` This endpoint is provided for just testing purposes. It emulates the generation of the summary and can be used to test the integration of release summary plug-in with IBM DevOps velocity. Expected schema is 
 - `vsmid` id of the value stream to generate the summary
  - `releaseid` id of the release to generate the summary
  - `currentStageName` pipeline stage containing the release candidate
  - `targetStageName` targeted release stage
  - `allVersions` if true, it will generated the summary considering work items af all versions associated with the release 
  
The following is a sample curl command:
    
    curl -i -X POST \
        -H "Content-Type:application/json" \
        -d \
        '{
            "vsmid" : "6641e92d735e31769cb2f7cc",
            "releaseid" : "669548dc6d0a6b58e6a0add4",
            "targetStageName" : "PROD",
            "currentStageName" : "DEV"
            "releaseid" : "6641e4ce818a54c626097ad4"
        }' \
    'https://.../reporting-consumer/pluginEndpoint/669e12a21e0e8a001b70ec35/emulate'

**Note**: Change the `669e12a21e0e8a001b70ec35` with the integration id of the created integration.

## Exploring the summary
Generated summary will be stored as a field of the `release` document. The following graphql query can be use to search and retrive a generated summary.

    query releaseEventById(\$release_id : ID\!){
                releaseEventById(_id : \$release_id){
    				summary
    				lastSummaryOn
                }
        }



|Back to ...||Latest Version||||
| :---: | :---: | :---: | :---: | :---: | :---: |
|[All Plugins](../../index.md)|[Velocity Plugins](../README.md)|[1.0.1](https://hub.docker.com/r/urbancode/ucv-ext-release-summary-openai/tags)|[Overview](overview.md)|[Usage](usage.md)|[Downloads](downloads.md)
