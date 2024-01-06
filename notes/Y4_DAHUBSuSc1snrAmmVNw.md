---
title: "比較保險的網路架構"
tags: 零時的學習不能等,網路服務,hackpad
---

# 比較保險的網路架構

> [點此觀看原始內容](https://g0v.hackpad.tw/EaWrGiHZgeu)


- 最基本的設置, 一般家用也是這樣
    \[ISP LINE1  VTUR\]--//--\[Gateway 1\]--//--\[LAN1\]

- 當一台 gateway 故障的時候, 管理者移除故障的 gateway 連線, 使用者重新取得 IP 可以恢復連線的架構, 一個 LAN 要有兩個以上的 gateway
    \[ISP LINE1  VTUR\]--//--\[Gateway 1\]--//--\[LAN1\]
    \[ISP LINE1  VTUR\]--//--\[Gateway 2\]--//--\[LAN1\]

- 當一條線路故障時, 管理者移除故障線路的 gateway 連線, 使用者重新取得 IP 可以恢復連線的架構
    \[ISP LINE1  VTUR\]--//--\[Gateway 1\]--//--\[LAN1\]
    \[ISP **LINE2** VTUR\]--//--\[Gateway 2\]--//--\[LAN1\]

- 人數很多的時候, 避免太多使用者使用同樣的 IP 對外連線, 造成某些服務的阻擋, 所以可能的做法
    \[ISP LINE1  VTUR\]--//--\[Gateway 1\]--//--\[LAN1\]
    \[ISP LINE2  VTUR\]--//--\[Gateway 2\]--//--\[LAN1\]
    \[ISP LINE1  VTUR\]--//--\[Gateway 3\]--//--\[LAN2\]
    \[ISP LINE2  VTUR\]--//--\[Gateway 4\]--//--\[LAN2\]

- 無線網路跟有線網路要分開不同的 LAN
    \[ISP LINE1  VTUR\]--//--\[Gateway 1\]--//--\[LAN1\]
    \[ISP LINE1  VTUR\]--//--\[Gateway 2\]--//--\[WLAN1\]

- 線路組在中研院的架構, 接近的狀態
    \[中研院\]--//--\[gateway 1\]--//--\[LAN R0\]
    \[中研院\]--//--\[gateway 2\]--//--\[LAN R0\]
    \[中研院\]--//--\[gateway 3\]--//--\[LAN R1\]
    \[中研院\]--//--\[gateway 4\]--//--\[LAN R1\]
    \[中研院\]--//--\[gateway 5\]--//--\[LAN R2\]
    \[中研院\]--//--\[gateway 6\]--//--\[LAN R2\]
    \[中研院\]--//--\[gateway 7\]--//--\[WLAN R0\]
    \[中研院\]--//--\[gateway 8\]--//--\[WLAN R0\]
    \[中研院\]--//--\[gateway 9\]--//--\[WLAN R1\]
    \[中研院\]--//--\[gateway 10\]--//--\[WLAN R1\]
    \[中研院\]--//--\[gateway 11\]--//--\[WLAN R2\]
    \[中研院\]--//--\[gateway 12\]--//--\[WLAN R2\]

- 但是這麼多 gateway 很難帶, 所以要用另外一個做法 XD
    \[ESXi Server \[gateway 1\]\[gateway 2\]\[gateway 3\]\[gateway 4\]\[gateway 5\]\[gateway 6\]\[gateway 7\]\[gateway 8\]\[gateway 9\]\[gateway 10\]\[gateway 11\]\[gateway 12\] /ESXi Server\]--// \[VLAN Trunk\] //--\[中研院 \[中研院\] \[LAN R0\]\[LAN R0\]\[LAN R1\]\[LAN R1\]\[LAN R2\]\[LAN R2\]\[WLAN R0\]\[WLAN R0\]\[WLAN R1\]\[WLAN R1\]\[WLAN R2\]\[WLAN R2\] /中研院\]

- 雞蛋不要放在同一個籃子裡, 線路組在中研院做服務的時候是有兩台獨立的 ESXi Server


```txt



