# Why We Need Segment Routing
###### tags: `Network` `Service Provider` 
```
Updated by OneNote on 30th Dec 2019.
```
The main drivers for hugging SR instead of traditional MPLS (LDP/RSVP) are
* The optimization of the signaling. It is carried out by decoupling LDP.
* ECMP supported. It is one of main shortages of RSVP.
* Easily distinguish (from troubleshooting perspective) the traffic is being stuck on which node.

![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_6f5e2e7e97357040974a9886eac14e96)
# 
The 2nd screenshot for the point of "The optimization of the signaling" (Segment Routing can remove protocols).
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_b93a22025e0450ed58d30c39279e0fff)
# 
One of the significant differences between LDP and SR is the label allocation. By default, LDP allocates the label for both the node-level (loopback address) and the link-level (every link). In essence, if the TE hasn't been considered for the entire IP/MPLS transfer backbone, then the link-level labels aren't really required. Unlike LDP, SR adopts the opposite way. It only allocates the label for the node-level by default.
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_0186cf49287be4392f345d0319e538b8)
# 
Continue with the previous section. In essence, if the TE hasn't been considered for the entire IP/MPLS transfer backbone, then the Adj-SID isn't required due to ECMP could be easily fulfilled by way of the PID.
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_0368bbdbdc7295f80afc73660e8a1092)
