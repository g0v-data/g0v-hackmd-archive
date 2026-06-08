---
title: roundtable_ discussion on Off-the-grid network 
tags: summit2026, program, programming, summit, 議程
---
# roundtable: discussion on Off-the-grid network 

> edit welcome [name=paulpengtw]

# mentality
- what will happen when most of the network capacity are gone
    - some speculation: nothing connect to the internet will work

# what should we prepare to get islander interconnected within the island

## case study
- [dComms working in Ukraine](https://drive.google.com/file/d/1Kf45_w129YS3GOH7H_hPnFn-o1cOOsyC/view)

## two aspects
- user side
- server side
    - Network Time Protocol server
    - TLS cert
        - TWCA might midigate the issue
    - ccTLD (.tw)
    - DNS resolvers
    - CDN edges
    - Package mirrors / registries: security patches may not be available when global internet is gone, attackers may exploit this
    - auth
        - single sign on (e.g. google, line, facebook)
    - recaptcha
    - mobile push notifications 
    - public cloud 
    - security update 
- Can ActivityPub help? (from the perspective of g0v.social admin)
    - ![](https://g0v.hackmd.io/_uploads/r1RwkQNZze.png)
    - multiple layers act as foundation: DNS, physical cables, etc
- are activitypub or matrix depend on dns
    - yes
    - domains that are not .tw based would not be resolved when undersea cable are severed.
        - e.g. g0v.social
        - neet to talk with TWNIC people for record expiry
    - let's encrypt let people have CA on ip address
    - maybe use a failover on dns resolver that is somehow controlled by gover't(e.g. HINET)
- Network environment in Ukraine under war
    - Internet may be down for days during shelling
    - Internet may be (forced) routed through Russia
- place the server inside the island or outside?
    - when the outage happen, is that ideal for us to put the server inside the warzone?
    - depend on the threat model and what's the hypothesis
    - dComms service distribution
        - instances around the city
        - each is localized, citizens signup within city
        - each city got their own instance
        - based on mesh vpn tech
            - like between Kiev and Kherson, since ap doesn't do routing
            - lighthouse
            - [yggdrasil network](https://yggdrasil-network.github.io/)
            - tinc
- city-wise communication seems feasible; but for people hosting services it's another problem to solve
- connection between two city is served
    - how to reroute: be creative, utilize as much resource as possible (e.g. computer center in university)
- what's the content people is posting on dComm services?
    - chatting
    - family posts
    - alert channels about bombing info
- recently installing PeerTube, contents:
    - tech tuturials
    - politicial contents
- Impression of using Matrix: slow, huge in size, has that changed?
    - It depends
    - server of matrix: maybe they resolved the issue if you run on a newer machine
    - is IRC/XMPP🕊️ a better alternative to Matrix?
        - Matrix's UX is superior to end-users
        - and they got video calling
- human organization on maintaining the service
    - coops/company/org ?
- trust of service deployer is everything
- is content moderation an issue
- [simplex chat](https://simplex.chat/)
    - another signal alternative
- is e2ee matter under network outage?
    - what if the server got control under PLA?
    - "adversarial hosting" with full disk encrytion
    - boot to boot encryption with yubikey

## wifi based intranet
- cost to each device is way too high
- the range between two access point (based on ARDEN, Amateur Radio Emergency Data Network) are not good enough
- even solution like meshtastic for end user is not that user friendly
- a tripod / dish / wifi access point each will be suffice for setting up a wifi intranet AP
- case [NYCMesh](https://www.nycmesh.net/)
- 

## what if certain city lost the connection to upstream service
- just call or text its syssadmin
- meshvpn access or reroute/ starlink
- the whole things is to figure out to contact someone near the server keyboard and get 2nd 

## Are datacenters targeted by the enemy?

- Ukraine uses sattlelite communictions early on, thus there is no datacenter to attack

## drill/test, but what are the test items

