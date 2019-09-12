---
title: 怎么使用hexo，github搭建个人博客
date: 2017-07-08 14:09:17
tags: 
---
1、安装Nodejs npm

2、安装hexo
npm install hexo-cli -g

3、 初始化、安装依赖
hexo init folder(文件夹)
cd folder（文件夹）
npm install

4、修改主题
hexo主题选择可以参考地址 https://www.zhihu.com/question/24422335
选择你喜欢的主题克隆到themes文件下面
修改_config.yml 将theme: 换成你克隆下来的主题文件名

5、github新建工程
工程名必须为 githupname.github.io 的格式

6、配置_config.yml
将配置文件修改成如下格式
title: 点滴
author: Joanna
deploy:
  type: git
  repository: https://github.com/princessJoanna/princessJoanna.github.io.git
   branch: master
（特别注意：分号后面都要后空格，tpye前面要有空格,sshkey没有添加的话需要先增加sshkey到github上面）

7、生成静态页面
hexo generate

8、本地启动
启动本地服务，进行文章预览调试，命令：
hexo server

浏览器输入http://localhost:4000

9、然后执行命令：
hexo deploy
然后再浏览器中输入http://princessJoanna.github.io/就行了