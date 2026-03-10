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
sudo docker run --gpus all -d --network host \
--name isaac51 \
-v /home/ubuntu/Omniverse:/workspace \
-e ACCEPT_EULA=Y \
-e OMNI_KIT_ALLOW_ROOT=1 \
-e OMNI_USER='$omni-api-token' \
-e OMNI_PASS='eyJhbGciOiJSUzI1NiIsInR5cCI6IkpXVCJ9.eyJzdWIiOiJuY2t1aW1yYyIsInByb2ZpbGUiOnsiZmlyc3RfbmFtZSI6IiIsImxhc3RfbmFtZSI6IiIsImVtYWlsIjoiIiwiYWRtaW4iOnRydWUsIm51Y2xldXNfcm8iOmZhbHNlLCJyZWFkb25seSI6ZmFsc2UsInByb3ZpZGVyIjoiSW50ZXJuYWwiLCJlbmFibGVkIjp0cnVlLCJhY3RpdmF0ZWQiOnRydWV9LCJqdGkiOiI1N2UxM2Y2NThhN2I0YWY2OTdjYjI1ZGUzYzA4Zjg0YyIsImlhdCI6MTc3MjgwODYyNn0.pbEkK2Q47a2VEuwPHyNvd6sU7VVsIZvIumBYDYVcNBEiFkyQoh6AG918Amvt-6rPbn0TfQ1Qd7OYV0VZtoLljFv0u9lh1-1hgzIht2STaD6zXow6ls-ZKUrDKXJ0UUVOZmJ8vE4qSGdtYZcpX6_3DAMSqDvylv2NQSIx-77j2iKPVZD6rHOZb95I7H3WkS7-V_JpNTYcV_iZ0xIBwqH3myb24gRYmBliGaggZVpWGaH3gG8hjn2T2MZnfpUyRxjxiqMwKJkcVskWfQvlWl057a0K5fKCQ8oZgKFUjDeMzZtZl_QUq6vt7R5z9pAxzLamVutjlDVXkvbyHiZ_4h4fIkbffXMEk3RmZjkPWJa_lWJ-hkQYAyVQH-nAkkqi664BhSb1Kt4GBrJDeUNLLCMZSL0zIVvzd1BfeOjfKG7xAMo44NjO27sAylX_-HzY9TAE6pzxb9CtFK4WuYc97CZTvEyGshyTbFWyaSQXw1Fy4jCaHGesqYg97xWIZXfxk2Z_uxagSKpDZ_gCs4BAOFpx1s0u88IzlQIJP-7_gVpRI_FozaNRCTIm-fPL1UL-JZdOq1zlFZ_ydiuiDPOST7RHXnzhZrLvQPYPWan16J3BKf7i6YrLs91vo5HDblRYNLsNp9irg15DgqLcJqI9mEftmvAhc_1qjgOP9iGHKDkAbHI' \
-e OMNI_HOST='140.116.234.118:8080' \
nvcr.io/nvidia/isaac-sim:5.1.0 \
bash -lc "cd /isaac-sim && ./runheadless.sh \
--/exts/omni.kit.livestream.app/primaryStream/streamPort=47998 \
--/exts/omni.kit.livestream.app/primaryStream/signalPort=49100"
```
- 最新版
```
sudo docker run --gpus all -d --network host \
--name isaac51 \
-v /home/ubuntu/Omniverse:/workspace \
-e ACCEPT_EULA=Y \
-e OMNI_KIT_ALLOW_ROOT=1 \
-e OMNI_USER='$omni-api-token' \
-e OMNI_PASS='eyJhbGciOiJSUzI1NiIsInR5cCI6IkpXVCJ9.eyJzdWIiOiJuY2t1aW1yYyIsInByb2ZpbGUiOnsiZmlyc3RfbmFtZSI6IiIsImxhc3RfbmFtZSI6IiIsImVtYWlsIjoiIiwiYWRtaW4iOnRydWUsIm51Y2xldXNfcm8iOmZhbHNlLCJyZWFkb25seSI6ZmFsc2UsInByb3ZpZGVyIjoiSW50ZXJuYWwiLCJlbmFibGVkIjp0cnVlLCJhY3RpdmF0ZWQiOnRydWV9LCJqdGkiOiJhMGJiYjI5ZDkzNjQ0MThhYjk2MTQ2OGQ1NTdkZWExMSIsImlhdCI6MTc3MzEzODQ5MX0.S6WG-_wRzxSHLmMi1GnZ5MRASiis4b3Lm-fonvR0G2aEXJYuw5ycEAJbDWGzYGsb5zs39EpFcYklZsJOyqO0qucxUBoezmgy_ET19zOinSgUciwC54m8rsUdihmqN22J4ktczAfG83Hs_6L2hYh_ONhQYC-D_mTo1s4b9IyYSiA3pMYnPtg4PhqKzdtOt9O9zrdEmQ_PBYdg0JVAyKE5um4fmegc-urRuur7EBIYeFF37cf5CIYX7PLjZa0NcPTl9orJyfXqCORwdLDYQMkz_Bn43t33evozhikmZ1VmDJA5DXbtRznIu6c8Sk-msYAyGGvR1QKswBcCZB7labwZQ43wLNHNooTIWaVPECfG66KSYlJOx-uOIOKhcny2kt523AKyQCUz34ogVkxXC7yDZ3HZqk_GibppEkHzUFFMkUSkfI7bZFJ9HJoopLkx-Ah2Ye39Kmb2fWvJ5ZE7zN7MJ1VWZ0zdokLdB06wfSuyoSD9CMJ7h5DU6cIonpVlUFdD3U0IA2eCoksCD75ul2-8uH9iR3QlaClPNnzH-C3qOmJeYV1uel8Wv_pQP5AKP-6YtKKmmRjizR-VnpK8KLQR-soDZhxTarTToi_8HqPwi5VphzewvQZuv3Iv4WDr7mZMmil0ATKLeBQvtn7LSCO3IwFUbtO4lOldrqQRXgS9ahE' \
-e OMNI_HOST='omniverse-nucleus.imrc.tw:443' \
nvcr.io/nvidia/isaac-sim:5.1.0 \
bash -lc "cd /isaac-sim && ./runheadless.sh \
--/exts/omni.kit.livestream.app/primaryStream/streamPort=47998 \
--/exts/omni.kit.livestream.app/primaryStream/signalPort=49100"
```

```
sudo docker logs -f isaac51
```
./isaac-sim.streaming.sh
- 進入 Isaac Sim 目錄
```
cd /isaac-sim
```

- 允許 Root 執行 + 啟動 WebRTC Streaming

```
./isaac-sim.streaming.sh
```
