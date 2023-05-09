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
>>
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
