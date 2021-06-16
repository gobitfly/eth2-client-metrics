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


