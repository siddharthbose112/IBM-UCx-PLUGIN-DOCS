# z/OS Rexx Executor - Steps

---

## Process steps in the z/OS Rexx Executor plug-in


## zOS Rexx Executor

Use this step to write input text to a sequential dataset. 
> **Note:** To create a GDG version add (+1) along with GDG base. An output property **DatasetName** will contain the actual GDG version dataset name that is created and can be referred in successive steps of the process.


| Name             | Type                                                           | Description                                                                                                                                                                                                    | Required |
|------------------|----------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|----------|
| Source Type      | Enumeration: TEXT / DATASET / ${p?:dataset.writer.source.type} | Source of data for writing into Output sequential dataset. Select DATASET to write from a PDS member or sequential dataset, FILE to write from a USS file, or TEXT to write text to output sequential dataset. | Yes      |
| Source Value     | String                                                         | Inline REXX statements or PDS containing REXX program. If the quotation marks are omitted, the user’s data set prefix from the TSO profile is automatically appended to the front of the data set name.        | Yes      |
| Arguments        | String                                                         | Provide a list of arguments to the REXX separated by space                                                                                                                                                     | No       |
| SYSPROC Datasets | String                                                         | Provide a list of datasets to be mapped as SYSPROC datasets for the REXX program                                                                                                                               | No       |

|          Back to ...          |                                |                                                                   Latest Version                                                                    | z/OS Dataset Writer ||||
|:-----------------------------:|:------------------------------:|:---------------------------------------------------------------------------------------------------------------------------------------------------:|:-------------------:| :---: | :---: | :---: |
| [All Plugins](../../index.md) | [Deploy Plugins](../README.md) | [4.1138411](https://raw.githubusercontent.com/UrbanCode/IBM-UCD-PLUGINS/main/files/zos-dataset-writer/ucd-plugins-zos-dataset-writer-4.1138411.zip) | [Readme](README.md) |[Overview](overview.md)|[Usage](usage.md)|[Downloads](downloads.md)|
