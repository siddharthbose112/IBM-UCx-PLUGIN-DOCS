# GenAI Summary Release-IBM - Usage

To use the GenAI Summary Release–IBM plug-in, the plug-in must be loaded and an instance created before you can configure the plug-in integration. You can define configuration properties in the user interface.

##  Integration

### Prerequisites
1. IBM DevOps Velocity 5.0.8 or Higher
2. Release Summary docker image (IBM plug-in)

### Offline Integration
1. Pull release summary docker image
2. In IBM DevOps Velocity, click **Settings > Integrations > Available**.
2. Click **Load Plugin**, and enter `[RELEASE SUMMARY IMAGE NAME]:[LATEST_TAG]`. For example `ucv-ext-release-summary-ibm:1.0.3`
3. On the Add Integration page enter values for the fields used to configure the integration and define communication.
4. Click **Save**.

### Online Integration

1. From the Plug-ins page, click **Settings > Integrations > Plug-ins**.
2. Under the Action column for the plug-in, click **Add Integration**.
3. On the Add Integration page enter values for the fields used to configure the integration and define communication.
4. Click **Save**.

### LLM Service Configuration
Provide the following plug-in configuration options:

- **watsonx.ai API Key**: API key to authenticate and use with the Watsonx.ai service (https://cloud.ibm.com/docs/account?topic=account-userapikey&interface=ui)
- **watsonx.ai project_id**: Provide project_id or space_id (https://www.ibm.com/docs/en/watsonx-as-a-service?topic=projects)
- **watsonx.ai service URI**: Depending on the region of your provisioned service instance, use one of the urls described in the documentation (https://ibm.github.io/watsonx-ai-python-sdk/setup_cloud.html#authentication)

## Invoking the plug-in

The plug-in is invoked when you generate the Release Readiness Report after integrating with the Handlebar reporter plug-in. The data from the GenAI Summary Release-IBM plug-in is displayed in a section called Release Summary within the Release Readiness Report.

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

2. `../reporting-consumer/pluginEndpoint/[INTEGRATION ID]/emulate` This endpoint is provided for just testing purposes. It emulates the generation of the summary and can be used to test the integration of release summary plug-in with velocity. Expected schema is 
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

## Configuration Properties

The following tables describe the properties used to configure the integration. Each table contains the field name when using the user interface and the property name when using a JSON file.

|Name|	Type|	Description|	Required|	Property Name|
|----|----|----|----|----|
|Integration Name|	string|	The name for plug-in integration|	Yes	|Name|
|LLM-Drop-Down	|array	|The LLM Provider	|Yes	|llmDropdown|
|WATSONX_APIKEY	|string	|The Api-key for WATSONX X	|Yes	|WATSONX_APIKEY|
|WATSONX_PROJECT_ID|	integer	|The ID of the project in WATSONX	|Yes	|WATSONX_PROJECT_ID|
|WATSONX_URL	|string	|URL for WARSONX	|Yes	|WATSONX_URL|


|Back to ...||Latest Version|GenAI Summary Release-IBM|||
| :---: | :---: | :---: | :---: | :---: | :---: |
|[All Plugins](../../index.md)|[Velocity Plugins](../README.md)|[1.0.3](https://hub.docker.com/r/urbancode/ucv-ext-release-summary-ibm/tags)|[Readme](README.md)|[Overview](overview.md)|[Downloads](downloads.md)|