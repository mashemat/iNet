## PCP
### To install PCP:
visit:\
https://pcp.io/download.html

### Get Congestion Parameters from the switch
1. Place the onyx folder under `/var/lib/pcp/pmdas`
2. Execute `./Install`
3. The metrics from the switch can be fetched using `pminfo -f`:
   
![alt text](https://github.com/niks16/iNet/blob/main/screenshots/pcp_output.png?raw=true)

4. The metrics can be viewed on the pmchart as well:

![alt text](https://github.com/niks16/iNet/blob/main/screenshots/pcp.png?raw=true)
