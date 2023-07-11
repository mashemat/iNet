# iNet
## sFlow
sFlow has two components: 
- sFlow Agent - should be enabled within the switch to send sFlow datagrams to the collector
- sFlow collector - collects sflow datagrams

### To configure sFlow Agent on the switch:
```
switch (config)# protocol sflow
switch (config)# sflow enable
switch (config)# sflow
switch (config sflow)# collector-ip aaa.bbb.ccc.ddd
switch (config sflow)# sampling-rate 4000
switch (config sflow)# counter-poll-interval 5
```
### To configure tools on the collector to visualize sFlow packets

1. [Download sFlow-RT](https://sflow-rt.com/download.php)
2. Run command: `sflow-rt/get-app.sh sflow-rt flow-trend`
3. Restart sFlow-RT

Alternatively, use the Docker image:
https://hub.docker.com/r/sflow/flow-trend/

For more information, visit:
https://sFlow-RT.com

The following window on the local host should be visible after starting the sflow-rt service with flow-trend app downloaded:
<img width="1438" alt="image" src="https://github.com/niks16/iNet/assets/22795428/d0a4a51d-2c6d-4097-b3ba-62245e4a2ab6">

On defining the flow specification with the appropriate keys, the flow-trend graph shows only the RoCEv2 traffic.
|Name| Comment|
|:----|:----|
|ipsource | source address|
|ipdestination | destination address|
|ibbt_offset | IBBT header offset from start of packet|
|ibbtack | acknowledge Request|
|ibbtdestqp | destination QP|
|ibbtopcode | opcode|
|ibbtopname | operation Name|
|ibbtoptransport | transport Type|
|ibbttver | transport Header Version|


Further, a filter can be added:
- udpdestinationport = 4791

![image](https://github.com/niks16/iNet/assets/22795428/296612c9-d3d3-4be2-9b62-e929c53b4d56)

For more information, visit: 
https://sflow-rt.com/define_flow.php

## PCP (Performance Co-Pilot)
PCP is a framework and services to support system-level performance monitoring and performance management. The code can be found in the folder `pcp`.
For more information regarding implementing a PMDA, visit: https://ryandoyle.net/posts/writing-a-pmda-for-pcp/
