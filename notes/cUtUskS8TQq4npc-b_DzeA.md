#!/bin/bash

# 切換至指定目錄
cd ~/Code/Fullcode_clone_script

# 開啟新的 terminal 並執行第一個 script
gnome-terminal -- bash -c "./LTS-v12_AST2500EVB_FULL1.sh; exec bash"

# 開啟新的 terminal 並執行第二個 script
gnome-terminal -- bash -c "./LTS-v13_AST2600EVB_FULL1.sh; exec bash"