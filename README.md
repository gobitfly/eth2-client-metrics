# Ethereum consensus client metrics


| Client   | Version   | Support     | Docs
| :------------- | :----------: | :----------: | :----------: |
|  Lighthouse | v1.4.0  | Yes  | No   |
|  Prysm | v1.3.10 | Yes (Alpha)   | [Yes](https://docs.prylabs.network/docs/prysm-usage/client-stats/ "Yes")   |
|  Teku | / | No  | No   |
|  Nimbus | / | No   | No   |


------------

## Specification

***Included in every Request***

| Metric   | Description   | 
| :------------- | :----------: | 
|  version |  (int) Stats Data Specification Version 1  |
|  timestamp | (long) unix timestamp in milliseconds  |
|  process |  (string) validator, beaconnode, system  |


------------

***Process General (included in all process requests except system)***

| Metric   | Description   | 
| :------------- | :----------: | 
|  cpu_process_seconds_total | (long) cpu seconds consumed by process |
|  |  |
|  memory_process_bytes	 |  bytes |
|  |  |
| client_name | (string) prysm, lighthouse, nimbus, teku |
| client_version |  (string) |
| client_build | (int) incrementing for easier comparison |
|  |  |
| sync_eth2_fallback_configured | (bool) whether a fallback is configured |
| sync_eth2_fallback_connected | (bool) whether we are currently connected with fallback |

------------

***Beaconnode additionals***


| Metric   | Description   | 
| :------------- | :----------: | 
|  disk_beaconchain_bytes_total	 | (long) |
|  |  |
| network_libp2p_bytes_total_receive | (long) |
| network_libp2p_bytes_total_transmit | (long) |
| network_peers_connected    | (int) total connected |
| sync_eth1_connected  | (bool) Eth1 node connected AND  |
| sync_eth2_synced  | (bool) Eth2 beaconnode in sync  |
| sync_beacon_head_slot	| (long) slot head |
| sync_eth1_fallback_configured	 | (bool) whether a fallback is configured |
| sync_eth1_fallback_connected | (bool) whether we are currently connected with fallback |
| slasher_active | (bool) whether slasher is active |

------------

***Validator additionals***

| Metric   | Description   | 
| :------------- | :----------: | 
|  validator_total | (int) |
|  validator_active | (int) |

------------

**System Only** 

System only stats does not require any of the above stats except *Included in every Request* (example at the bottom)

| Metric   | Description   | 
| :------------- | :----------: | 
|  cpu_cores   | (int) |
|  cpu_threads  | (int) |
|  |  |
| memory_node_bytes_total | (long) |
| memory_node_bytes_free | (long) |
| memory_node_bytes_cached | (long) |
| memory_node_bytes_buffered |(long) |
|  |  |
| disk_node_bytes_total| (long) |
| disk_node_bytes_free | (long) |
|  |  |
| disk_node_io_seconds | (long) |
| disk_node_reads_total | (long) disk iops, completed reads |
| disk_node_writes_total  | (long) disk iops, completed writes |
|  |  |
| network_node_bytes_total_receive  | (long) |
| network_node_bytes_total_transmit  | (long) |
|  |  |
| misc_node_boot_ts_seconds | (long) |
| misc_os | (long) |

------------

## Update Interval
Stats will be pushed once every minute

------------

## Bundling Data
The endpoint can be used to post either single json objects or multiple objects in form of a json array. Take a look at the examples below.

------------

## Examples 

**Single Data**

```
{
   "version": 1,
   "timestamp": 11234567,
   "process": "validator",
   "cpu_process_seconds_total": 1234567,
   "memory_process_bytes": 654321,
   "client_name": "lighthouse",
   "client_version": "1.1.2",
   "client_build": 12,
   "sync_eth2_fallback_configured": false,
   "sync_eth2_fallback_connected": false,
   "validator_total": 3,
   "validator_active": 2
}
```

**Multiple Data**

```
[
   {
      "version":1,
      "timestamp":1618835497239,
      "process":"beaconnode",
      "cpu_process_seconds_total":6925,
      "memory_process_bytes":1175138304,
      "client_name":"lighthouse",
      "client_version":"1.1.3",
      "client_build":42,
      "sync_eth2_fallback_configured":false,
      "sync_eth2_fallback_connected":false,
      "validator_active":1,
      "validator_total":1
   },
   {
      "version":1,
      "timestamp":1618835497258,
      "process":"system",
      "cpu_cores":4,
      "cpu_threads":8,
      "cpu_node_system_seconds_total":1953818,
      "cpu_node_user_seconds_total":229215,
      "cpu_node_iowait_seconds_total":3761,
      "cpu_node_idle_seconds_total":1688619,
      "memory_node_bytes_total":33237434368,
      "memory_node_bytes_free":500150272,
      "memory_node_bytes_cached":13904945152,
      "memory_node_bytes_buffers":517832704,
      "disk_node_bytes_total":250436972544,
      "disk_node_bytes_free":124707479552,
      "disk_node_io_seconds":0,
      "disk_node_reads_total":3362272,
      "disk_node_writes_total":47766864,
      "network_node_bytes_total_receive":26546324572,
      "network_node_bytes_total_transmit":12057786467,
      "misc_node_boot_ts_seconds":1617707420,
      "misc_os":"unk"
   }
]
```

