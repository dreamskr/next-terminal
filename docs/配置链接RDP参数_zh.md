


| 参数 | 说明 | 是否必须 |
| -------- | -------- | -------- |
| hostname | RDP服务器主机名或IP地址 | 必须 |
| port | RDP服务器端口。默认3389 |  |
| 认证和安全 |
| username | 用于验证的用户名。此参数是可选的。 | NLA，必须 |
| password | 尝试身份验证时使用的密码。此参数是可选的。 | NLA，必须 |
| domain | 尝试身份验证时使用的域。此参数是可选的 |  |
| security | RDP连接加密方式。默认使用标准RDP加密方式。可选参数：rdp,nla,tls,any | 建议设置tls |
| ignore-cert | 如果设置为true，忽略服务器返回的证书。 | 建议true |
| disable-auth | 如果设置为“true”，认证将被禁用。请注意，这是指在连接时进行的身份验证。服务器通过远程桌面会话执行的任何身份验证（如登录对话框）仍然会发生。默认情况下，启用身份验证，并仅在服务器请求时使用。如果使用NLA，则必须通过定义启用身份验证。 |  |
| 会话设置 |
| client-name | 当连接到RDP服务器时，Guacamole通常会提供自己的主机名作为客户端的名称。如果指定了此参数，Guacamole将使用其值。在Windows RDP服务器上，该值在会话中作为CLIENTNAME环境变量显示。 |  |
| console | 如果设置为“true”，则将连接到RDP服务器的控制台（管理员）会话。 |  |
| initial-program | 程序连接后立即运行的完整路径。此参数是可选的。 |  |
| server-layout | 服务器端键盘布局。这是RDP服务器的布局，与客户端上使用的键盘布局无关。Guacamole客户端与键盘布局无关。然而，RDP协议 并不独立于键盘布局，Guacamole需要知道服务器的键盘布局，以便在用户打字时发送正确的键。默认情况下，将使用美国英语qwerty键盘。 |  |
| 显示设置 |
| color-depth | 请求的颜色深度，以像素为单位。此参数是可选的。如果指定，则必须是8,16或24.无论此处选择什么值，如果特定更新使用少于256种颜色，Guacamole将始终将该更新作为256色PNG发送。 |  |
| width | 要请求的显示器的宽度，以像素为单位。此参数是可选的。如果未指定此值，则将使用连接客户端显示的宽度 |  |
| height | 要显示的高度，以像素为单位。此参数是可选的。如果未指定此值，则将使用连接客户端显示的高度。 |  |
| dpi | 在DPI中显示客户端所需的有效分辨率。此参数是可选的。如果未指定此值，则客户端显示的分辨率和大小将一起使用，以启发式地确定RDP会话的适当分辨率。 |  |
| resize-method | 当客户端显示的宽度或高度发生变化时，用于更新RDP服务器的方法。此参数是可选的。如果未指定此值，则当客户端显示更改大小时，不会执行任何操作。可选参数：display-update、reconnect |  |
| 设备重定向 |
| disable-audio | 默认情况下，客户端和libguac-client-rdp都会启用音频。如果您关心带宽使用情况或声音导致问题，您可以通过将此参数设置为“true”来显式禁用声音。 |  |
| enable-audio-input | 如果设置为“true”，则会启用音频输入支持（麦克风），利用RDP的标准“AUDIO_INPUT”通道。默认情况下，RDP中的音频输入支持被禁用。 |  |
| enable-printing | 默认情况下禁用打印，但启用打印功能后，RDP用户可以打印到发送包含打印到Guacamole客户端的文档的PDF的虚拟打印机。通过将此参数设置为“true”来启用打印。打印支持需要 安装GhostScript。如果在打印时 guacd找不到 gs可执行文件，打印尝试将失败。 |  |
| enable-drive | 默认情况下禁用文件传输，但启用文件传输后，RDP用户可以将文件传输到持久存在于Guacamole服务器上的虚拟驱动器。通过将此参数设置为“true”来启用文件传输支持。文件将存储在由“ drive-path”参数指定的目录中，如果启用了文件传输，则该参数是必需的。 |  |
| drive-path | Guacamole服务器上应存储传输文件的目录。该目录必须对guacd可访问，并且对运行guacd的用户可读写。此参数不指RDP服务器上的目录。如果文件传输未启用，则此参数将被忽略。 |  |
| create-drive-path | 如果设置为“true”，并且启用了文件传输，同时drive-path 该参数不存在，则该参数指定的目录将自动创建。将只创建路径中的最终目录 - 如果路径之前的其他目录不存在，则自动创建将失败，并会记录错误。默认情况下，该drive-path参数指定的目录 将不会自动创建，并且尝试将文件传输到不存在的目录将被记录为错误。如果文件传输未启用，则此参数将被忽略。 |  |
| console-audio | 如果设置为“true”，则在RDP服务器的控制台（admin）会话中将显式启用音频。将此选项设置为“true”仅在console参数也设置为“true”的情况下才有意义 。 |  |
| static-channels | 以逗号分隔的静态通道名称列表打开并显示为管道。如果您希望在远程桌面上运行的应用程序和JavaScript之间进行通信，则这是最好的方式。鳄梨酱将打开一个带有静态通道名称的出站管道。如果JavaScript需要在另一个方向进行通信，则应该通过打开具有相同名称的另一个管道来进行响应。Guacamole允许打开任意数量的静态通道，但RDP的协议限制将每个通道名称的大小限制为7个字符。 |  |
| 预连接PDU（Hyper-V）|
| preconnection-id | RDP源的数字ID。这是一个非负整数值，指定应使用潜在的几个逻辑RDP连接。此参数是可选的，仅当RDP服务器被记录为需要时才需要此参数。如果使用Hyper-V，这应该留空。 |  |
| preconnection-blob | 标识RDP源的任意字符串 - 由相同RDP服务器托管的潜在的几个逻辑RDP连接之一。此参数是可选的，只有当RDP服务器被记录为需要它时才需要，如Hyper-V。在所有情况下，此参数的含义对于RDP协议本身是不透明的，由RDP服务器决定。对于Hyper-V，这将是目标虚拟机的ID。 |  |
| 远程桌面网关 |
| gateway-hostname | 用作远程桌面连接中介的远程桌面网关的主机名。如果省略，则不会使用网关。 |  |
| gateway-port | 远程桌面网关的端口，用作远程桌面连接的中介。默认情况下，这将是“443”。如果在1.2之前使用FreeRDP版本，则此设置无效。旧版本的FreeRDP使用硬编码值“443”。 |  |
| gateway-username | 如果正在使用网关，则使用远程桌面网关进行身份验证的用户名。不一定与实际使用远程桌面连接的用户相同。 |  |
| gateway-password | 使用远程桌面网关进行身份验证时提供的密码 |  |
| gateway-domain | 用户使用远程桌面网关进行认证的域。不一定与用户实际使用远程桌面连接相同。 |  |
| 负载均衡和RDP连接代理 |
| load-balancing-info | 提供给连接代理的负载均衡信息或cookie。如果没有连接代理，这里应该为空 |  |
| 性能标识 |
| enable-wallpaper | 如果设置为true，则开启桌面壁纸渲染。默认为不开启 |  |
| enable-wallpaper | 如果设置为true，则开启窗口和控件的主题。默认为不开启 |  |
| enable-font-smoothing | 如果设置为“true”，文本将以平滑的边缘呈现。默认情况下，RDP上的文本粗体呈现，因为这减少了文本使用的颜色数量，从而减少了连接所需的带宽。 |  |
| enable-full-window-drag | 如果设置为“true”，窗口的内容将随着窗口的移动而显示。默认情况下，RDP服务器将仅在窗口拖动时绘制窗口边框。 |  |
| enable-desktop-composition | 如果设置为“true”，则允许使用透明窗口和阴影等图形效果。默认情况下，此类效果（如果可用）被禁用。 |  |
| enable-menu-animations | 如果设置为“true”，菜单开启和关闭动画将被允许。默认情况下禁用菜单动画 |  |
| RemoteApp |
| remote-app | 指定RemoteApp在远程桌面上启动。如果您的远程桌面服务器支持，则该应用程序以及只有此应用程序将对用户可见。Windows需要对远程应用程序的名称的特殊符号。远程应用程序的名称必须带有两个竖条。例如，如果您已在服务器上创建了一个远程应用程序并为其 notepad.exe分配了名称“notepad”，则可以将此参数设置为：“|| notepad”。 |  |
| remote-app-dir | 用于远程应用程序的工作目录（如果有）。如果RemoteApp不在使用中，则此参数无效。 |  |
| remote-app-args | 用于远程应用程序的命令行参数（如果有）。如果RemoteApp不在使用中，则此参数无效。 |  |


