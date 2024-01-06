---
title: "vNext 實作計畫"
tags: VNext,hackpad
---

# vNext 實作計畫

> [點此觀看原始內容](https://g0v.hackpad.tw/ffhN0cnUnHg)


之前就有在設想如何能採用時下技術，讓傳統BBS系統能夠脫離硬體、頻寬、政治上的束縛，達成無上站人數限制的架構；原本想用NextBBS或是P2PBBS的名子，到這裡找了一下之後發現 [**PTT vNext**](https://g0v.hackpad.com/PTT-vNext-kt3vsWylF9i)  的討論有相似訴求，所以借用vNext這個名子進行社群開發。

概念
Full utilize new toys like p2p filesystem, data structure change streaming to dramaticly reduce server's loading. the main server(cluster) mainly handle write operation and feeding newest changes to clients.

1.  使用p2p傳播上站主要架構(Main entry and long-term data, e.g.
    1.  Main menu
    2.  Board category structure
    3.  board archived data
    4.  chat history
2.  使用p2p to sync live changes for boards, one sync streaming network  for one board.
3.  The board's live data get archived on daily / size base
參考技術清單
1.  [tristanls](https://github.com/tristanls)/[**gossipmonger**](https://github.com/tristanls/gossipmonger)
    1.  Gossip protocol endpoint for real-time peer-to-peer replication
2.  [automenta](https://github.com/automenta)/[**telepathine**](https://github.com/automenta/telepathine)
    1.  p2p gossip protocol w/ incremental diffs & failure detection for a fault-tolerant, self-managing cluster or mesh (for node.js)
3.  [http://ipfs.io/](http://ipfs.io/)
    1.  IPFS is a new hypermedia distribution protocol, addressed by content and identities. IPFS enables the creation of completely distributed applications. It aims to make the web faster, safer, and more open.
    2.  [https://www.youtube.com/watch?v=8CMxDNuuAiQ](https://www.youtube.com/watch?v=8CMxDNuuAiQ)


