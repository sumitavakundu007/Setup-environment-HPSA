# Setup-environment-HPSA
Setup ubuntu 18.04.6 environment for Hard particle self-assembly reasearch

$ Install ubuntu-18.04.6 bionic

### Create two directories in /home/user
```bash
mkdir softwares my_install
```
### Install git and set proxy on git
```bash
sudo apt-get install git
```
open .gitconfig and add the following lines
```bash
vi .gitconfig
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
sudo vi /etc/wgetrc
```
```bash
http_proxy = http://username:password@proxy.server.comn:port/
https_proxy = https://username:password@proxy.server.comn:port/
ftp_proxy = ftp://username:password@proxy.server.comn:port/
use_proxy = on
```
