自架 jitsi 筆記
==============
* 環境用 AWS EC2 t2.micro
    * 1GB Ram
    * 在 buildweb 時記憶體會不夠，需要 1.5G 左右，但是運作只會用到 300M 很夠，所以可以 build 時用 t2.small ， build 完再降回來
* prosody
    * Debian 9 內建的是 prosody 0.9 ，不支援 websocket ，如果想要支援 websocket 可換 prosody 0.10
    * https://prosody.im/download/package_repository
    * 需要套件
        * sudo apt install luarocks libssl1.0-dev libtolua-dev
        * sudo luarocks install net-url
        * sudo luarocks install basexx
        * sudo luarocks install luajwtjitsi
        * sudo luarocks install lua-cjson 2.1.0-1

