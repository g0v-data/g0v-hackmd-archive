# **[IPCTPE-11]**[TPE + Ignition Edge] User scenarios
## [IPCTPE-14]支援客戶安裝 Ignition Edge 於 UC-8112A, UC-8200
### **Summary**
客戶可以在有安裝 TPE 的 UC-8112A, UC-8200 上運行 Ignition Edge.
(如 Russ 回報的 OverlayFS 的問題，Ignition Edge license 在設備重開機之後，依然要維持有效狀態。）

**Validation Steps**

1. Ignition service is not running on first boot and Gateway is on the commissioning page.
2. Correct acceptance of the IASLA.
3. If shipping with MQTT, correct acceptance of CLSLA.
4. Ensure all modules are installed. If modules are uninstalled to reduce installation size, the
correct modules are installed for the pre-licensed edition the device is shipping with.
5. If shipping with Edge MQTT or Edge IIoT, the MQTT modules needed are pre-installed and
connections can be made.
6. The version of Ignition that is loaded on the device is correctly licensed.
7. Ignition starts without error messages or concerning warnings in the Ignition Diagnostic
logs.
8. No existence of the .uuid file before starting Ignition. A fresh .uuid is generated when
Ignition is started for the first time.
9. Proper memory settings are set in the ignition.conf file for both initial and max memory.
10. An outgoing and incoming Gateway Network connection can be made.
11. Remote Tags and Remote Tag Historian work on the Gateway Network
12. Benchmarks show reasonable consistent throughput
13. Upon power loss and restoration, Ignition automatically starts back up and successfully
connects to the Gateway Network and MQTT if applicable.
14. If the device has documentation for a “hard reset” or “factory reset”, the Ignition
configuration, projects, and .uuid should all be properly reset to match the factory image,
and the agreements should be presented again before Ignition starts.

**Know issue**
* The overlayfs will cause the Ignition Edge license to be invalid after each reboot, unless there is an update to the current FW image. Wes Huang, Joe Lin, and Ken Chou have details on how this was done for the UC-8200 Images to correct the issue (due to dual core CPU)	example of the check that is performed by Ignition license:	{using the `stat /bin` command}
the inode value will change after each boot.
    *    reboot system to check if Ignition Edge license is valid