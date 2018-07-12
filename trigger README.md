# Nessus

https://www.tenable.com/products/nessus-home

## Overview
TODO

## Triggers integrated with Nessus

##### Note

`testingintegrations` is a DNIF event store that can be uploaded for testing.

### Launch a Scan

This method launches a scan for a particular Scan ID

- input : A Scan ID

```
_fetch $ScanID from testingintegrations limit 1
>>_trigger nessus begin_scan_by_id $ScanID
```

###### Sample walkthrough screenshot/video for launching a scan
The lookup call returns output in the following structure for available data

|Field|Description|
|-|-|
|$NESUuid|Uuid of a Scan|

### Launch All Scans
This method launches all the scans on the Nessus Server

```
_fetch * from testingintegrations limit 1
>>_trigger nessus begin_all_scans
```

###### Sample walkthrough screenshot/video for launching all scans
The lookup call returns output in the following structure for available data

|Field|Description|
|-|-|
|$NESUuid|Uuid of a Scan|

## Using the Nessus API with DNIF  
The Nessus API can be found on the Nessus website at:

  https://www.tenable.com/products/nessus-home

### Getting started with Nessus API with DNIF

1. ###### Login to your Data Store, Correlator, and A10 containers.  
   [ACCESS DNIF CONTAINER VIA SSH](https://dnif.it/docs/guides/tutorials/access-dnif-container-via-ssh.html)
2. ###### Move to the `/dnif/<Deployment-key>/trigger_plugins` folder path.
```
$cd /dnif/CnxxxxxxxxxxxxV8/trigger_plugins/
```
3. ###### Clone using the following command
```  
git clone https://github.com/dnif/trigger-nessus.git nessus
```
4. ###### Move to the `/dnif/<Deployment-key>/trigger_plugins/nessus/` folder path and open dnifconfig.yml configuration file     
Replace the tag:
```
trigger_plugin:
  USERNAME: <add your username for nessus server>
  PASSWORD: <add your password for nessus server>
  HOST:<host on which the nessus server works>
  PORT:<add <port on which your nessus server is operating on>
```
