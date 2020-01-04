---
title: "如何使用hugo写博客"
date: 2019-12-26T13:12:19+08:00
draft: false
---
### 环境搭建

1. 你需要FQ

2. 安装VSCode

3. 安装GIT

4. 安装cmder
[fdf](../static/images/ping.png)
5. 安装hugo

  1. [hugo官方安装教程](https://gohugo.io/getting-started/installing)

  2. 注意检查本地PATH路径是否有hugo启动路径

  3. cmder中输入下列代码检查是否安装成功

~~~ 
  hugo version
~~~

### hugo快速开始

1. [hugo官网](https://gohugo.io)

2. 点击Quick Start

3. 按官方教程一步步做

#### 注意事项：

1. 步骤2 quickstart 文件夹命名更改格式: 你的github用户名.github.io-xxx

2. 步骤3 可以更改博客主题，新手不建议更改

hugo操作完毕。

### 上传至GitHub**

1. 到你创建博客文件夹的根目录创建一个文件,命名为.gitignore,在里面输入/public/

2. 进入public文件夹,输入下列代码

~~~
git init

git add.

git commit -v
~~~
3. 进入githua创建一个新的仓库，命名规则: 用户名.github.io
4. 复制github里面的俩行代码即可部署完成
~~~
git remote add origin
git push -u origin master
~~~
5. 进入setting查看部署完成链接



### Github备份你的博客代码
1. github创建一个新的仓库
2. 复制那俩行代码即可

  

### Github更新你的代码

~~~
git status
git add .
git commit -v
git pull
git push origin master
~~~

