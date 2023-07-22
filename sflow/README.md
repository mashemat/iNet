# In Network Monitoring Strategies
## sFlow
sFlow has two components: 
- sFlow Agent - should be enabled within the switch to send sFlow datagrams to the collector
- sFlow collector - collects sflow datagrams

### To configure sFlow Agent on the switch:
Run these command in global config mode to configure sFlow paramenters
```
switch (config)# protocol sflow
switch (config)# sflow enable
switch (config)# sflow
switch (config sflow)# collector-ip aaa.bbb.ccc.ddd
switch (config sflow)# sampling-rate 4000
switch (config sflow)# counter-poll-interval 5
```
Run this command on specific interface(s) to enable sFlow monitoring on the interface(s)
```
switch (config) # int ethernet 1/1
switch (config interface ethernet 1/1) # sflow enable
```
Finally, you should be able to confirm the configuration, using the following command:
```
switch # show sflow

sflow protocol: enabled
sflow: enabled
VRF name: default
sampling-rate: 4000
max-sample-size: 128
counter-poll-interval: 10
max-datagram-size: 1400
collector ip: 10.128.15.1
udp port: 6343
ip-agent: 10.128.15.251

ingress ports:
Interfaces:
Ethernet eth1/4 eth1/2 eth1/1 eth1/3
Port-channel po13
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
