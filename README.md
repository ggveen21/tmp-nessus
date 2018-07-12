# Nessus

https://www.tenable.com/products/nessus-home

## Overview
TODO

## Lookups integrated with Nessus

##### Note

`testingintegrations` is a DNIF event store that can be uploaded for testing.

### Retrieve Latest report

Complete latest report for a given scan ID.

- input : A Scan ID

```
_fetch $Domain from testingintegrations limit 1
>>_lookup alienvault-otx get_domain_report $Domain
```

###### Sample
The lookup call returns output in the following structure for available data

|Field|Description|
|-|-|
|$NESHostname|Host name that was scanned|
|$NESPort|Port that was scanned|
|$NESProtocol|Protocol that was scanned by the host name|
|$NESSeverity|Severity of the report|
|$NESPluginID|ID of Plugin used in the report item|
|$NESPluginName|Name of the Plugin used in the report item|
|$NESPluginFamily|Family to which the plugin belongs|
|$NESPluginType|Type of plugin which is used|
|$NESPluginOutput|Output received by the plugin|
|$NESDescription|Description of the report|
|$NESSolution|Solution provided by the report|
|$NESSynopsis|Synopsis of the report|

### Retrieve All reports for a scan
To get all the reports for a particular scan ID.

- input : A Scan ID

```
_fetch $Domain from testingintegrations limit 1
>>_lookup alienvault-otx get_domain_pulse_report $Domain
```

###### Sample output
The lookup call returns output in the following structure for available data

|Field|Description|
|-|-|
|$NESHostname|Host name that was scanned|
|$NESPort|Port that was scanned|
|$NESProtocol|Protocol that was scanned by the host name|
|$NESSeverity|Severity of the report|
|$NESPluginID|ID of Plugin used in the report item|
|$NESPluginName|Name of the Plugin used in the report item|
|$NESPluginFamily|Family to which the plugin belongs|
|$NESPluginType|Type of plugin which is used|
|$NESPluginOutput|Output received by the plugin|
|$NESDescription|Description of the report|
|$NESSolution|Solution provided by the report|
|$NESSynopsis|Synopsis of the report|

## Using the Nessus API with DNIF  
The AlienVault OTX API can be found on the Alien Vault website at

  https://otx.alienvault.com/api

### Getting started with AlienVault OTX API with DNIF

1. ###### Login to your Data Store, Correlator, and A10 containers.  
   [ACCESS DNIF CONTAINER VIA SSH](https://dnif.it/docs/guides/tutorials/access-dnif-container-via-ssh.html)
2. ###### Move to the `/dnif/<Deployment-key>/lookup_plugins` folder path.
```
$cd /dnif/CnxxxxxxxxxxxxV8/lookup_plugins/
```
3. ###### Clone using the following command
```  
git clone https://github.com/dnif/lookup-alienvault-otx.git alienvault-otx
```
4. ###### Move to the `/dnif/<Deployment-key>/lookup_plugins/alienvault-otx/` folder path and open dnifconfig.yml configuration file     

 Replace the tag: <Add_your_api_key_here> with your AlienVault API key which can be generated at https://otx.alienvault.com

```
lookup_plugin:
  AVOTX_API_KEY: <Add_your_api_key_here>
```
