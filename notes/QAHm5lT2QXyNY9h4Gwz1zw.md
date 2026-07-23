# 使用codex連接blender mcp server
[toc]
## 整體架構
```
             ┌─────────────┐
             │   Codex     │
             └──────┬──────┘
                    │ MCP Tool
                    ▼
         ┌────────────────────┐
         │ blender-mcp Server │
         │  (uvx blender-mcp) │
         └─────────┬──────────┘
                   │ localhost:9876
                   ▼
         ┌────────────────────┐
         │ Blender Addon      │
         └─────────┬──────────┘
                   ▼
              Blender Scene
```
## blender mcp server
- [blender map server github ](https://github.com/ahujasid/blender-mcp/blob/main/addon.py)
- 下載 addon.py
## 安裝blender
- 安裝[blender](https://www.blender.org/download/lts/4-5/)
- 點擊linux
![](https://g0v.hackmd.io/_uploads/rydx181BGg.png)
- `tar -xf blender-4.5.12-linux-x64.tar.xz`
- `cd blender-4.5.12-linux-x64`
- `./blender`
![](https://g0v.hackmd.io/_uploads/H1Ih18JHMg.png)
- edit-->preferences
![](https://g0v.hackmd.io/_uploads/rkb_lIyHfg.png)
- get extension--> install from disk
![](https://g0v.hackmd.io/_uploads/BySjbLJBzl.png)
- 匯入addon.py
- 點擊方向位置旁的小箭頭
![](https://g0v.hackmd.io/_uploads/H1zG78JSMg.png)
- 點擊connect to mcp server
![](https://g0v.hackmd.io/_uploads/SkLrQ8JSfx.png)

## codex連接
- 在vscode的extensions輸入codex並安裝
![](https://g0v.hackmd.io/_uploads/B1E2Q8ySGl.png)
- bar右側會有chatgpt標誌，點擊即可開啟codex
![](https://g0v.hackmd.io/_uploads/H1CbNIJBGe.png)
- 點擊settings標誌
![](https://g0v.hackmd.io/_uploads/H1AVEUkSGe.png)
- 輸入mcp server設定
![](https://g0v.hackmd.io/_uploads/ByxikEUkSfe.png)

## 測試是否連接成功
- 輸入下列文字，如果有出現類似下方圖片的結果表示有連接到mcp server
```
What MCP tools are currently available to you?
```
![](https://g0v.hackmd.io/_uploads/BkgsNIyrMg.png)
- 輸入下列文字，測試修改場景
```
Using execute_blender_code, create a UV sphere at (2, 0, 0) named TestSphere.
```
- 成功的話會出現圓球在畫面上
![](https://g0v.hackmd.io/_uploads/HktsUIkBfx.png)

## extension
:::success
**修改界面字體大小**
edit-->preferences
![](https://g0v.hackmd.io/_uploads/rkb_lIyHfg.png)
interface-->修改resolution scale
![](https://g0v.hackmd.io/_uploads/rkyklUySfx.png)
:::


