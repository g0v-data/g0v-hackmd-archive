```
Frame 77340 (84 bytes on wire, 84 bytes captured)
    Arrival Time: Feb 25, 2011 15:38:14.291033000
    [Time delta from previous captured frame: 0.000063000 seconds]
    [Time delta from previous displayed frame: 0.000000000 seconds]
    [Time since reference or first frame: 24908.386747000 seconds]
    Frame Number: 77340
    Frame Length: 84 bytes
    Capture Length: 84 bytes
    [Frame is marked: False]
    [Protocols in frame: eth:ip:udp:dns]
Ethernet II, Src: Supermic_7f:85:1c (00:30:48:7f:85:1c), Dst: Cisco_40:44:00 (00:1f:27:40:44:00)
    Destination: Cisco_40:44:00 (00:1f:27:40:44:00)
        Address: Cisco_40:44:00 (00:1f:27:40:44:00)
        .... ...0 .... .... .... .... = IG bit: Individual address (unicast)
        .... ..0. .... .... .... .... = LG bit: Globally unique address (factory default)
    Source: Supermic_7f:85:1c (00:30:48:7f:85:1c)
        Address: Supermic_7f:85:1c (00:30:48:7f:85:1c)
        .... ...0 .... .... .... .... = IG bit: Individual address (unicast)
        .... ..0. .... .... .... .... = LG bit: Globally unique address (factory default)
    Type: IP (0x0800)
Internet Protocol, Src: 10.16.183.86 (10.16.183.86), Dst: 10.0.80.11 (10.0.80.11)
    Version: 4
    Header length: 20 bytes
    Differentiated Services Field: 0x00 (DSCP 0x00: Default; ECN: 0x00)
        0000 00.. = Differentiated Services Codepoint: Default (0x00)
        .... ..0. = ECN-Capable Transport (ECT): 0
        .... ...0 = ECN-CE: 0
    Total Length: 70
    Identification: 0x9fcb (40907)
    Flags: 0x04 (Don't Fragment)
        0... = Reserved bit: Not set
        .1.. = Don't fragment: Set
        ..0. = More fragments: Not set
    Fragment offset: 0
    Time to live: 64
    Protocol: UDP (0x11)
    Header checksum: 0x7f6a [correct]
        [Good: True]
        [Bad : False]
    Source: 10.16.183.86 (10.16.183.86)
    Destination: 10.0.80.11 (10.0.80.11)
User Datagram Protocol, Src Port: 46913 (46913), Dst Port: domain (53)
    Source port: 46913 (46913)
    Destination port: domain (53)
    Length: 50
    Checksum: 0x1bb5 [incorrect, should be 0xd5d2 (maybe caused by "UDP checksum offload"?)]
        [Good Checksum: False]
        [Bad Checksum: True]
Domain Name System (query)
    Transaction ID: 0x08cd
    Flags: 0x0100 (Standard query)
        0... .... .... .... = Response: Message is a query
        .000 0... .... .... = Opcode: Standard query (0)
        .... ..0. .... .... = Truncated: Message is not truncated
        .... ...1 .... .... = Recursion desired: Do query recursively
        .... .... .0.. .... = Z: reserved (0)
        .... .... ...0 .... = Non-authenticated data OK: Non-authenticated data is unacceptable
    Questions: 1
    Answer RRs: 0
    Authority RRs: 0
    Additional RRs: 0
    Queries
        test.test.com: type A, class IN
            Name: test.test.com
            Type: A (Host address)
            Class: IN (0x0001)

Frame 77389 (234 bytes on wire, 234 bytes captured)
    Arrival Time: Feb 25, 2011 15:38:27.233395000
    [Time delta from previous captured frame: 0.000007000 seconds]
    [Time delta from previous displayed frame: 0.000000000 seconds]
    [Time since reference or first frame: 24921.329109000 seconds]
    Frame Number: 77389
    Frame Length: 234 bytes
    Capture Length: 234 bytes
    [Frame is marked: False]
    [Protocols in frame: eth:ip:udp:dns]
Ethernet II, Src: Cisco_40:44:00 (00:1f:27:40:44:00), Dst: Supermic_7f:85:1c (00:30:48:7f:85:1c)
    Destination: Supermic_7f:85:1c (00:30:48:7f:85:1c)
        Address: Supermic_7f:85:1c (00:30:48:7f:85:1c)
        .... ...0 .... .... .... .... = IG bit: Individual address (unicast)
        .... ..0. .... .... .... .... = LG bit: Globally unique address (factory default)
    Source: Cisco_40:44:00 (00:1f:27:40:44:00)
        Address: Cisco_40:44:00 (00:1f:27:40:44:00)
        .... ...0 .... .... .... .... = IG bit: Individual address (unicast)
        .... ..0. .... .... .... .... = LG bit: Globally unique address (factory default)
    Type: IP (0x0800)
Internet Protocol, Src: 10.0.80.11 (10.0.80.11), Dst: 10.16.183.86 (10.16.183.86)
    Version: 4
    Header length: 20 bytes
    Differentiated Services Field: 0x00 (DSCP 0x00: Default; ECN: 0x00)
        0000 00.. = Differentiated Services Codepoint: Default (0x00)
        .... ..0. = ECN-Capable Transport (ECT): 0
        .... ...0 = ECN-CE: 0
    Total Length: 220
    Identification: 0x46e2 (18146)
    Flags: 0x00
        0... = Reserved bit: Not set
        .0.. = Don't fragment: Not set
        ..0. = More fragments: Not set
    Fragment offset: 0
    Time to live: 62
    Protocol: UDP (0x11)
    Header checksum: 0x19be [correct]
        [Good: True]
        [Bad : False]
    Source: 10.0.80.11 (10.0.80.11)
    Destination: 10.16.183.86 (10.16.183.86)
User Datagram Protocol, Src Port: domain (53), Dst Port: 46913 (46913)
    Source port: domain (53)
    Destination port: 46913 (46913)
    Length: 200
    Checksum: 0x29d4 [correct]
        [Good Checksum: True]
        [Bad Checksum: False]
Domain Name System (response)
    [Request In: 77340]
    [Time: 12.942362000 seconds]
    Transaction ID: 0x08cd
    Flags: 0x8180 (Standard query response, No error)
        1... .... .... .... = Response: Message is a response
        .000 0... .... .... = Opcode: Standard query (0)
        .... .0.. .... .... = Authoritative: Server is not an authority for domain
        .... ..0. .... .... = Truncated: Message is not truncated
        .... ...1 .... .... = Recursion desired: Do query recursively
        .... .... 1... .... = Recursion available: Server can do recursive queries
        .... .... .0.. .... = Z: reserved (0)
        .... .... ..0. .... = Answer authenticated: Answer/authority portion was not authenticated by the server
        .... .... .... 0000 = Reply code: No error (0)
    Questions: 1
    Answer RRs: 1
    Authority RRs: 2
    Additional RRs: 4
    Queries
        test.test.com: type A, class IN
            Name: test.test.com
            Type: A (Host address)
            Class: IN (0x0001)
    Answers
        test.test.com: type A, class IN, addr 10.40.80.36
            Name: test.test.com
            Type: A (Host address)
            Class: IN (0x0001)
            Time to live: 15 minutes
            Data length: 4
            Addr: 10.40.80.36
    Authoritative nameservers
        test.com: type NS, class IN, ns ns1.softlayer.com
            Name: test.com
            Type: NS (Authoritative name server)
            Class: IN (0x0001)
            Time to live: 19 hours, 56 minutes, 38 seconds
            Data length: 16
            Name server: ns1.softlayer.com
        test.com: type NS, class IN, ns ns2.softlayer.com
            Name: test.com
            Type: NS (Authoritative name server)
            Class: IN (0x0001)
            Time to live: 19 hours, 56 minutes, 38 seconds
            Data length: 6
            Name server: ns2.softlayer.com
    Additional records
        ns1.softlayer.com: type A, class IN, addr 67.228.254.4
            Name: ns1.softlayer.com
            Type: A (Host address)
            Class: IN (0x0001)
            Time to live: 19 hours, 55 minutes, 26 seconds
            Data length: 4
            Addr: 67.228.254.4
        ns1.softlayer.com: type AAAA, class IN, addr 2607:f0d0:0:f:1::1
            Name: ns1.softlayer.com
            Type: AAAA (IPv6 address)
            Class: IN (0x0001)
            Time to live: 22 hours, 1 minute, 35 seconds
            Data length: 16
            Addr: 2607:f0d0:0:f:1::1
        ns2.softlayer.com: type A, class IN, addr 67.228.255.5
            Name: ns2.softlayer.com
            Type: A (Host address)
            Class: IN (0x0001)
            Time to live: 20 hours, 40 seconds
            Data length: 4
            Addr: 67.228.255.5
        ns2.softlayer.com: type AAAA, class IN, addr 2607:f0d0:0:f:2::1
            Name: ns2.softlayer.com
            Type: AAAA (IPv6 address)
            Class: IN (0x0001)
            Time to live: 20 hours, 18 minutes, 33 seconds
            Data length: 16
            Addr: 2607:f0d0:0:f:2::1


Frame 77390 (262 bytes on wire, 262 bytes captured)
    Arrival Time: Feb 25, 2011 15:38:27.233403000
    [Time delta from previous captured frame: 0.000008000 seconds]
    [Time delta from previous displayed frame: 0.000008000 seconds]
    [Time since reference or first frame: 24921.329117000 seconds]
    Frame Number: 77390
    Frame Length: 262 bytes
    Capture Length: 262 bytes
    [Frame is marked: False]
    [Protocols in frame: eth:ip:icmp:ip:udp:dns]
Ethernet II, Src: Supermic_7f:85:1c (00:30:48:7f:85:1c), Dst: Cisco_40:44:00 (00:1f:27:40:44:00)
    Destination: Cisco_40:44:00 (00:1f:27:40:44:00)
        Address: Cisco_40:44:00 (00:1f:27:40:44:00)
        .... ...0 .... .... .... .... = IG bit: Individual address (unicast)
        .... ..0. .... .... .... .... = LG bit: Globally unique address (factory default)
    Source: Supermic_7f:85:1c (00:30:48:7f:85:1c)
        Address: Supermic_7f:85:1c (00:30:48:7f:85:1c)
        .... ...0 .... .... .... .... = IG bit: Individual address (unicast)
        .... ..0. .... .... .... .... = LG bit: Globally unique address (factory default)
    Type: IP (0x0800)
Internet Protocol, Src: 10.16.183.86 (10.16.183.86), Dst: 10.0.80.11 (10.0.80.11)
    Version: 4
    Header length: 20 bytes
    Differentiated Services Field: 0xc0 (DSCP 0x30: Class Selector 6; ECN: 0x00)
        1100 00.. = Differentiated Services Codepoint: Class Selector 6 (0x30)
        .... ..0. = ECN-Capable Transport (ECT): 0
        .... ...0 = ECN-CE: 0
    Total Length: 248
    Identification: 0x65e8 (26088)
    Flags: 0x00
        0... = Reserved bit: Not set
        .0.. = Don't fragment: Not set
        ..0. = More fragments: Not set
    Fragment offset: 0
    Time to live: 64
    Protocol: ICMP (0x01)
    Header checksum: 0xf7eb [correct]
        [Good: True]
        [Bad : False]
    Source: 10.16.183.86 (10.16.183.86)
    Destination: 10.0.80.11 (10.0.80.11)	
Internet Control Message Protocol
    Type: 3 (Destination unreachable)
    Code: 3 (Port unreachable)
    Checksum: 0x1948 [correct]
    Internet Protocol, Src: 10.0.80.11 (10.0.80.11), Dst: 10.16.183.86 (10.16.183.86)
        Version: 4
        Header length: 20 bytes
        Differentiated Services Field: 0x00 (DSCP 0x00: Default; ECN: 0x00)
            0000 00.. = Differentiated Services Codepoint: Default (0x00)
            .... ..0. = ECN-Capable Transport (ECT): 0
            .... ...0 = ECN-CE: 0
        Total Length: 220
        Identification: 0x46e2 (18146)
        Flags: 0x00
            0... = Reserved bit: Not set
            .0.. = Don't fragment: Not set
            ..0. = More fragments: Not set
        Fragment offset: 0
        Time to live: 62
        Protocol: UDP (0x11)
        Header checksum: 0x19be [correct]
            [Good: True]
            [Bad : False]
        Source: 10.0.80.11 (10.0.80.11)
        Destination: 10.16.183.86 (10.16.183.86)
    User Datagram Protocol, Src Port: domain (53), Dst Port: 46913 (46913)
        Source port: domain (53)
        Destination port: 46913 (46913)
        Length: 200
        Checksum: 0x29d4 [correct]
            [Good Checksum: True]
            [Bad Checksum: False]
    Domain Name System (response)
        [Request In: 77340]
        [Time: 12.942370000 seconds]
        Transaction ID: 0x08cd
        Flags: 0x8180 (Standard query response, No error)
            1... .... .... .... = Response: Message is a response
            .000 0... .... .... = Opcode: Standard query (0)
            .... .0.. .... .... = Authoritative: Server is not an authority for domain
            .... ..0. .... .... = Truncated: Message is not truncated
            .... ...1 .... .... = Recursion desired: Do query recursively
            .... .... 1... .... = Recursion available: Server can do recursive queries
            .... .... .0.. .... = Z: reserved (0)
            .... .... ..0. .... = Answer authenticated: Answer/authority portion was not authenticated by the server
            .... .... .... 0000 = Reply code: No error (0)
        Questions: 1
        Answer RRs: 1
        Authority RRs: 2
        Additional RRs: 4
        Queries
            test.test.com: type A, class IN
                Name: test.test.com
                Type: A (Host address)
                Class: IN (0x0001)
        Answers
            test.test.com: type A, class IN, addr 10.40.80.36
                Name: test.test.com
                Type: A (Host address)
                Class: IN (0x0001)
                Time to live: 15 minutes
                Data length: 4
                Addr: 10.40.80.36
        Authoritative nameservers
            test.com: type NS, class IN, ns ns1.softlayer.com
                Name: test.com
                Type: NS (Authoritative name server)
                Class: IN (0x0001)
                Time to live: 19 hours, 56 minutes, 38 seconds
                Data length: 16
                Name server: ns1.softlayer.com
            test.com: type NS, class IN, ns ns2.softlayer.com
                Name: test.com
                Type: NS (Authoritative name server)
                Class: IN (0x0001)
                Time to live: 19 hours, 56 minutes, 38 seconds
                Data length: 6
                Name server: ns2.softlayer.com
        Additional records
            ns1.softlayer.com: type A, class IN, addr 67.228.254.4
                Name: ns1.softlayer.com
                Type: A (Host address)
                Class: IN (0x0001)
                Time to live: 19 hours, 55 minutes, 26 seconds
                Data length: 4
                Addr: 67.228.254.4
            ns1.softlayer.com: type AAAA, class IN, addr 2607:f0d0:0:f:1::1
                Name: ns1.softlayer.com
                Type: AAAA (IPv6 address)
                Class: IN (0x0001)
                Time to live: 22 hours, 1 minute, 35 seconds
                Data length: 16
                Addr: 2607:f0d0:0:f:1::1
            ns2.softlayer.com: type A, class IN, addr 67.228.255.5
                Name: ns2.softlayer.com
                Type: A (Host address)
                Class: IN (0x0001)
                Time to live: 20 hours, 40 seconds
                Data length: 4
                Addr: 67.228.255.5
            ns2.softlayer.com: type AAAA, class IN, addr 2607:f0d0:0:f:2::1
                Name: ns2.softlayer.com
                Type: AAAA (IPv6 address)
                Class: IN (0x0001)
                Time to live: 20 hours, 18 minutes, 33 seconds
                Data length: 16
                Addr: 2607:f0d0:0:f:2::1

```
