
# Njs-Unit - Usage

To use the plug-in, the plug-in must be loaded and an instance created. Load the plug-in into the DevOps Velocity container if necessary. From the user interface, click **Settings** > **Integrations** > **Plugins**. On the Plugins page, locate the plug-in and click **Load Plugin**. To create an instance, locate the plug-in and click **Install**. The plug-in is now listed below those plug-ins to be installed and available for invoking.


## Integration type

The Njs-Unit plugin is a parser type plugin. It parses XML and JSON data. 

The following shows the schema for the payload. Replace the angle brackets with your values for the parameters.


```

{

"tenant_id": "<tenant_id>",    // required Tenant ID
"metricName": "<metric_name>", // optional: name for recurring test set
"application": {
"name": "<application_name>"  //Name of application
}``,
"record": {

"recordName": "<record_name>", // optional: Name for this record
"executionDate": 1547983466015, // optional:
UNIX Epoch
"pluginType": "Njs-Unit",
"dataFormat": "mocha/junitXML", //for xml use these mocha/junitXML, jest/junitXML, tape/junitXML,  
                                tap/junitXML format and for JSON use these mochaJSON, jestJSON, tapeJSON, tapJSON format
"metricsRecordUrl": "<Jenkins_build_url>"
// optional: To link the Jenkins build with test results
}``,
"build": {  // Optional: One of the following
fields must be included
"buildId": "<build_id>",
"jobExternalId": "<external_job_id>",
"url":
"<build_url>",
}``,
"commitId": "<commit_id>",  // optional
"pullRequestId": "<pullrequest_id>", // optional

"environment": "<environment_name>" // optional
}``

```

## Invoking the plug-in

To gather data from the Njs-Unit server, send an HTTP Post request with the data to parse. Whenever a there is a hit to the endpoint, the data is parsed and displayed as metrics in HCL Accelerate. You can use various methods such as Postman, REST calls, CURL, and CI/CD tools like Jenkins to invoke the plugin endpoints.

### Invoke the plug-in using a Rest call

When using a REST call to invoke the Njs-Unit plugin, it must be a POST method and include the location of the HCL Accelerate quality data endpoint. 

The following request sample shows a REST call that you can copy and update as necessary. Key points about the snippet: 

The URL points to the HCL Accelerate quality data endpoint. Update with the server location for your installation of HCL Accelerate. 

The BODY of the call is a multipart/form data. It includes information about the payload. 
METHOD: POST  
URL: https://<url_urbancodevelocity_server>/reporting-consumer/metrics  
BODY (multipart/form-data): 
 { 
  payload: <payload_json_object_string> // See below for schema format 
 testArtifact: <xml_file/JSON_file> 
 } 

### Invoke using Curl 

curl --request POST \ 
  --url https://url_urbancodevelocity_server>/reporting-consumer/metrics \ 
  --form 'payload={ 
  "tenant_id": "", 
  "application": { 
    "name": "My Application" 
  }, 
  "record": { 
    "pluginType": "Njs-Unit", 

        "dataFormat": "mocha/junitXML" // for xml use these mocha/junitXML, jest/junitXML, tape/junitXML,  tap/junitXML format and for JSON use these mochaJSON, jestJSON, tapeJSON, tapJSON format 

  } 
} 
' \ 
  --form testArtifact=@test-result/mocha.xml 

### Payload schema 

The following shows the schema for the payload. Replace the angle brackets with your values for the parameters. 
{ 
  "tenant_id": "<tenant_id>",    // required Tenant ID 
  "metricName": "<metric_name>", // optional: name for recurring test set 
  "application": { 
    "name": "<application_name>"  //Name of application 
  }, 
  "record": { 
    "recordName": "<record_name>", // optional: Name for this record 
    "executionDate": 1547983466015, // optional: UNIX Epoch 
    "pluginType": "Njs-Unit", 

        "dataFormat": "mocha/junitXML", //for xml use these mocha/junitXML, jest/junitXML, tape/junitXML,  tap/junitXML format and for JSON use these mochaJSON, jestJSON, tapeJSON, tapJSON format 

    "metricsRecordUrl": "<Jenkins_build_url>" // optional: To link the Jenkins build with test results 
  }, 
  "build": {  // Optional: One of the following fields must be included  
    "buildId": "<build_id>", 
    "jobExternalId": "<external_job_id>", 
    "url": "<build_url>", 
  }, 
  "commitId": "<commit_id>",  // optional 
  "pullRequestId": "<pullrequest_id>", // optional 
  "environment": "<environment_name>" // optional 
} 



|Back to ...||Latest Version|Njs-Unit |||
| :---: | :---: | :---: | :---: | :---: | :---: |
|[All Plugins](../../index.md)|[Velocity Plugins](../README.md)|[1.0.4-File 1 ](https://raw.githubusercontent.com/UrbanCode/IBM-UCV-PLUGINS/main/files/ucv-ext-njs-unit/ucv-ext-njs-unit%3A1.0.4.tar.7z.001)[and 1.0.4-File 2](https://raw.githubusercontent.com/UrbanCode/IBM-UCV-PLUGINS/main/files/ucv-ext-njs-unit/ucv-ext-njs-unit%3A1.0.4.tar.7z.002)|[Readme](README.md)|[Overview](overview.md)|[Usage](usage.md)|
