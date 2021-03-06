# Nessus

https://www.tenable.com/products/nessus-home

## Overview
TODO

## Lookups integrated with Nessus

##### Note

`testingintegrations` is a DNIF event store that can be uploaded for testing.

### Retrieve Latest Scan Report for ScanID

This method retrieves latest reports for a particular Scan ID.

- input : A Scan ID

```
_fetch $ScanID from testingintegrations limit 1
>>_lookup nessus get_latest_report_for_scanid $ScanID
```

###### Sample walkthrough screenshot/video for latest scan report
The lookup call returns output in the following structure for available data

|Field|Description|
|-|-|
|$NESHostname|Host name that was scanned|
|$NESPort|Port that was scanned|
|$NESProtocol|Protocol used to scan the host name|
|$NESSeverity|Severity of the report item|
|$NESPluginID|ID of plugin used in the report item|
|$NESPluginName|Name of the plugin used in the report item|
|$NESPluginFamily|Family to which the plugin belongs|
|$NESPluginType|Type of plugin used|
|$NESPluginOutput|Output provided by the plugin|
|$NESDescription|Description of the report|
|$NESSolution|Solution provided in the report item|
|$NESSynopsis|Synopsis of the report|

### Retrieve All Reports for a ScanID
This method retrieves all scan reports for a particular Scan ID.

- input : A Scan ID

```
_fetch $ScanID from testingintegrations limit 1
>>_lookup nessus get_all_reports_for_scanid $ScanID
```

###### Sample walkthrough screenshot/video for all scan reports
The lookup call returns output in the following structure for available data

|Field|Description|
|-|-|
|$NESHostname|Host name that was scanned|
|$NESPort|Port that was scanned|
|$NESProtocol|Protocol used to scan the host name|
|$NESSeverity|Severity of the report item |
|$NESPluginID|ID of plugin used in the report item|
|$NESPluginName|Name of the plugin used in the report item|
|$NESPluginFamily|Family to which the plugin belongs|
|$NESPluginType|Type of plugin used|
|$NESPluginOutput|Output provided by plugin|
|$NESDescription|Description of the report|
|$NESSolution|Solution provided in the report item|
|$NESSynopsis|Synopsis of the report|

### Retrieve All ScanIDs
This method retrieves all the Scan IDs

```
_fetch * from testingintegrations limit 1
>>_lookup nessus get_all_scanids
```
###### Sample walkthrough screenshot/video for all scan ids
The lookup call returns output in the following structure for available data

|Field|Description|
|-|-|
|$NESScanID|ID for a particular scan|

## Using the Nessus API with DNIF  
The Nessus API can be found on the Nessus website at:

  https://www.tenable.com/products/nessus-home

### Getting started with Nessus API with DNIF

1. ###### Login to your Data Store, Correlator, and A10 containers.  
   [ACCESS DNIF CONTAINER VIA SSH](https://dnif.it/docs/guides/tutorials/access-dnif-container-via-ssh.html)
2. ###### Move to the `/dnif/<Deployment-key>/lookup_plugins` folder path.
```
$cd /dnif/CnxxxxxxxxxxxxV8/lookup_plugins/
```
3. ###### Clone using the following command
```  
git clone https://github.com/dnif/lookup-nessus.git nessus
```
4. ###### Move to the `/dnif/<Deployment-key>/lookup_plugins/nessus/` folder path and open dnifconfig.yml configuration file     
Replace the tag:
```
lookup_plugin:
  USERNAME: <add your username for nessus server>
  PASSWORD: <add your password for nessus server>
  HOST:<host on which the nessus server works>
  PORT:<add <port on which your nessus server is operating on>
```
