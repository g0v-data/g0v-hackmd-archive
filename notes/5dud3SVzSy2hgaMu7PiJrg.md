# 女婕思小抄
[toc]
## 解圖片工具
- exiftool
    - 用途：讀取圖片的 metadata（如 EXIF 資訊），常有 flag 藏在這裡。
    - `exiftool image.jpg`
- zsteg
    - 用途：分析 PNG、BMP 等圖片的 LSB 隱寫技術。
    - `zsteg image.png
    - `ㄈ-a`       | 自動掃描所有常見通道與隱寫方式      |
| `-E`       | 自訂掃描通道和位元層（如 `b1,r`） |
| `--lsb`    | 列出所有可能存在的隱寫資訊        |
| `--bits N` | 指定幾個最低有效位元來分析        |
| `-v`       | 顯示詳細輸出               |
`
`
- strings
    - 用途：直接抓出圖片中的可見 ASCII 字串，有時 flag 會直接藏在圖片 metadata 或尾部。
    - `strings image.jpg | grep -i flag`
- binwalk
    - 用途：分析圖片中是否嵌入了其他檔案（例如 zip、PNG、MP3 等）。
    - `binwalk image.jpg`
    - `binwalk -Me image.jpg  # 多層遞迴解壓`
- stegsolve
    - 打開圖片後，可以切換各種視角查看藏匿資訊。
- steghide
    - 用途：藏有資料的圖片（如 JPEG）中提取藏匿內容。
    - `steghide extract -sf image.jpg
`