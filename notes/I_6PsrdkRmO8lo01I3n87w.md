# nginx cross 
1. `export PATH=/root/Marvell_98DX3510_switch/trunk/mrvl_22.02.0_kernel/toolchain/aarch64v8-marvell-linux-gnu-5.2.1_x86_64_20160301/bin:$PATH`
2. `export CROSS_COMPILE=/root/Marvell_98DX3510_switch/trunk/mrvl_22.02.0_kernel/toolchain/aarch64v8-marvell-linux-gnu-5.2.1_x86_64_20160301/bin/aarch64-marvell-linux-gnu-` 
3. 下载Nginx 1.15.6，zlib 1.2.11，openssl 1.1.1d，pcre 8.43
4. 先进入每个依赖的源码目录，分别把pcre、openssl编译好。
5. 編譯pcre
* `LDFLAGS=-L/root/Marvell_98DX3510_switch/trunk/mrvl_22.02.0_kernel/toolchain/aarch64v8-marvell-linux-gnu-5.2.1_x86_64_20160301/lib `
* `CFLAGS=-I/root/Marvell_98DX3510_switch/trunk/mrvl_22.02.0_kernel/toolchain/aarch64v8-marvell-linux-gnu-5.2.1_x86_64_20160301/include` 
* `CC=aarch64-marvell-linux-gnu-gcc` 
* `CXX=aarch64-marvell-linux-gnu-g++ `
* `./configure --disable-shared --build=x86_64-marvell-linux-gnu --target=aarch64-marvell-linux-gnu --host=aarch64-marvell-linux-gnu --prefix=/root/Marvell_98DX3510_switch/trunk/apps/pcre2-10.43/target`
* `make` 
6. 編譯openssl
* `./Configure linux-aarch64 --prefix=/root/Marvell_98DX3510_switch/trunk/apps/openssl-1.1.1v/target no-shared no-threads --cross-compile-prefix=aarch64-marvell-linux-gnu-`
* `make`
7.編譯nginx
 `./configure --with-openssl=/root/Marvell_98DX3510_switch/trunk/apps/openssl-3.2.0 --crossbuild=Linux::aarch64 --with-cc=${CROSS_COMPILE}gcc --prefix=/root/Marvell_98DX3510_switch/trunk/apps/nginx-1.22.1-target/target --with-pcre=/root/Marvell_98DX3510_switch/trunk/apps/pcre2-10.43-target/ --with-zlib=/root/Marvell_98DX3510_switch/trunk/apps/zlib-1.3.1-target/ --without-http_gzip_module --with-http_ssl_module`
11.  ` ./configure --with-cc-opt=-I$TOOLCHAIN/include --crossbuild=aarch64-marvell-linux-gnu --prefix=/root/Marvell_98DX3510_switch/trunk/apps/nginx-1.22.1-target/target             --with-zlib=/root/Marvell_98DX3510_switch/trunk/apps/zlib-1.3.1-target/ --with-pcre=/root/Marvell_98DX3510_switch/trunk/apps/pcre2-10.43-target/ --with-openssl=/root/Marvell_98DX3510_switch/trunk/apps/openssl-1.1.1v-target/             --with-http_stub_status_module --with-http_ssl_module`