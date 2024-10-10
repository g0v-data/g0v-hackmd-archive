

1. 針對陸軍司令部的WAF日誌查察1600-1800前10大攻擊手法
AzureDiagnostics
| where Category == "FrontDoorWebApplicationFirewallLog" and ( host_s == "army.mnd.gov.tw" or host_s == "army-mnd-gov-tw-01-dwajdzgbf0ckafft.a01.azurefd.net" )
| where TimeGenerated between (datetime(2024-10-01T08:00:00Z) .. datetime(2024-10-01T10:00:00Z))
| summarize count () by ruleName_s
| top 10 by count_



