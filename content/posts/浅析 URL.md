---
title: "浅析URL"
date: 2019-12-28T13:12:19+08:00
draft: false
---

#### 一. URL 有哪几部分？

URL 包括 "协议+域名或 IP+端口号+路径+查询字符串+锚点"
![URL](/images/url.gif)

**http：//或 https：//**

"http"代表超文本传输 ​​ 协议。让浏览器知道它将使用哪种协议来访问 domain 中指定的信息。“ https”协议是“超文本传输 ​​ 协议安全”的缩写，表示通过 HTTP 传输的信息已加密且安全。在 http 或 https 之后是冒号（：）和两个正斜杠（//），用于将协议与 URL 的其余部分分隔开。

**www**

接下来，“ www”代表万维网，用于区分内容。URL 的这一部分不是必需的，可以省去很多次。例如，键入“ http://computerhope.com ”仍然可以将您带到 Computer Hope 网站。地址的这一部分也可以代替重要的子页面，称为 subdomain。

**computerhope.com**

接下来，“ computerhope.com”是网站的域名。域的最后一部分称为域后缀，即 TLD。它用于标识网站的类型或位置。例如，“。com”是商业名称的缩写，“。org”是组织的缩写，“。co.uk”是英国。还有许多其他域后缀可用。要获取域名，您可以通过域名注册商注册名称。

**/jargon/u/**
接下来的“行话”和上述网址的“U”形部分是目录在网页所在的服务器上。在此示例中，网页有两个目录，因此，如果您尝试在服务器上查找文件，则该文件将位于/public_html/jargon/u 目录中。对于大多数服务器，public_html 目录是包含 HTML 文件的默认目录。

**url.htm**

最后，url.htm 是您正在查看的域上的实际网页。尾随的.htm 是网页的文件扩展名，指示该文件是 HTML 文件。Internet 上的其他常见文件扩展名包括.html，.php，.asp，.cgi，.xml，.jpg 和.gif。这些文件扩展名中的每一个都执行不同的功能，就像计算机上所有不同类型的文件一样。

#### 二. DNS 的作用是什么，nslookup 命令怎么用

**DNS**

域名系统（DNS）是 Internet 的电话簿。人们通过域名（例如 nytimes.com 或 espn.com）在线访问信息。Web 浏览器通过 Internet 协议（IP）地址进行交互。DNS 将域名转换为 IP 地址，以便浏览器可以加载 Internet 资源。

连接到 Internet 的每个设备都有一个唯一的 IP 地址，其他计算机可使用该 IP 地址查找该设备。DNS 服务器消除了人们存储 IP 地址（例如 192.168.1.1（在 IPv4 中））或更复杂的较新的字母数字 IP 地址（例如 2400：cb00：2048：1 :: c629：d7a2（在 IPv6 中））的需要。

**nslookup 命令**

Nslookup –它是一个功能强大的网络管理命令行工具，用于查询域名系统（DNS）以获取域名或 IP 地址，映射或其他任何特定的 DNS 记录。

**主要用于:**

- 查找主机的 IP 地址。
- 查找 IP 地址的域名。
- 查找域的邮件服务器。
  ![URL](/images/nslookup命令.png)

#### 三. IP 的作用是什么，ping 命令怎么用

**IP (Internet Protocol)** 地址是网络硬件的地址。它有助于将计算机连接到网络上以及全球的其他设备。IP 地址由数字或字符组成。
**Ping 命令**
![URL](/images/ping.png)

**ping**命令通常用作验证计算机通过网络与另一台计算机或网络设备通信的简单方法。

#### 四. 域名是什么，分别哪几类域名

1. 域名可以说是一个 IP 地址的代称，目的是为了便于记忆后者。(qq.com,baidu.com 就是域名)
2. 域名主要有三类：
   - 一级域名
   - 二级域名
   - 三级域名

例如：

www.xiedaimala.com 是二级域名(俗称一级域名)

xiedaimala.com 是三级域名(俗称二级域名)
