---
title: gitlab设置ssh-key
date: 2020-03-28 09:48:39
---
1.打开本地git bash,使用如下命令生成ssh公钥和私钥对

、、、sctript
ssh-keygen -t rsa -C 'xxx@xxx.com' 然后一路回车(-C 参数是你的邮箱地址)
、、、

2.然后会出现：Enter file in which to save the key (/Users/yzq/.ssh/id_rsa):
、、、sctript
回车
、、、

3.如果你的.ssh/id_rsa已经，则会出现：/Users/yzq/.ssh/id_rsa already exists.

Overwrite (y/n)? y

4.设置你的密码（位数不要太短，尽量设置6位）
出现sskey 密钥图形

5.现在只需要查看本机ssh公钥，获取得到它

、、、sctript
cd ~/.ssh
ls（查看目录是否有id_rsa.pub文件）
查看公钥：cat id_rsa.pub    或者vim id_rsa.pub
、、、

获取到的那一大段，就是我们需要的ssh key，复制下来,包括前面和后面的，给到下图配置，即可完成GitLab配置ssh key

配置到gitlab,sshKey，设置的地方