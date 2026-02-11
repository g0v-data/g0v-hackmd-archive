# omniverse ubuntu install(docker)

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
- 測試
```
docker --version
```

- 安裝 NVIDIA Container Toolkit（讓 Docker 用 GPU）
加入 NVIDIA keyring
```
curl -fsSL https://nvidia.github.io/libnvidia-container/gpgkey \
 | sudo gpg --dearmor -o /usr/share/keyrings/nvidia-container-toolkit-keyring.gpg
```

加入 Repository（Ubuntu 24.04 可用 22.04）
    
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

- 下載 Isaac Sim
```
sudo docker pull nvcr.io/nvidia/isaac-sim:5.1.0
```
- 建立可寫入資料夾

```
mkdir ~/Omniverse
sudo chmod -R 777 ~/Omniverse
```

- 啟動 Isaac Sim Container

```
sudo docker run --gpus all -it --network host \
-v /home/ubuntu/Omniverse:/workspace \
-e ACCEPT_EULA=Y \
--entrypoint /bin/bash \
nvcr.io/nvidia/isaac-sim:5.1.0
```
```
sudo docker run --gpus all -d --network host \
--name isaac51 \
-v /home/ubuntu/Omniverse:/workspace \
-e ACCEPT_EULA=Y \
-e OMNI_KIT_ALLOW_ROOT=1 \
nvcr.io/nvidia/isaac-sim:5.1.0 \
bash -lc "cd /isaac-sim && ./isaac-sim.streaming.sh"

```
```
sudo docker logs -f isaac51
```
- 進入 Isaac Sim 目錄
```
cd /isaac-sim
```

- 允許 Root 執行 + 啟動 WebRTC Streaming

```
./isaac-sim.streaming.sh
```
