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

A window on the local host should be visible after starting the sflow-rt service with flow-trend app downloaded.

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

![alt text](https://github.com/niks16/iNet/blob/main/screenshots/sflow_RDMA_WRITE.png?raw=true)

For more information, visit: 
https://sflow-rt.com/define_flow.php

## Performance Co-Pilot (PCP)
PCP is a framework and services to support system-level performance monitoring and performance management. The code can be found in the folder `pcp/onyx`. The metrics can be viewed both on command line and in a graphical way.
![alt text](https://github.com/niks16/iNet/blob/main/screenshots/pcp.png?raw=true)

For more information regarding implementing a PMDA, visit: https://ryandoyle.net/posts/writing-a-pmda-for-pcp/

## Open-MPI
To test the monitoring tools on the HPC message-passing protocol, the Message Passing Interface (MPI) was used. The Open MPI is an open-source implementation of the Message Passing Interface (MPI). It RDMA through InfiniBand and RoCE protocols. The script used for testing can be found in the folder `mpi`.
