---
tags: bridge
---
# bridge

- Contributors: pm5
- Project repo: https://github.com/g0v/bridge

## What's the issue / 有什麼問題

- There's no really fixed boundaries for a community like g0v, so people use a lot of different online tools for communications.  Since not everyone is constantly checking every communication tool, as the community expands, it is harder and harder to effectively communicate and build consensus.
- Currently g0v relies heavily on Slack for online communications.  This creates a few problems:
    1. Slack is not open source.  This is a problem in itself for some.
    2. Slack provides limited features for its free version.
    3. Depending on a single tool makes it expensive to maintain the infrastructure and to migrate to other tools.
- If part of the community wishes to migrate to another communication tool, the two sets of tools may run in parallel for quite a long period of time, and there needs to be a way to help people converting back and forth.

**中文**

- 社群沒有邊界，所以使用很多不同型態的線上溝通工具。因為不是每個人都會隨時查看每個線上工具，社群愈擴散，溝通效果與凝聚力就愈差。
- 目前 g0v 重度依賴 Slack 進行線上即時溝通，這會有幾個問題：
    1. Slack 不是開源的，對部分人來說這本身就是個問題。
    2. Slack 免費版有一些功能限制。
    3. 太過集中在單一工具讓維護與轉移成本很高。
- 如果社群要逐漸移動到別的溝通工具，中間的轉換期可能很長，需要協助大家轉換的橋接方式。

## How to solve the it / 怎麼解決問題

- [matterbridge](https://github.com/42wim/matterbridge) can bridge many different communication tools, and forward the messages on one of them to all the other places.
- [g0v/bridge](https://github.com/g0v/bridge) can build a set of tools to configure and monitor matterbridge.
- "Bridge governance guidelines" can help people understand how bridge will use their data, and how can projects and channels utilize bridge in their work.

**中文**

- [matterbridge](https://github.com/42wim/matterbridge) 可以串接不同的溝通工具，把其中一方的訊息轉送到其它多方。
- [g0v/bridge](https://github.com/g0v/bridge) 可以建立一套設定與控制 matterbridge 的工具。
- 「bridge 治理機制」可以讓大家瞭解 bridge 會如何使用資料，而各專案與頻道可以如何使用 bridge 協助他們溝通。

## How can I help / 需要什麼協助

- Apply and install bot/app tokens for the communication tools for multiple communities.
    - g0v Slack: [installed and working](https://g0v.hackmd.io/xbrqQThXSNmWTepWqbZ9GQ)
    - Code for Korea: installed and working
    - Code for Japan: installed and working
    - (You can propose other communities here)
- Build the governance guidelines for bridge.

**中文**

- 取得多個社群溝通工具的 bot/app/token
    - [Slack] g0v Slack [已取得並設定完成](https://g0v.hackmd.io/xbrqQThXSNmWTepWqbZ9GQ)
    - [Slack] Code for Korea 已取得並設定完成
    - [Slack] Code for Japan 已取得並設定完成
    - [Discord] 零時小學校 已取得並設定完成
    - [Discord] UniCourse 已取得並設定完成
    - [Slack] Parti
        - 連結 g0v Slack #disinfo
    - [Slack] 島島阿學 建立中
        - 連結 g0v Slack #島島阿學
    - [Slack] Code for ALL #event channel [籌備文件](https://g0v.hackmd.io/mHhoDJlYRIClYZIOlMjgqg)
    - [Telegram] clickhouse.tw
        - 連結 g0v Slack #clickhouse
    - [Meshtasic] Meshtasic to g0v slack
        - Meshtastic 的 SignalTest channel，連結 g0v Slack #civil-defense
        - https://g0v.hackmd.io/0bHi9giDQN66h0HGAVp9aw
    - （其它可在這份文件上提議，在無 bridge 治理機制之前暫時於文件上討論決定）
- 討論 bridge 治理機制
- 筆記跨頻道訊息呈現結果與課題
    - 20250112 圖文 https://g0v.hackmd.io/laSUbXSySQOqE2nbpB8QYQ?view

## Assorted ideas / 其它想法

- Alternatives to Slack
    - [Zulip](https://github.com/zulip/zulip) (you can join the [Zulip community server](https://zulip.readthedocs.io/en/latest/contributing/chat-zulip-org.html) to see it working; also read [this](https://zulip.com/for/open-source/), [this](https://zulip.com/for/communities/), [this](https://zulip.com/help/moderating-open-organizations), and [this](https://news.ycombinator.com/item?id=27149123))
    - [Discord](https://discord.com/)
        - [Adding Discord to g0v bridge](https://g0v.hackmd.io/vdIjwcbiQcm3FCnKrcsaiA)
    - Telegram
        - [Adding Telegram group to bridge](https://g0v.hackmd.io/a3IelgLGT-GwisBu0RNNXQ?view)
    - [Mattermost](https://github.com/mattermost/mattermost-server)
    - [Rocket Chat](https://github.com/RocketChat/Rocket.Chat)
    - IRC
- [LINE and Slack Integration](https://g0v.hackmd.io/HSdBjpZcTdu5VHUsv4DRKA)