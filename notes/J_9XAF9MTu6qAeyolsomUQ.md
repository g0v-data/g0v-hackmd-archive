# 關於 FbScraping 的 cpu 測試
0. 希望透過本機模擬預測 middle2 上執行指令的 cpu 增加是否能提升 discover, update 的速度，如果能增加那增加的幅度會預期是多少？（假設本機上的表現和 middle2 上的表現是同樣的線性關係）
1. 比較 middle2 與本機，在一樣的基礎指令參數（n=1）下執行時的速度：各跑 a 和 b 達 3 小時以上，計算個別的速度（discover：article數/經過時數，update：article snapshot數/經過時數））
    - a. discover
        `python3 fb_handler.py --discover --page --login --max 100 --cpu {n} --auto 2`
    - b. update
        `python3 fb_handler.py --update --page --max 10000 --cpu {n} --auto 2`
2. 在本機上測試 n 為 2 ~ 4 時，discover 和 update 寫入到本機上的資料庫的速度各是多少，計算速度的方式同 1
3. 列出本機上 n 為 1 ~ 4 時和 middle2 上 n 為 1 時 discover 和 update 個別的速度
4. 模擬 middle2 上 n 為 2 ~ 4 時 discover 和 update 的速度：透過 m2_n = m2_1 x (本_n / 本_1)，n 為 2 ~ 4
    - m2_n: 預測 middle2 上以 cpu 參數為 n 執行指令時，discover 和 update 分別的速度
    - m2_1: middle2 上以 cpu 參數為 1 執行指令時，discover 和 update 分別的速度
    - 本_n: 本機上以 cpu 參數為 n 執行指令時，discover 和 update 分別的速度
    - 本_1: 本機上以 cpu 參數為 1 執行指令時，discover 和 update 分別的速度