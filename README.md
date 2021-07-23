# Next Terminal

下一代终端。

![Docker image](https://github.com/dushixiang/next-terminal/workflows/Docker%20image/badge.svg?branch=master)

## 快速了解

Next Terminal是使用Golang和React开发的一款HTML5的远程桌面网关，具有小巧、易安装、易使用、资源占用小的特点，支持RDP、SSH、VNC和Telnet协议的连接和管理。

Next Terminal基于 [Apache Guacamole](https://guacamole.apache.org/) 开发，使用到了guacd服务。

目前支持的功能有：

- 授权凭证管理
- 资产管理（支持RDP、SSH、VNC、TELNET协议）
- 指令管理
- 批量执行命令
- 在线会话管理（监控、强制断开）
- 离线会话管理（查看录屏）
- 双因素认证
- 资产标签
- 资产授权
- 多用户&用户分组
- 计划任务

## 在线体验

https://next-terminal.typesafe.cn/

test/test

## 协议与条款

如您需要在企业网络中使用 next-terminal，建议先征求 IT 管理员的同意。下载、使用或分发 next-terminal 前，您必须同意 [协议](./LICENSE) 条款与限制。本项目不提供任何担保，亦不承担任何责任。

## 快速安装

> 本项目未进行严格的安全性测试，不建议部署安装在公网环境。

- [使用docker安装](docs/install-docker.md)
- [原生安装](docs/install-naive.md)
- [FAQ](docs/faq.md)

默认账号密码为 admin/admin

## 相关截图

[截图](docs/screenshot.md)

## 联系方式

- QQ群 938145268

- Telegram

  https://t.me/next_terminal
  
  
  # Guacamole介绍

Guacamole是一个提供了基于HTML5 web应用程序的远程桌面代理服务器。通过使用Guacamole服务器，我们很轻松的在浏览器上远程访问Guacamole代理的主机。

![guacamole架构](https://github.com/TelDragon/guacamole/blob/master/docs/_static/img/guac-arch.png?raw=true)

我们可以在浏览器访问Guacamole页面的时候，此时，浏览器会通过HTTP使用Guacamole协议与Guacamole 服务器中的Web服务器进行连接。Guacamole Web应用会从用户的请求中读取Guacamole协议，并将其转发给guacd（本地Guacamole代理）。Guacd根据web 应用转发过来的Guacamole协议来代替用户连接到远程桌面服务器。在Guacamole Web应用与guacd进行通信的时候，两者均不需要知道实际使用的远程桌面协议是什么，即协议不可知性。

在Guacamole的组成中主要包含如下三部分：

#### Guacamole协议是用于远程显示和事件传输的协议，不实现特定的桌面环境支持，实现了现有远程桌面的超集。
#### guacd是Guacamole的核心，guacd也不了解任何具体的远程桌面协议，而是实现了通过web应用转发的Guacamole协议来确定哪些协议需要加载，哪些参数必须传递给它。
#### web应用程序是Guacamole与用户进行交互的部分。Apache提供了基于Java的编写的Web应用程序，但是这并不代表Guacamole 只支持Java。Guacamole是一个API。
# 文档
[Centos7.2部署guacamloe1.0.0中文文档](https://github.com/TelDragon/guacamole/blob/master/docs/Centos7.2_deploy_guacamole1.0.0_zh.md)

[guacamole连接参数官方文档](http://guacamole.apache.org/doc/gug/configuring-guacamole.html)

[VNC连接参数中文文档](https://github.com/TelDragon/guacamole/blob/master/docs/%E9%85%8D%E7%BD%AE%E9%93%BE%E6%8E%A5VNC%E5%8F%82%E6%95%B0_zh.md)

[RDP连接参数中文文档](https://github.com/TelDragon/guacamole/blob/master/docs/%E9%85%8D%E7%BD%AE%E9%93%BE%E6%8E%A5RDP%E5%8F%82%E6%95%B0_zh.md)

[SSH连接参数中文文档](https://github.com/TelDragon/guacamole/blob/master/docs/%E9%85%8D%E7%BD%AE%E9%93%BE%E6%8E%A5SSH%E5%8F%82%E6%95%B0_zh.md)

[Telnet连接参数中文文档](https://github.com/TelDragon/guacamole/blob/master/docs/%E9%85%8D%E7%BD%AE%E9%93%BE%E6%8E%A5Telnet%E5%8F%82%E6%95%B0_zh.md)

[其它更多参数中文文档](https://github.com/TelDragon/guacamole/blob/master/docs/%E5%85%B6%E4%BB%96%E6%9B%B4%E5%A4%9A%E5%8F%82%E6%95%B0%E9%85%8D%E7%BD%AE_zh.md)

# guacamole用户手册
[guacamole用户手册](https://github.com/TelDragon/guacamole/blob/master/docs/gug/Manual.md)

# 测试界面

在浏览器中打开Guacamole Web应用，地址为http://Guacamole_Server_IP:8080/guacamole

Guacamole登录界面
![guacamole登录界面](https://github.com/TelDragon/guacamole/blob/master/docs/_static/img/Guacamole00.png?raw=true)

下图为guacamole登录后显示的页面。
![guacamole登陆后的界面](https://github.com/TelDragon/guacamole/blob/master/docs/_static/img/Guacamole01.png?raw=true)

下图是“CentOS 7 TigerVNC”连接结果，主要测试TigerVNC,采用VNC协议。
![guacamole_VNC](https://github.com/TelDragon/guacamole/blob/master/docs/_static/img/Guacamole02.png?raw=true)

下图是“Windows 10(Test)”连接的结果展示，测试RDP。
![guacamole_windows](https://github.com/TelDragon/guacamole/blob/master/docs/_static/img/Guacamole03.png?raw=true)

下图是"CentOS SSH"连接结果，测试SSH。
![guacamole_ssh](https://github.com/TelDragon/guacamole/blob/master/docs/_static/img/Guacamole04.png?raw=true)

下图是“Ubuntu x11vnc”，测试x11vnc。
![guacamloe_ubuntu](https://github.com/TelDragon/guacamole/blob/master/docs/_static/img/Guacamole05.png?raw=true)


# 免费和开源
Apache Guacamole始终是免费且开源的软件。它是根据[Apache许可2.0版许可的](http://www.apache.org/licenses/LICENSE-2.0)，并且由使用Guacamole访问他们自己的开发环境的开发人员社区主动维护。

# 开发API文档 (api-documentation)
