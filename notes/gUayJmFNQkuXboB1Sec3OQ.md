# Todo list

## 2024-5-13 to 2024-5-20

### Brian

- [x] 3D gaussian splatting能否只更新部分point clouds？
    * 只有在某個角度被看到的那些point cloud會參與render，因此也只有這些point cloud會被更新。因此不存在原本提出的問題。不過有些方法會固定point cloud的某些屬性（比如rotation），可以參考。
- [ ] stable diffusion有Viewpoint bias（比如現實圖片中大多數都是front Viw）。第一階段用zero1to3先得到符合3D特性的coarse model（在這個階段可以先不更新顏色屬性？）(distengle geometry and appearance)，第二階段使用stable diffusion再用多視角不同prompt的方法進行refine
- [ ] 受DreamCraft3D啟發，我們可以分階段同時結合不同的diffusion model的優勢達到我們的目的。所以打算整理現有的diffusion model的特點：https://g0v.hackmd.io/@cqFb7IsmShmEXKHL14pa8Q/BJrH8ve7A/edit
- [ ] depth and normal maps可以扮演什麼角色？




### Peng


