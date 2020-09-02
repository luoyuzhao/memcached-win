# memcached-win
memcached,windows
1.安装cygwin64
http://www.cygwin.com/
安装make，gcc-g++，perl，mingw-gcc-g++等工具

2.下载openssl
https://github.com/openssl/openssl

3.下载libevent
https://libevent.org/

4.下载memchached
http://memcached.org/

5.编译
运行Cygwin64Terminal

编译openssl

tar zxvf openssl-OpenSSL_1_1_1g.tar.gz -C /usr/src
cd /usr/src/openssl-OpenSSL_1_1_1g
./config --prefix=/usr/local/openssl
make && make install

编译libevent
tar zxvf libevent-2.1.12-stable.tar.gz -C /usr/src
cd /usr/src/libevent-2.1.12-stable
export PKG_CONFIG_PATH=/usr/local/openssl/lib/pkgconfig/
./configure --prefix=/usr/local/libevent CFLAGS="-I/usr/local/openssl/include" LDFLAGS="-I/usr/local/openssl/lib"
如不需要openssl则--disable-openssl
./configure --prefix=/usr/local/libevent --disable-openssl
make && make install

编译memchached
tar zxvf memcached-1.6.6.tar.gz -C /usr/src
cd /usr/src/memcached-1.6.6
./configure --prefix=/usr/local/memcached --with-libevent=/usr/local/libevent
make && make install

复制cygwin64安装目录bin下的cygwin1.dll到memchached/bin中
复制libevent/bin下全部文件(cygevent-2-1-7.dll,cygevent_pthreads-2-1-7.dll,cygevent_openssl-2-1-7.dll,cygevent_extra-2-1-7.dll,cygevent_core-2-1-7.dll)
至memchached/bin中
done!


