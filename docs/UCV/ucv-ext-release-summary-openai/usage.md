# GenAi Summary Release - OpenAi

##  Install Release Summary Plugin

### Prerequisites
1. DevOps Velocity 5.0.7 or higher
2. Release Summary docker image 


### Install - Offline
1.  Pull release summary docker image
2.  Navigate to the `settings/integrations` page of Velocity  and select the `Installed` tab.
2.  Click the `Load Plugin` button near the top of the page, and enter in `[RELEASE SUMMARY IMAGE NAME]:[LATEST_TAG]`.
3.  Select `Submit` and the plugin will be installed. You will then see the `GenAI Summary Release - OpenAI` in the list of plugins (or if already present, the new uploaded version). Skip the requested configuration.

### Install - Online

1. Navigate to the `settings/integrations` page of Velocity  and select the `Available` tab.
2. Select `GenAI Summary Release - OpenAi` plugin and click `Install` action.

## Configure
To add the release summary integration navigate to `settings/integrations` page and select the `Installed` tab.
1. Check the `GenAI Release Summary - OpenAI` and click `Add Integration`
2. Insert a name for the integration
3. Select an LLM service
4. Provide settings for the selected LLM

### LLM Service Configuration
Provide the following plugin configuration options:

- **OpenAI API Key**: API key to authenticate and use with the OpenAI service

## Execution
The plugin will be triggered when we Run Release Readiness Report
it expose 2 endpoint:
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
    
  
**Note**: change the `669e12a21e0e8a001b70ec35` with the integration id of the created integration.

2. `../reporting-consumer/pluginEndpoint/[INTEGRATION ID]/emulate` This endpoint is provided for just testing purposes. It emulates the generation of the summary and can be used to test the integration of release summary plugin with velocity. Expected schema is 
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

**Note**: change the `669e12a21e0e8a001b70ec35` with the integration id of the created integration.

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
