

開啟防火牆
	icmp
	netsh advfirewall firewall add rule name="ICMP Allow incoming V4 echo request" protocol=icmpv4:8,any dir=in action=allow
	遠端桌面
	遠端管理
	防火牆遠端管理
