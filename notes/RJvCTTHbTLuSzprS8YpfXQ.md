---
title: Using Internet in NIA Global Center
---
# Using Internet in NIA Global Center

## VPN

One solution is to use ProtonVPN:

1. Install ProtonVPN from https://protonvpn.com/ and register. It's free.
2. Start the application.  In Settings, go to "Connection" tab, and in "Protocol" choose "OpenVPN (TCP)".
   ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_3e5e4309b28df127cb5dbe07cb65460a.jpg)
3. If you are on Linux, open a terminal and run `protonvpn-cli config -p tcp`
3. Connect to one of the VPN servers.
4. Try git pull or ssh to your server. It should work.


> [name=yutin] Outline VPN https://getoutline.org/ works but you need to create your own server

> [name=pm5] ProtonVPN https://protonvpn.com/ works on the phone but not on computers.
> > ~~Jerry: It's not stable on MacBook Pro. I can connect to Japan server but it keeps disconnect and connect.~~ Please see the top #VPN block.
> > 
> > pm5: Got working on Linux computer with OpenVPN + alternative routing https://protonvpn.com/blog/mac-ios-vpn-bypass-censorship/ The config I'm having:

```
Proton VPN User Settings
---------------------------
Default Protocol:       OpenVPN (TCP)
Kill Switch:            Off
Netshield:              Ads and malware
DNS:                    Automatic
Alternative Routing:    Enabled
VPN Accelerator:        Enabled
Moderate NAT:           Off
Non Standard Ports:     Off
```

> [name=ronnywang] It seems only 80, 443, 8443 are allowed. (I add port 8443 on my sshd and I can connect to my server now.)

> [name=RS] If your school/organization has SSL VPN (Fortinet, Pulse Secure), you could also use them.
Just tried and it works! :ok_hand:

## GitHub

One solution is to use it through VPN (ProtonVPN in OpenVPN TCP mode, or SSL VPN of your choice).

Another option is to pull over port 443: `git clone ssh://git@ssh.github.com:443/yourname/yourrepo`

> [name=ronnywang] port 22 is not allowed here. If you want git pull from github over ssh. you can use “git clone ssh://git@ssh.github.com:443/yourname/yourrepo”

> [name=pm5] Regular GitHub pull works when using OpenVPN TCP mode in ProtonVPN XD

> [name=pm5] btw https://codeberg.org/ is not blocked XD
