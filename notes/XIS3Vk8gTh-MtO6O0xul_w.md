---
tags: edu
---

# omniverse ubuntu install(docker)
[toc]
## 安裝初始環境
- 確認 GPU
```
nvidia-smi
```

- 安裝 Docker
```
sudo apt update
sudo apt install docker.io -y
sudo systemctl enable docker
sudo systemctl start docker
```
- 測試是否docker安裝成功
```
docker --version
```

- 安裝 NVIDIA Container Toolkit（讓 Docker 用 GPU）
- 加入 NVIDIA keyring
```
curl -fsSL https://nvidia.github.io/libnvidia-container/gpgkey \
 | sudo gpg --dearmor -o /usr/share/keyrings/nvidia-container-toolkit-keyring.gpg
```

- 加入 Repository（Ubuntu 24.04 可用 22.04）
    
```
curl -fsSL https://nvidia.github.io/libnvidia-container/ubuntu22.04/libnvidia-container.list \
 | sed 's#deb https://#deb [signed-by=/usr/share/keyrings/nvidia-container-toolkit-keyring.gpg] https://#g' \
 | sudo tee /etc/apt/sources.list.d/nvidia-container-toolkit.list
```
- 安裝 Toolkit
```
sudo apt update
sudo apt install -y nvidia-container-toolkit
sudo nvidia-ctk runtime configure --runtime=docker
sudo systemctl restart docker
```
- 測試 Docker GPU(成功代表 Docker 可用 GPU)
```
sudo docker run --rm --gpus all nvidia/cuda:12.2.0-base-ubuntu22.04 nvidia-smi
```
- 登入 NVIDIA NGC
```
sudo docker login nvcr.io
```
Username：$oauthtoken

Password：[NGC API Key](https://org.ngc.nvidia.com/setup/api-key)要去申請

## 下載 Isaac Sim
```
sudo docker pull nvcr.io/nvidia/isaac-sim:5.1.0
```
- 建立可寫入資料夾

```
mkdir -p ~/Omniverse
sudo chown -R $USER:$USER ~/Omniverse
chmod -R 755 ~/Omniverse
```
## 取得nucleus server token
- 登入[https://omniverse-nucleus.imrc.tw/](https://omniverse-nucleus.imrc.tw/)

- 右鍵點選`omniverse-nucleus.imrc.tw:443`，點擊API Token

![](https://g0v.hackmd.io/_uploads/SJxwznC33-l.png)

- 輸入名稱取得token

![](https://g0v.hackmd.io/_uploads/rJlS53RhnZx.png)
## 建立docker container
- 啟動 Isaac Sim Container
- name ==isaac51==為自己預設，可自行更改
- OMNI_PASS要寫==nucleus server token==
```
sudo docker run --gpus all -d --network host \
--name isaac51 \
--runtime=nvidia \
-v /home/ubuntu/Omniverse:/workspace \
-e ACCEPT_EULA=Y \
-e OMNI_KIT_ALLOW_ROOT=1 \
-e OMNI_USER='$omni-api-token' \
-e OMNI_PASS='your_nucleus_api_token' \
-e OMNI_HOST='omniverse-nucleus.imrc.tw:443' \
nvcr.io/nvidia/isaac-sim:5.1.0 \
bash -lc "cd /isaac-sim && ./runheadless.sh \
--/exts/omni.kit.livestream.app/primaryStream/streamPort=47998 \
--/exts/omni.kit.livestream.app/primaryStream/signalPort=49100"
```
## docker常用指令
- 看「目前正在運行的 container」
```
sudo docker ps
```
- 看「這個 container 裡面的執行過程」
```
sudo docker logs -f isaac51
```
- 停止container
```
sudo docker stop isaac51
```
- 重新開啟container
```
sudo docker start isaac51
```
- 刪除 container
```
sudo docker rm isaac51
```
- 停止+刪除container
```
sudo docker rm -f isaac51
```