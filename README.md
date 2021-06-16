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
|  **CPU Process Stats** |  |
|  cpu_process_seconds_total | (long) cpu seconds consumed by process |
|  |  |
|  **Memory Process Stats** |  |
|  memory_process_bytes	 |  bytes |
|  |  |
| client_name | (string) prysm, lighthouse, nimbus, teku |
| client_version |  (string) |
| client_build | (int) incrementing for easier comparison |

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

***System Only** 

System only stats does not require any of the above stats except *Included in every Request* (example at the bottom)

| Metric   | Description   | 
| :------------- | :----------: | 
| CPU |  |
|  cpu_cores   | (int) |
|  cpu_threads  | (int) |
|  |  |
| Memory |  |
| memory_node_bytes_total | (long) |
| memory_node_bytes_free | (long) |
| memory_node_bytes_cached | (long) |
| memory_node_bytes_buffered |(long) |
|  |  |
| Disk |  |
| disk_node_bytes_total| (long) |
| disk_node_bytes_free | (long) |
|  |  |
| disk_node_io_seconds | (long) |
| disk_node_reads_total | (long) disk iops, completed reads |
| disk_node_writes_total  | (long) disk iops, completed writes |
|  |  |
| Network |  |
| network_node_bytes_total_receive  | (long) |
| network_node_bytes_total_transmit  | (long) |
|  |  |
| misc_node_boot_ts_seconds | (long) |
| misc_os | (long) |
