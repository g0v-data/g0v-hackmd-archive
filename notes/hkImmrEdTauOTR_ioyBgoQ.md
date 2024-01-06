# Troubleshooting datacenter network loop
###### tags: `TS`

Event Description:
When building the DDOS area happen the network loop situation occurs; when the loop happens the service will crash, and the attack server connects "before switch" to the pressure test IPS can handle attack traffic, the attack server's MAC address for unknown reason's display at the MGMT environment.

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_6ef377406689caec47b51008919fa363.png)

Root cause:
The Citrix load balancer uses VLAN 1 to be a management, but the VLAN 1 is native VLAN and the Truck port native VLAN is untagged, and the MGMT VLAN also uses native VLAN, so will cause the VLAN1 device can connect to each other, and the two of load balancer connect to the same MGMT environment and same private environment, if the VLAN 1 has new device connect the MAC address table will be renewed, and will happen the broadcast storm.

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_300671fafcf49c5586dd78e9b48542cf.png)

Solve:
specify unused VLAN numbers for the MGMT environment and exclude the MGMT environment VLAN number at the Trunck port in the private environment.


