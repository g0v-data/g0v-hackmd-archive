Cypress Wifi Linux FMAC Driver Package - README
===============================================

Package Version
---------------
%VERSION%


Release Date
------------
%DATE%


Description
-----------
This is Cypress's Linux brcmfmac driver and firmware support package.
Brcmfmac is an open-source driver project.

Files in this release:
* Backports package (%F_BACKPORTS%)
* Firmware/clm_blob files (%F_FIRMWARE%)
* Cypress fmac patch files (%F_PATCH%)
* Device tree files (%F_DEVICETREE%)
* hostapd/wpa_supplicant patch (%F_HOSTAP%)
* Cirrent Agent (%F_CIRRENT%)
* Documents (docs/)
* README

For more information about the Linux brcmfmac project, see:

[brcm80211 Wireless Wiki](https://wireless.wiki.kernel.org/en/users/drivers/brcm80211)

For more information about Linux backports project, see:

[Linux Backports Project](https://backports.wiki.kernel.org/index.php/Main_Page)

11AX chips firmware
-------------------
* cyfmac5557x series
   * By default firmware cyfmac55572-pcie.trxse is used
   * If your chip is 55571, 55573 please also use cyfmac55572-pcie.trxse

11AC chips firmware
-------------------
* cyfmac5459x series
   * By default firmware cyfmac54591.* is included
   * If your chip is 54591/54590 please also use cyfmac54591.* for firmware/blob/nvram

Test Environment
----------------
* ARM (MCIMX6SX-SDB)
   * Linux v4.14.78 (NXP imx_4.14.78_1.0.0_ga)
   * backports
* x86
   * Linux v4.12
   * backports


Instructions
------------
The patch files in this package are based on Linux v5.15.58, so older kernels
need use backports package. Below are examples of how to use this package
with an older kernel or linux-stable v5.15.58.

### Using backports with an older kernel (v4.4+)

Linux kernel image and cypress driver modules need to be built separately.
Below is the example of using with iMX Linux v4.14.78:

#### Build the kernel image
```bash
#1. Have the BSP kernel source available
   git clone https://source.codeaurora.org/external/imx/linux-imx
   cd linux-imx
   git checkout imx_4.14.78_1.0.0_ga
#2. Set up build environment and kernel configuration
   source /opt/poky/1.8/environment-setup-cortexa7hf-vfp-neon-poky-linux-gnueabi
   make imx_v7_defconfig
#3. Edit .config and build cfg80211 as module
#     CONFIG_CFG80211=m
#     CONFIG_BCMDHD=n
#3.1 Disable cfg80211 regdb for the kernel above v5.4.18
#     CONFIG_CFG80211_REQUIRE_SIGNED_REGDB=n
#     CONFIG_CFG80211_USE_KERNEL_REGDB_KEYS=n
#4. Enable below configs in .config
#     CONFIG_ASYMMETRIC_KEY_TYPE=y
#     CONFIG_ASYMMETRIC_PUBLIC_KEY_SUBTYPE=y
#     CONFIG_X509_CERTIFICATE_PARSER=y
#     CONFIG_PKCS7_MESSAGE_PARSER=y
#5. Build the Linux kernel image
   make oldconfig
   make zImage -j 8
#6. The kernel image is available here
   arch/arm/boot/zImage
```

#### Build the cypress driver/backports modules
```bash
#1. Untar the Cypress backports package
    tar zxvf cypress-backports-*.tar.gz
    cd v5.15.58-backports
#2. (Native) compile local tools and generate .config (in a new terminal
#   without sourcing Yoctol toolchain settings)
    bash
    MY_KERNEL=<the 4.14.78 kernel path>
    make KLIB=$MY_KERNEL KLIB_BUILD=$MY_KERNEL defconfig-brcmfmac
#3. (Cross) compile kernel modules
    source /opt/poky/1.8/environment-setup-cortexa7hf-vfp-neon-poky-linux-gnueabi
    make KLIB=$MY_KERNEL KLIB_BUILD=$MY_KERNEL modules
#4. The kernel modules are available here
#      compat/compat.ko
#      net/wireless/cfg80211.ko
#      drivers/net/wireless/broadcom/brcm80211/brcmutil/brcmutil.ko
#      drivers/net/wireless/broadcom/brcm80211/brcmfmac/brcmfmac.ko
```

#### Device tree
```bash
#1. Untar the cypress devicetree package
    tar zxvf cypress-devicetree-*.tar.gz
#2. Find your board's dtb file, for example
#      cypress-devicetree/iMX6SX/4.14.78/imx6sx-sdb-btwifi-fmac.dtb
```
Note: If your board's dtb is not available in the cypress devicetree
      package, please refer to the available dts/dtsi files and create
      them for your board, then compile them for the dtb file. iMX dts
      files are located in linux-imx/arch/arm/boot/dts/ folder of the
      Linux kernel tree. Below command compiles a dtb file
```bash
    make ARCH=arm <devicetree name>.dtb
```

#### Load the cypress wifi driver
```bash
#1. Copy your boards's zImage and dtb files to the target board
    bash
    TARGET_IP=<target board IP>
    scp <dtb file> root@$TARGET_IP:/run/media/mmcblk1p1/cy.dtb
    scp <zImage file> root@$TARGET_IP:/run/media/mmcblk1p1/zImage_cy
#2. Copy firmware files to the target board
    tar zxvf cypress-firmware*.tar.gz
    scp firmware/* root@$TARGET_IP:/lib/firmware/cypress
#3. Copy your nvram file (from board vendor) to the target board and rename it
    scp <nvram file> root@$TARGET_IP:/lib/firmware/cypress/<fw name>.txt
#      (fw name is your chip's *.bin file name in the cypress firmware package)
#4. Copy cypress kernel modules to the target board
    scp <module files> root@$TARGET_IP:/lib/modules/4.14.78
#5. (iMX console) Press ctrl-c after target boot to enter u-boot and configure it
#   for the new zImage/dtb files
   env print image fdt_file
   setenv image zImage_cy
   setenv fdt_file cy.dtb
   saveenv
   env print image fdt_file
   reset
#6. (iMX console) Boot up the target board with the above zImage and insmod cypress modules
    insmod /lib/modules/4.14.78/compat.ko
    insmod /lib/modules/4.14.78/cfg80211.ko
    insmod /lib/modules/4.14.78/brcmutil.ko
    insmod /lib/modules/4.14.78/brcmfmac.ko
```
Note: More on fmac driver [firmware/nvram install](https://wireless.wiki.kernel.org/en/users/drivers/brcm80211#firmware_installation1)

### Using Linux Stable v5.15.58
```bash
#1. Download Linux stable kernel source
    wget https://git.kernel.org/pub/scm/linux/kernel/git/stable/linux.git/snapshot/linux-5.15.58.tar.gz
    tar zxvf linux-5.15.58.tar.gz
#2. In Linux root folder, untar/apply cypress patches with below bash commands
    cd linux-5.15.58
    tar zxvf cypress-patch*.tar.gz
    for i in cypress-patch/*.patch; do patch -p1 < $i; done
#3. Set kernel .config and enable below options, then compile kernel image
#      CONFIG_BRCMUTIL=y
#      CONFIG_BRCMFMAC=y
#      CONFIG_BRCMFMAC_SDIO=y
#      CONFIG_BRCMFMAC_PROTO_BCDC=y
#      CONFIG_BRCMFMAC_PCIE=y
#      CONFIG_BRCMFMAC_PROTO_MSGBUF=y
#4. (optional) Backup original firmware files
    cp /lib/firmware/cypress /lib/firmware/cypress-bak -r
#5. Update firmware files in /lib/firmware/cypress
    tar zxvf cypress-firmware*.tar.gz
    cp firmware/* /lib/firmware/cypress
#6. Boot the system with the new kernel image
```


Instructions - Hostap
---------------------
The patch files in this package are based on Hostap commit 13837a031a78.
Below is an example of how to apply these files and build
hostapd/wpa_supplicant binaries.

### Build the hostapd/wpa_supplicant binaries
```bash
#1. Download Hostap source and change the HEAD to commit 13837a031a78.
    git clone git://w1.fi/hostap.git
    cd hostap
    git checkout 13837a031a78
#2. In Hostap root folder, untar/apply cypress patches with below bash commands
    tar zxvf cypress-hostap_2_11-*.tar.gz
    for i in cypress-hostap_2_11-devel/*.patch; do patch -p1 < $i; done
#3. (Hostapd) in hostapd root directory, have a build time configuration file,
#   .config, and build hostapd and hostapd_cli
    cd hostapd
    cp defconfig_base .config
    make clean
    make
#4. (Wpa_supplicant) in wpa_supplicant root directory, have a build time
#   configuration file, .config, and build wpa_supplicant and wpa_cli
    cd wpa_supplicant
    cp defconfig_base .config
    make clean
    make
#5. The binaries are available here
#     hostap/hostapd/hostapd
#     hostap/hostapd/hostapd_cli
#     hostap/wpa_supplicant/wpa_supplicant
#     hostap/wpa_supplicant/wpa_cli
```
Note: Set CONFIG_SAE=y in .config to enable WPA3-Personal (SAE) support.
      5459x, 43012 and 43439 only supports sae_pwe 1 or 2 in hostapd.conf and wpa_supplicant.conf
Note: For commercial SAP use on an IOT device, we recommand to launch the AP with DTIM_PERIOD is 1.
      dtim_period=1 in hostapd.conf

Instructions - Cirrent Agent
----------------------------

The Cirrent Agent with IoT Network Intelligence support has been pre-compiled
for easy installation on platforms with armhf architecture.

### Install the Cirrent Agent files

```bash
#1. Untar the Cirrent Agent installation package
    tar zxvf %F_CIRRENT%
#2. Install the required files to the root / directory
    cp -av cypress-cirrent/* /
#3. Edit and uncomment PROVISION_CRED from the /etc/default/cirrent file with
#   credentials from https://console.cirrent.com
#4. Enable the Cirrent Agent to start on boot and reboot with Systemd init
    systemctl enable cirrent
#   or with SysV init
    update-rc.d cirrent defaults
    reboot
```

For more information on using the Cirrent Agent, please visit
https://support.cirrent.com


Supports
======================================================
### BT shared SDIO information
BTS_VERSION: 1.1.1


Cypress Wifi Linux FMAC Driver Package - Release Notes
======================================================

FMAC Driver Changes
-------------------
* SDIO (001, 006, 011, 039-041, 059, 061, 080)
* SoftAP (002, 042-043, 060, 064, 071, 078)
* Generic fixes (003, 014, 017, 045, 050-051, 053-055, 067-068, 070, 072-075)
* Wake on Wireless LAN (005, 012)
* Power saving (007, 010, 015, 077)
* USB (008-009, 030)
* Thermal throttling (013)
* 43570 (016)
* 54591 (018, 032, 057)
* RSDB (019, 021, 065-066)
* PCIE (020, 052, 076)
* Manufacturing (022, 023, 056, 081)
* Roaming (024-029)
* P2P (0031, 062, 069)
* 43012 (033-035)
* 4373 (036, 038)
* Throughput enhancement (037)
* ARP Offload (044)
* DPP (046, 058)
* Firmware/nvram (047, 063)
* Data path (048)
* Event handling (049)
* WPA3 (079)


FMAC Driver Patch List
----------------------
 * 0001-non-upstream-add-sg-parameters-dts-parsing.patch [x]
 * 0002-brcmfmac-support-AP-isolation.patch
 * 0003-non-upstream-make-firmware-eap_restrict-a-module-par.patch [x]
 * 0004-non-upstream-support-wake-on-ping-packet.patch [x]
 * 0005-non-upstream-remove-WOWL-configuration-in-disconnect.patch [x]
 * 0006-non-upstream-avoid-network-disconnection-during-susp.patch [x]
 * 0007-non-upstream-Changes-to-improve-USB-Tx-throughput.patch [x]
 * 0008-brcmfmac-introduce-module-parameter-to-configure-def.patch
 * 0009-non-upstream-configure-wowl-parameters-in-suspend-fu.patch [x]
 * 0010-non-upstream-disable-command-decode-in-sdio_aos-for-.patch [x]
 * 0011-brcmfmac-increase-default-max-WOWL-patterns-to-16.patch
 * 0012-non-upstream-Enable-Process-and-forward-PHY_TEMP-eve.patch [x]
 * 0013-non-upstream-fix-continuous-802.1x-tx-pending-timeou.patch [x]
 * 0014-non-upstream-add-sleep-in-bus-suspend-and-cfg80211-r.patch [x]
 * 0015-brcmfmac-add-CYW43570-PCIE-device.patch
 * 0016-non-upstream-fix-scheduling-while-atomic-issue-when-.patch [x]
 * 0017-brcmfmac-Support-89459-pcie.patch
 * 0018-brcmfmac-Support-multiple-AP-interfaces-and-fix-STA-.patch
 * 0019-non-upstream-Support-custom-PCIE-BAR-window-size.patch [x]
 * 0020-brcmfmac-support-for-virtual-interface-creation-from.patch
 * 0021-brcmfmac-increase-dcmd-maximum-buffer-size.patch
 * 0022-brcmfmac-set-net-carrier-on-via-test-tool-for-AP-mod.patch
 * 0023-nl80211-add-authorized-flag-back-to-ROAM-event.patch
 * 0024-brcmfmac-set-authorized-flag-in-ROAM-event-for-offlo.patch
 * 0025-brcmfmac-set-authorized-flag-in-ROAM-event-for-PMK-c.patch
 * 0026-nl80211-add-authorized-flag-to-CONNECT-event.patch
 * 0027-brcmfmac-set-authorized-flag-in-CONNECT-event-for-PM.patch
 * 0028-brcmfmac-add-support-for-Opportunistic-Key-Caching.patch
 * 0029-brcmfmac-To-support-printing-USB-console-messages.patch
 * 0030-non-upstream-Fix-no-P2P-IE-in-probe-requests-issue.patch [x]
 * 0031-brcmfmac-add-54591-PCIE-device.patch
 * 0032-non-upstream-support-DS1-exit-firmware-re-download.patch [x]
 * 0033-non-upstream-fix-43012-insmod-after-rmmod-in-DS1-fai.patch [x]
 * 0034-non-upstream-fix-43012-driver-reload-failure-after-D.patch [x]
 * 0035-brcmfmac-reset-PMU-backplane-all-cores-in-CYW4373-du.patch
 * 0036-non-upstream-calling-skb_orphan-before-sending-skb-t.patch [x]
 * 0037-non-upstream-workaround-for-4373-USB-WMM-5.2.27-test.patch [x]
 * 0038-non-upstream-disable-command-decode-in-sdio_aos-for-.patch [x]
 * 0039-non-upstream-disable-command-decode-in-sdio_aos-for-.patch [x]
 * 0040-non-upstream-disable-command-decode-in-sdio_aos-for-.patch [x]
 * 0041-brcmfmac-support-the-forwarding-packet.patch
 * 0042-brcmfmac-add-a-variable-for-packet-forwarding-condit.patch
 * 0043-brcmfmac-don-t-allow-arp-nd-offload-to-be-enabled-if.patch
 * 0044-non-upstream-ignore-FW-BADARG-error-when-removing-no.patch [x]
 * 0045-brcmfmac-Support-DPP-feature.patch
 * 0046-brcmfmac-move-firmware-path-to-cypress-folder.patch
 * 0047-brcmfmac-add-support-for-sof-time-stammping-for-tx-p.patch
 * 0048-non-upstream-free-eventmask_msg-after-updating-event.patch [x]
 * 0049-brcmfmac-fix-invalid-address-access-when-enabling-SC.patch
 * 0050-brcmfmac-add-a-timer-to-read-console-periodically-in.patch
 * 0051-brcmfmac-return-error-when-getting-invalid-max_flowr.patch
 * 0052-brcmfmac-Fix-to-add-skb-free-for-TIM-update-info-whe.patch
 * 0053-brcmfmac-Fix-to-add-brcmf_clear_assoc_ies-when-rmmod.patch
 * 0054-brcmfmac-dump-dongle-memory-when-attaching-failed.patch
 * 0055-brcmfmac-update-address-mode-via-test-tool-for-AP-mo.patch
 * 0056-brcmfmac-load-54591-firmware-for-chip-ID-0x4355.patch
 * 0057-brcmfmac-Fix-interoperating-DPP-and-other-encryption.patch
 * 0058-brcmfmac-fix-SDIO-bus-errors-during-high-temp-tests.patch
 * 0059-brcmfmac-Add-dump_survey-cfg80211-ops-for-HostApd-Au.patch
 * 0060-revert-brcmfmac-set-state-of-hanger-slot-to-FREE-whe.patch
 * 0061-brcmfmac-correctly-remove-all-p2p-vif.patch
 * 0062-brcmfmac-fix-firmware-trap-while-dumping-obss-stats.patch
 * 0063-brcmfmac-add-creating-station-interface-support.patch
 * 0064-brcmfmac-support-station-interface-creation-version-.patch
 * 0065-brcmfmac-To-fix-crash-when-platform-does-not-contain.patch
 * 0066-brcmfmac-Remove-the-call-to-dtim_assoc-IOVAR.patch
 * 0067-brcmfmac-fix-CERT-P2P-5.1.10-failure.patch
 * 0068-brcmfmac-Fix-for-when-connect-request-is-not-success.patch
 * 0069-brcmfmac-Avoiding-Connection-delay.patch
 * 0070-non-upstream-Revert-brcm80211-select-WANT_DEV_COREDU.patch [x]
 * 0071-brcmfmac-Fix-connecting-enterprise-AP-failure.patch
 * 0072-brcmfmac-Fix-for-skbuf-allocation-failure-in-memory-.patch
 * 0073-brcmfmac-Update-SSID-of-hidden-AP-while-informing-it.patch
 * 0074-brcmfmac-Fix-PCIE-suspend-resume-issue.patch
 * 0075-brcmfmac-disable-mpc-when-power_save-is-disabled.patch
 * 0076-brcmfmac-Fix-authentication-latency-caused-by-OBSS-s.patch
 * 0077-brcmfmac-support-external-SAE-authentication-in-stat.patch
 * 0078-brcmfmac-fix-sdio-watchdog-timer-start-fail-issue.patch
 * 0079-brcmfmac-Frameburst-vendor-command-addition.patch
 * 0080-brcmfmac-add-support-for-CYW43439-SDIO-chipset.patch
 * 0081-brcmfmac-add-BT-shared-SDIO-support.patch
 * 0082-brcmfmac-add-CYW43439-SR-related-changes.patch
 * 0083-brcmfmac-add-support-for-CYW43439-with-blank-OTP.patch
 * 0084-brcmfmac-support-43439-Cypress-Vendor-and-Device-ID.patch
 * 0085-brcmfmac-fix-P2P-device-discovery-failure.patch
 * 0086-brcmfmac-Add-SDIO-vendor-device-id-for-CYW89459-in-h.patch
 * 0087-brcmfmac-Add-CYW89459-HW-ID-and-modify-sdio-F2-block.patch
 * 0088-brcmfmac-Fix-AP-interface-delete-issue.patch
 * 0089-brcmfmac-Revise-channel-info-for-WPA3-external-SAE.patch
 * 0090-brcmfmac-Fix-structure-size-for-WPA3-external-SAE.patch
 * 0091-brcmfmac-support-54590-54594-PCIe-device-id.patch
 * 0092-brcmfmac-revise-SoftAP-channel-setting.patch
 * 0093-brcmfmac-Optimize-CYW4373-SDIO-current.patch [v5.13-rc7]
 * 0094-brcmfmac-use-request_firmware_direct-for-loading-boa.patch
 * 0095-brcmfmac-enable-pmk-catching-for-ext-sae-wpa3-ap.patch
 * 0096-brcmfmac-fixes-CYW4373-SDIO-CMD53-error.patch
 * 0097-brcmfmac-add-PCIe-mailbox-support-for-core-revision-.patch
 * 0098-brcmfmac-add-support-for-TRX-firmware-download.patch
 * 0099-brcmfmac-add-Cypress-PCIe-vendor-ID.patch
 * 0100-brcmfmac-add-support-for-CYW55560-PCIe-chipset.patch
 * 0101-brcmfmac-add-bootloader-console-buffer-support-for-P.patch
 * 0102-brcmfmac-support-4373-pcie.patch
 * 0103-brcmfmac-extsae-supports-SAE-OKC-roam.patch
 * 0104-nl80211-add-roaming-offload-support.patch
 * 0105-brcm80211-add-FT-11r-OKC-roaming-offload-support.patch
 * 0106-brcmfmac-support-extsae-with-psk-1x-offloading.patch
 * 0107-brcmfmac-Disable-out-of-band-device-wake-based-DeepS.patch
 * 0108-brcmfmac-skip-6G-oob-scan-report.patch
 * 0109-brcmfmac-Improve-the-delay-during-scan.patch
 * 0110-brcmfmac-add-FW-AP-selection-mod-param.patch
 * 0111-brcmfmac-Changing-info-messages-under-debug-BRCMF_IN.patch
 * 0112-revert-brcmfmac-Set-timeout-value-when-configuring-p.patch
 * 0113-brcmfmac-fixes-scan-invalid-channel-when-enable-host.patch
 * 0114-brcmfmac-do-not-disable-controller-in-apmode-stop.patch
 * 0115-brcmfmac-support-11ax-and-6G-band.patch
 * 0116-brcmfmac-fixes-invalid-channel-still-in-the-channel-.patch
 * 0117-non-upstream-Fix-lspci-not-enumerating-wifi-device-a.patch [x]
 * 0118-brcmfmac-support-signal-monitor-feature-for-wpa_supp.patch
 * 0119-brcmfmac-add-support-for-CYW55560-SDIO-chipset.patch
 * 0120-brcmfmac-Modified-Kconfig-help-format.patch
 * 0121-brcmfmac-Fix-incorrect-WARN_ON-causing-set_pmk-failu.patch
 * 0122-brcmfmac-report-cqm-rssi-event-based-on-rssi-change-.patch
 * 0123-brcmfmac-add-WPA3_AUTH_1X_SUITE_B_SHA384-related-sup.patch
 * 0124-non-upstream-Handle-the-6G-case-in-the-bw_cap-chansp.patch [x]
 * 0125-net-brcm80211-Fix-race-on-timer_add-in-wifi-driver.patch
 * 0126-brcmfmac-Remove-WARN_ON-while-no-6g-bw_cap.patch
 * 0127-brcmfmac-update-the-statically-defined-HE-MAC-PHY-Ca.patch
 * 0128-brcmfmac-fix-set_pmk-warning-message.patch
 * 0129-brcmfmac-update-BIP-setting-and-wsec_info-for-GMAC-a.patch
 * 0130-brcmfmac-send-roam-request-when-supplicant-triggers-.patch
 * 0131-brcmfmac-send-BCNLOST_MSG-event-on-beacon-loss-for-s.patch
 * 0132-brcmfmac-trying-to-get-GCMP-cap-before-doing-set-it.patch
 * 0133-brcmfmac-update-firmware-loading-name-for-CY5557x.patch
 * 0134-brcmfmac-use-SR-core-id-to-decide-SR-capability-for-.patch
 * 0135-brcmfmac-SAP-mode-parsing-sae_h2e-setting-from-beaco.patch
 * 0136-brcmfmac-add-sanity-check-for-potential-underflow-an.patch
 * 0137-brcmfmac-Fixing-vulnerability.patch
 * 0138-brcmfmac-Implementing-set_bitrate_mask-cfg80211-ops-.patch
 * 0139-brcmfmac-add-FT-PSK-roaming-offload-support.patch
 * 0140-brcmfmac-enable-6G-split-scanning-feature.patch
 * 0141-brcmfmac-set-HE-6GHz-capabilities-for-bring-up-SAP.patch
 * 0142-brcmfmac-add-interface-to-set-bsscolor-for-bring-up-.patch
 * 0143-non-upstream-add-IFX-vendor-OUI-file.patch [x]
 * 0144-non-upstream-adding-vendor_cmds-are-with-IFX_OUI.patch [x]
 * 0145-brcmfmac-introduce-a-module-parameter-to-disable-the.patch
 * 0146-brcmfmac-skip-6GHz-capab-registration-with-cfg80211-.patch
 * 0147-brcmfmac-set-HE-rate-only-if-HE-MCS-set-and-valid.patch
 * 0148-brcmfmac-remove-workaround-cause-the-FW-can-support-.patch
 * 0149-brcmfmac-ext_owe-supporting.patch
 * 0150-brcmfmac-Avoid-adding-two-sets-of-HE-Capab-and-Oper-.patch
 * 0151-non-upstream-Add-IFX-TWT-Offload-support.patch [x]
 * 0152-non-upstream-vendor-cmd-addition-for-wl-he-bsscolor.patch [x]
 * 0153-non-upstream-vendor-cmd-addition-for-wl-he-muedca_op.patch [x]
 * 0154-non-upstream-vendor-cmd-addition-for-wl-amsdu.patch [x]
 * 0155-non-upstream-vendor-cmd-addition-for-wl-ldpc_cap.patch [x]
 * 0156-non-upstream-Refine-TWT-code-for-checkpatch.patch [x]
 * 0157-cfg80211-fix-u8-overflow-in-cfg80211_update_notliste.patch
 * 0158-cfg80211-mac80211-reject-bad-MBSSID-elements.patch
 * 0159-cfg80211-fix-BSS-refcounting-bugs.patch
 * 0160-cfg80211-avoid-nontransmitted-BSS-list-corruption.patch
 * 0161-brcmfmac-Fix-potential-buffer-overflow-in-brcmf_fweh.patch
 * 0162-non-upstream-vendor-cmd-addition-for-wl-oce-enable.patch [x]
 * 0163-non-upstream-vendor-cmd-addition-for-wl-randmac.patch [x]
 * 0164-brcmfmac-compile-warning-fix.patch
 * 0165-brcmfmac-Fix-invalid-RAM-address-warning-for-PCIE-pl.patch
 * 0166-brcmfmac-Fix-dpp-very-low-tput-issue.patch
 * 0167-non-upstream-keep-IFX-license-header-for-non-upstrea.patch [x]
 * 0168-non-upstream-internal-sup-uses-join-command-to-send-.patch [x]
 * 0169-non-upstream-Supporting-IFX_vendor-commands-of-MBO.patch [x]
 * 0170-brcmfmac-Set-corresponding-cqm-event-handlers-based-.patch
 * 0171-non-upstream-isolate-power_save-off-and-mpc-0.patch [x]
 * 0172-brcmfmac-Add-NULL-checks-to-fix-multiple-NULL-pointe.patch
 * 0173-brcmfmac-fix-compiler-error.patch
 * 0174-non-upstream-supporting-giartrx-IFX-vendor-ID.patch [x]
 * 0175-wireless-brcmfmac-Use-netif_rx.patch
 * 0176-brcmfmac-replace-SDIO-function-number-with-definitio.patch
 * 0177-brcmfmac-move-SDIO-function-number-definition-to-sdi.patch
 * 0178-brcmfmac-Restore-channel-info.patch
 * 0179-brcmfmac-Avoid-adding-two-sets-of-HE-Capab-and-Oper-.patch
 * 0180-non-upstream-sdio-t-put-tuning.patch [x]
 * 0181-brcmfmac-get-chip-info-from-SDIOD-if-chip-common-spa.patch
 * 0182-non-upstream-vendor-cmd-addition-for-wpa_cli-wnm_max.patch [x]
 * 0183-brcm80211-Resolve-skb-alloc-failures-in-FMAC.patch
 * 0184-non-upstream-sdio-t-put-tuning.patch [x]
 * 0185-brcmfmac-Fix-a-NULL-pointer-dereference.patch
 * 0186-brcmfmac-add-protection-for-PCIe-Read-Write-out-of-b.patch
 * 0187-brcmfmac-Added-DSCP-to-WMM-UP-mapping.patch
 * 0188-brcmfmac-fix-mac-address-is-not-assigned-for-iovar-B.patch
 * 0189-non-upstream-fixing-compile-error-on-kernel-5.9-onwa.patch [x]
 * 0190-brcmfmac-fix-for-guard-interval-for-iw-set-bitrates.patch
 * 0191-brcmfmac-Add-support-for-ethtool-packet-statistics.patch
 * 0192-brcmfmac-Add-55500-chip-support.patch
 * 0193-brcmfmac-SDIO-Rev31-changes-in-rmmod-sequence.patch
 * 0194-brcmfmac-Wait-for-bootloader-ready-before-doing-back.patch
 * 0195-brcmfmac-prevent-double-free-on-hardware-reset.patch
 * 0196-brcmfmac-Update-D2H-Validation-Done-Timeout.patch
 * 0197-brcmfmac-SR-in-not-getting-enabled-in-H1.patch
 * 0198-brcmfmac-set-up-wrong-status-when-use-internal-suppl.patch
 * 0199-brcmfmac-TWT-Add-a-new-feature-source-header-file-fo.patch
 * 0200-brcmfmac-TWT-Add-support-to-handle-the-async-TWT-eve.patch
 * 0201-brcmfmac-TWT-create-a-debugfs-file-to-expose-the-TWT.patch
 * 0202-brcmfmac-Update-IFX-NL80211-Vendor-source-and-header.patch
 * 0203-brcmfmac-add-protection-for-firmware-doesn-t-have-ex.patch
 * 0204-brcmfmac-fix-compiler-error-when-using-vanilla-kerne.patch
 * 0205-non-upstream-to-prevent-rx-interrupt-comes-too-early.patch [x]
 * 0206-brcmfmac-Send-CSA-to-supplicant-on-channel-change.patch
 * 0207-brcmfmac-extowe_ap-mode-supporting.patch
 * 0208-brcmfmac-resort-data-structure-of-owe_info.patch
 * 0209-brcmfmac-TWT-fixed-feature-check.patch
 * 0210-brcmfmac-External-roam-time-enhancements.patch
 * 0211-brcmfmac-fixing-compile-warning.patch
 * 0212-brcmfmac-TWT-Handle-unsolicited-setup-accept-and-sol.patch
 * 0213-brcmfmac-TWT-use-Dialog-Token-as-unique-identifier-t.patch
 * 0214-brcmfmac-TWT-Update-teardown-state-while-handling-Te.patch
 * 0215-brcmfmac-TWT-Handle-timeout-of-Setup-and-Teardown-ev.patch
 * 0216-brcmfmac-TWT-rephrase-print-statements-with-addition.patch
 * 0217-brcmfmac-offload-add-configuration-infrastructure-su.patch
 * 0218-brcmfmac-offload-clean-add-all-entries-in-ICMP-ND-fo.patch
 * 0219-brcmfmac-avoid-unnecessary-WL-Down-UP-while-setting-.patch
 * 0220-non-upstream-update-sae_password-for-potential-roami.patch [x]
 * 0221-brcmfmac-offload-update-the-brcmf_configure_arp_nd_o.patch
 * 0222-brcmfmac-Fix-DUT-is-vulnerable-to-key-reinstallation.patch
 * 0223-brcmfmac-Support-for-WPA3-FT-SAE-roam-offload.patch
 * 0224-brcmfmac-TWT-cleanup-stale-session-entries-after-rec.patch
 * 0225-brcmfmac-Fix-kernel-crash-while-updating-tx-statisti.patch
 * 0226-brcmfmac-avoid-memory-use-after-free-in-the-escan-ti.patch
 * 0227-non-upstream-add-command-to-show-module-parameter.patch [x]
 * 0228-brcmfmac-support-43022-Cypress-Vendor-and-Device-ID.patch
 * 0229-brcmfmac-Chip-id-changes-for-43022.patch
 * 0230-brcmfmac-Move-shared-console-address-location.patch
 * 0231-brcmfmac-enable-support-for-split-scan-to-optimize-t.patch
 * 0232-brcmfmac-kso-sequence-sleep-delay-enhancement.patch
 * 0233-brcmfmac-Avoid-realloc-resources-on-DS1-exit-in-fw-d.patch
 * 0234-brcmfmac-PCIe-RX-throughput-improvement.patch
 * 0235-brcmfmac-Increase-the-kso_sequence-bail-out-timer.patch
 * 0236-non-upstream-btsdio-add-ifx-bt-shared-sdio-file.patch [x]
 * 0237-non-upstream-fixing-the-last-hostapd_cli-disabled-in.patch [x]
 * 0238-brcmfmac-fixing-mbss-iovar-setting-for-multiple-BSS-.patch
 * 0239-non-upstream-new-value-for-roamoff-for-report-differ.patch [x]
 * 0240-brcmfmac-Support-idleclock-feature-for-43012-43022-c.patch
 * 0241-non-upstream-btsdio-enable-export-api-to-r-w-F3-one-.patch [x]
 * 0242-non-upstream-btsdio-enable-export-api-for-F3-receivi.patch [x]
 * 0243-non-upstream-btsdio-attach-init-deinit.patch [x]
 * 0244-non-upstream-btsdio-check-rx-interrupt-before-get-rx.patch [x]
 * 0245-non-upstream-btsdio-enable-export-api-for-F3-transfe.patch [x]
 * 0246-non-upstream-btsdio-support-export-api-to-set-block-.patch [x]
 * 0247-non-upstream-btsdio-claim-function-3-in-band-irq.patch [x]
 * 0248-non-upstream-btsdio-reset-bt-in-remove-flow-when-bt-.patch [x]
 * 0249-non-upstream-btsdio-add-command-to-show-bt-shared-sd.patch [x]
 * 0250-brcmfmac-DS2-udp-tx-crash-fix.patch
 * 0251-brcmfmac-OOB-irq-support-on-43022-DS2.patch
 * 0252-brcmfmac-pcie-INTMASK-address-is-another-address-fro.patch
 * 0253-brcmfmac-fix-wrong-NULL-check-in-msgbuf_rx.patch
 * 0254-non-upstream-btsdio-support-43012-43022.patch [x]
 * 0255-brcmfmac-Bootloader-host-handshake-implementation.patch
 * 0256-brcmfmac-Avoid-socram-access-in-secure-mode.patch
 * 0257-brcmfmac-Support-secure-and-non-secure-code-flow.patch
 * 0258-brcmfmac-Bring-up-DS1-for-43022-DM-chip.patch
 * 0259-brcmfmac-do-not-access-D11-SHM-and-PMU-registers-for.patch
 * 0260-brcmfmac-fixes-for-FW-redownload-after-DS1-2-exit.patch
 * 0261-brcmfmac-New-rmmod-seq-for-43022-secure-mode.patch
 * 0262-brcmfmac-Change-bus-width-independent-of-sdio_idlecl.patch
 * 0263-brcmfmac-Remove-chip-id-check-from-kso-0-bail-out-lo.patch
 * 0264-brcmfmac-fix-wrong-FW-extension-problem-for-secure-c.patch
 * 0265-brcmfmac-separate-43022-sdio-download-function-from-.patch
 * 0266-nl80211-Sync-with-wireless-next-2023-10-26-include-u.patch
 * 0267-non-upstream-nl80211-bring-back-IFX-nl80211.h-change.patch [x]
 * 0268-brcmfmac-set-authorized-flag-in-CONNECT-event-for-al.patch
 * 0269-nl80211-Add-support-to-set-AP-settings-flags-with-si.patch
 * 0270-brcmfmac-fix-compiler-warning-on-kernel-v4.12.patch
 * 0271-brcmfmac-fix-warning-error-when-enable-PCIE_BARWIN_S.patch
 * 0272-brcmfmac-Add-new-survey-dump-feature.patch
 * 0273-brcmfmac-update-local-pmklist-while-process-auth_sta.patch
 * 0274-brcmfmac-fix-mmc-tuning-failed.patch
 * 0275-non-upstream-check-and-set-default-fcmode-of-the-chi.patch [x]
 * 0276-brcmfmac-add-protection-for-not-calling-cfg80211_ch_.patch
 * 0277-brcmfmac-get-wdev-from-the-event-reporting-ifp.patch
 * 0278-non-upstream-vendor-cmd-addition-for-replay-counter.patch [x]
 * 0279-non-upstream-btsdio-forward-device-id-to-bt-driver.patch [x]
 * 0280-brcmfmac-skip-bss-update-when-NULL-mac-received-for-.patch
 * 0281-brcmfmac-Adding-set-and-remove-F3-device.patch
 * 0282-brcmfmac-Fix-KERNEL-WARNING-due-to-invalid-chspec.patch
 * 0283-brcmfmac-Check-bus-sleep-state-in-isr.patch
 * 0284-brcmfmac-resetting-sb-window-address.patch
 * 0285-brcmfmac-SWLINUX-4018-Resolves-compilation-err.patch
 * 0286-non-upstream-Increase-delay-in-kso-sequence.patch [x]
 * 0287-brcmfmac-OOB-crash-Fix-on-iMX-platform.patch
 * 0288-non-upstream-fix-func3-compile-error.patch [x]
 * 0289-non-upstream-btsdio-add-DM-device-ID.patch [x]
 * 0290-wifi-brcmfmac-Fix-use-after-free-bug-in-brcmf_cfg802.patch
 * 0291-non-upstream-provide-the-iw-command-to-set-get-value.patch [x]
 * 0292-non-upstream-vendor-cmds-string-infrastructure-with-.patch [x]
 * 0293-non-upstream-mkeep_alive-and-tko-string-vendor-cmds.patch [x]
 * 0294-brcmfmac-Add-module_param-to-set-idle_time_zero.patch

Note: [*] is the upstream tag containing the patch
      [-] means under upstream review
      [x] means no plan to upstream


Hostap Patch List
-----------------
 * 0001-wpa_supplicant-Support-4-way-handshake-offload-for-F.patch
 * 0002-wpa_supplicant-Notify-Neighbor-Report-for-driver-tri.patch
 * 0003-nl80211-Report-connection-authorized-in-EVENT_ASSOC.patch
 * 0004-wpa_supplicant-Add-PMKSA-cache-for-802.1X-4-way-hand.patch
 * 0005-OpenSSL-Fix-build-with-OpenSSL-1.0.1.patch
 * 0006-DPP-Do-more-condition-test-for-AKM-type-DPP-offload.patch
 * 0007-non-upstream-defconfig_base-Add-Infineon-default-con.patch [x]
 * 0008-Fix-to-check-Invalid-GTK-IE-length-in-M3-at-STA.patch
 * 0009-Add-CONFIG_WPA3_SAE_AUTH_EARLY_SET-flags-and-codes.patch
 * 0010-wpa_supplicant-Support-WPA_KEY_MGMT_FT-for-eapol-off.patch
 * 0011-wpa_supplicant-suppress-deauth-for-PMKSA-caching-dis.patch
 * 0012-Fix-for-PMK-expiration-issue-through-supplicant.patch
 * 0013-SAE-Drop-PMKSA-cache-after-receiving-specific-deauth.patch
 * 0014-Avoid-deauthenticating-STA-if-the-reason-for-freeing.patch
 * 0015-wpa_supplicant-support-bgscan.patch
 * 0016-non-upstream-wl-cmd-create-interface-to-support-driv.patch [x]
 * 0017-non-upstream-wl-cmd-create-wl_do_cmd-as-an-entry-doi.patch [x]
 * 0018-non-upstream-wl-cmd-create-ops-table-to-do-wl-comman.patch [x]
 * 0019-non-upstream-wl-cmd-add-more-compile-flag.patch
 * 0020-Fix-dpp-config-parameter-setting.patch
 * 0021-DPP-Resolving-failure-of-dpp-configurator-exchange-f.patch
 * 0022-Enabling-SUITEB192-and-SUITEB-compile-options.patch
 * 0023-DPP-Enabling-CLI_EDIT-option-for-enrollee-plus-respo.patch
 * 0024-non-upstream-SAE-disconnect-after-PMKSA-cache-expire.patch [x]
 * 0025-Add-support-for-beacon-loss-roaming.patch
 * 0026-wpa_supplicant-Set-PMKSA-to-driver-while-key-mgmt-is.patch
 * 0027-Enabling-OWE-in-wpa_supplicant.patch
 * 0028-Add-link-loss-timer-on-beacon-loss.patch
 * 0029-TWT-Add-support-to-offload-TWT-Session-setup-handlin.patch
 * 0030-nl80211-Introduce-new-Vendor-header-file-for-driver-.patch
 * 0031-fixup-nl80211-Introduce-new-Vendor-header-file-for-d.patch
 * 0032-TWT-Use-IFX-Vendor-path-to-offload-TWT-session-setup.patch
 * 0033-TWT-Use-IFX-Vendor-path-to-offload-TWT-session-Teard.patch
 * 0034-TWT-Add-support-to-configure-TWT-of-a-session-using-.patch
 * 0035-Fix-for-station-sending-open-auth-instead-of-SAE-aut.patch
 * 0036-Fix-associating-failed-when-PMK-lifetime-is-set-to-1.patch
 * 0037-non-upstream-p2p_add_group-command-unification.patch [x]
 * 0038-non-upstream-MBO-wpa_cli-mbo-command-by-IFX-vendorID.patch [x]
 * 0039-Enabling-TLS-v1.3-by-default.patch
 * 0040-Disable-4-way-handshake-offload-for-DPP.patch
 * 0041-non-upstream-WNM-wpa_cli-wnm_maxilde-command-by-IFX-.patch [x]
 * 0042-OWE-AP-enable-OWE-compile-option-for-hostapd-executi.patch
 * 0043-DPP2.0-support-DPP2.0-and-add-pfs-init-flow-on-EVENT.patch
 * 0044-non-upstream-Prevent-invalid-akm-key-mgmt-when-MFP-r.patch [x]
 * 0045-Reset-authentication-and-encryption-parameters-while.patch
 * 0046-Reset-pmk-while-handling-roam-event.patch
 * 0047-brcmfmac-add-a-configurable-link_loss-parameter-for-.patch
 * 0048-DPP-fix-for-akm-sae-and-add-dpp_reconfig-command-to-.patch
 * 0049-DPP-enable-CONFIG_DPP3-flag.patch
 * 0050-MLD-STA-protect-connect-CMD-attribute-MLO-support-un.patch
 * 0051-nl8211-Set-NL80211_WPA_VERSION_2-vs-_3-based-on-AKM-.patch
 * 0052-bgscan-wpa_supplicant-segment-fault-when-do-simple-b.patch
 * 0053-hostapd-calling-driver-to-remove-pmkid-while-pmk-cac.patch
 * 0054-non-upstream-Check-supported-Replay-Counters-through.patch [x]
 * 0055-non-upstream-WNM-fix-wnm_maxilde-coredump-and-get-em.patch [x]
 * 0056-non-upstream-temporarily-disable-the-compiler-optimi.patch
 * 0057-enable-ACS-compile-option-by-default.patch
Note: [*] is the upstream tag containing the patch
      [x] means no plan to upstream
