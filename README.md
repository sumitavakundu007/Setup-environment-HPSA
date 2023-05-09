# Setup-environment-HPSA
Setup ubuntu 18.04.6 environment for Hard particle self-assembly reasearch

$ Install ubuntu-18.04.6 bionic

### Create two directories in /home/user
```bash
$ mkdir softwares my_install
```
### Install git and set proxy on git
```bash
$ sudo apt-get install git
```
open .gitconfig and add the following lines
```bash
$ vi .gitconfig
```
```bash
[http]
[http "https://iacs.res.in"]
        proxy = http://User
        proxy = http://User
[http "https://domain.com"]
        sslVerify = false
[https]
[user]
[http]
[url "https://"]
        insteadOf = git://
[user]
        name = Username
        email = your email id
[http]
        sslVerify = false
        proxy = http://Username:password@proxy.server.com:port
```
### Set proxy on wget
Open /etc/wgetrc and uncomment the following lines
```bash
$ sudo vi /etc/wgetrc
```
```bash
http_proxy = http://username:password@proxy.server.comn:port/
https_proxy = https://username:password@proxy.server.comn:port/
ftp_proxy = ftp://username:password@proxy.server.comn:port/
use_proxy = on
```
## If you want to install almost everything from scratch then follow these steps
### Install GCC-v7.5.0 (c++11 compiler)
```bash
$ unset LIBRARY_PATH CPATH C_INCLUDE_PATH PKG_CONFIG_PATH CPLUS_INCLUDE_PATH INCLUDE
```
GCC depends on GMP, MPFR, MPC and ISL. Work for each of them one by one
```bash
$ export /path/to/prefix = /custom_path_for_gcc
```
### GMP
```bash
wget ftp://gcc.gnu.org/pub/gcc/infrastructure/gmp-4.3.2.tar.bz2
$ tar -xvf gmp-4.3.2.tar
$ cd gmp-4.3.2
$ ./configure --disable-shared --enable-static --prefix=/path/to/prefix
$ make && make check && make install
```
### MPFR
```bash
$ wget ftp://gcc.gnu.org/pub/gcc/infrastructure/mpc-0.8.1.tar.gz
$ tar -xvf mpfr-2.4.2.tar
$ cd mpfr-2.4.2
$ ./configure --disable-shared --enable-static --prefix=/path/to/prefix --with-gmp=/path/to/prefix
$ make && make check && make install
```
### MPC
```bash
$ wget ftp://gcc.gnu.org/pub/gcc/infrastructure/mpc-0.8.1.tar.gz
$ tar zxvf mpc-0.8.1.tar.gz
$ cd mpc-0.8.1
$ ./configure --disable-shared --enable-static --prefix=/path/to/prefix --with-gmp=/path/to/prefix --with-mpfr=/path/to/prefix
$ make && make check && make install
```
### ISL
```bash
$ tar -xvf isl-0.18.0.tar.gz
$ cd isl-0.18.0
$  ./configure --disable-shared --enable-static --prefix=/path/to/prefix --with-gmp=/path/to/prefix
$ make && make install
```
Now it's the time to compile GCC
```bash
$ tar -xvf gcc-vx.x.x
$ cd gcc-vx.x.x
$ mkdir build && cd build
$../configure --prefix=/path/to/prefix --enable-std=c++11 --enable-shared --disable-bootstrap --disable-libstdcxx-pch --enable-languages=all --enable-threads=posix --with-gmp=/path/to/prefix --with-mpfr=/path/to/prefix --with-mpc=/path/to/prefix --with-libisl=/path/to/prefix --disable-multilib --disable-werror
$ make -j20
$ make install
```
