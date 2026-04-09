# omniverse isaac sim mcp server
[toc]
## Installation
```
cd ~/Documents
git clone https://github.com/omni-mcp/isaac-sim-mcp
```
![](https://g0v.hackmd.io/_uploads/rJeTvhNrnWg.png)

## Install MCP Server
```
uv pip install "mcp[cli]"
uv run /home/ubuntu/Documents/isaac-sim-mcp/isaac_mcp/server.py
```
![](https://g0v.hackmd.io/_uploads/H1D-p4B2-e.png)

## 下載cursor
[點擊前往下載](https://cursor.com/zh-Hant/download?utm_source=google_paid&utm_campaign=%5BSearch%5D+%5BBrand%5D+%5BEN%5D+%5BAPAC+T1%5D+%5BBroad%5D+%5BMax+Conv%5D+%5BSubscribes%5D+Brand&utm_term=cursor&utm_medium=paid&utm_content=799681480444&cc_platform=google&cc_campaignid=23639215328&cc_adgroupid=194817004980&cc_adid=799681480444&cc_keyword=cursor&cc_matchtype=b&cc_device=c&cc_network=g&cc_placement=&cc_location=9199124&cc_adposition=&gad_source=1&gad_campaignid=23639215328&gbraid=0AAAABAkdGgRvTAiWfLduKnrfGWPc0tgdD&gclid=CjwKCAjwnN3OBhA8EiwAfpTYeojl7v-SZCR4lImnR0pLZyzsOD98vObmJFV6YbkEmC3pv_4fPejighoCruQQAvD_BwE)
## 建立mcp server
![](https://g0v.hackmd.io/_uploads/BkeLWCNSnZl.png)
- 補圖
```
{
    
    "mcpServers": {
        "isaac-sim": {
            "command": "uv run /home/ubuntu/Documents/isaac-sim-mcp/isaac_mcp/server.py"
        }
    }
}
```
## 開啟Isaac-sim
```

cd ~/isaacsim/_build/linux-x86_64/release

./isaac-sim.sh \
--ext-folder /home/julia/文件/isaac-sim-mcp

```

![](https://g0v.hackmd.io/_uploads/r1HecVBnWg.png)

![](https://g0v.hackmd.io/_uploads/Bkf49VB3Zx.png)
- 嘗試呼叫場景資訊，確認mcp server是否有連線成功
```
Call isaac-sim get_scene_info
```
![](https://g0v.hackmd.io/_uploads/BkxW8c4H2Zg.png)
- 透過下prompt create a cude
```
create a cude in isaac-sim
```
![](https://g0v.hackmd.io/_uploads/H1kd54ShZg.png)