## Notice:

### 1. 预连接PDU（Hyper-V）

一些RDP服务器在单个服务器后面托管多个逻辑RDP连接，在单个TCP端口上侦听。要在这些逻辑连接之间进行选择，RDP客户端必须发送“预连接PDU” - 包含唯一标识目的地的值的消息，称为“RDP源”。

如果使用预连接PDU需要注意：

##### 1.设置“ port”为“ 2179”，因为这是Hyper-V使用的默认端口。标准RDP端口为3389，Guacamole将使用端口3389，除非指定了不同的值。
##### 2.适当地指定“ username”和“ password”，并将“ security” 设置为“ nla”或“ any”。Hyper-V要求连接客户端进行网络级认证。Guacamole的默认设置是使用标准RDP加密，而不使用Hyper-V不支持的网络级认证。
##### 3.如有必要，请将“ ignore-cert” 设置为“ true”。Hyper-V可能使用自签名证书。

### 2. 设备重定向

设备重定向是指通过RDP使用非显示设备。Guacamole的RDP支持目前允许重定向音频，打印和磁盘访问，其中一些需要额外的配置才能正常运行。

默认情况下，音频重定向将被启用。如果Guacamole正确安装，并且您的RDP服务器支持音频重定向，则声音应在远程连接中播放，无需手动干预。

打印需要在Guacamole服务器上安装GhostScript，并允许用户将任意文档直接打印到PDF。当文档打印到重定向打印机时，用户将在其Web浏览器中收到该文档的PDF。

Guacamole通过模拟虚拟磁盘驱动器提供对RDP文件传输的支持。该驱动器将持续在Guacamole服务器上，限于指定的驱动器路径。如果在Guacamole SSH连接上启用了驱动器重定向，则用户将能够上传和下载文件。

如果你的服务驱动重定向失败可能存在动态库加载错误查询日志

```
Failed to load guacdr plugin. Drive redirection and printing will not work. Sound MAY not work.
Failed to load guacsnd alongside guacdr plugin. Sound will not work. Drive redirection and printing MAY not work.
```
centos7 解决方法

```
ln -s /usr/local/lib/freerdp/guacdr.so /usr/lib64/freerdp/
ln -s /usr/local/lib/freerdp/guacsnd.so /usr/lib64/freerdp/
```

debian 解决方法

```
mkdir -p /usr/lib/x86_64-linux-gnu/freerdp
ln -s /usr/local/lib/freerdp/guacsnd-client.so /usr/lib/x86_64-linux-gnu/freerdp/guacsnd-client.so
ln -s /usr/local/lib/freerdp/guacdr-client.so /usr/lib/x86_64-linux-gnu/freerdp/guacdr-client.so
```
