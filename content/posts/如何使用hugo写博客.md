---
title: "如何使用hugo写博客"
date: 2019-12-26T13:12:19+08:00
draft: false
---

### 环境搭建

1. 你需要 FQ

2. 安装 VSCode

3. 安装 GIT

4. 安装 cmder

5. 安装 hugo

6. [hugo 官方安装教程](https://gohugo.io/getting-started/installing)

7. 注意检查本地 PATH 路径是否有 hugo 启动路径

8. cmder 中输入下列代码检查是否安装成功

```
  hugo version
```

### hugo 快速开始

1. [hugo 官网](https://gohugo.io)

2. 点击 Quick Start

3. 按官方教程一步步做

#### 注意事项：

1. 步骤 2 quickstart 文件夹命名更改格式: 你的 github 用户名.github.io-xxx

2. 步骤 3 可以更改博客主题，新手不建议更改

hugo 操作完毕。

### 上传至 GitHub\*\*

1. 到你创建博客文件夹的根目录创建一个文件,命名为.gitignore,在里面输入/public/

2. 进入 public 文件夹,输入下列代码

```
git init

git add.

git commit -v
```

3. 进入 githua 创建一个新的仓库，命名规则: 用户名.github.io
4. 复制 github 里面的俩行代码即可部署完成

```
git remote add origin
git push -u origin master
```

5. 进入 setting 查看部署完成链接

### Github 备份你的博客代码

1. github 创建一个新的仓库
2. 复制那俩行代码即可

### Github 更新你的代码

```
git status
git add .
git commit -v
git pull
git push origin master
```
