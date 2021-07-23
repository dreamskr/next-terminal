
| 参数 | 说明 | 是否必须 |
| -------- | -------- | -------- |
| 网络参数 |
| hostname | Guacamole应该连接到的SSH服务器的主机名或IP地址。 |   必须   |
| port | SSH服务器正在侦听的端口，通常为22.此参数是可选的。如果未指定，则将使用默认值22。 |  |
| 认证 |
| username | 用于验证的用户名（如果有）。此参数是可选的。如果未指定，连接后将提示您输入用户名。 |  |
| password | 尝试身份验证时使用的密码（如果有）。此参数是可选的。如果未指定，连接后将提示您输入密码。 |  |
| private-key | 用于公钥认证的私钥的全部内容。如果未指定此参数，则不会使用公钥认证。私钥必须采用OpenSSH格式，由OpenSSH ssh-keygen实用程序生成。 |  |
| passphrase | 用于解密私钥以用于公钥认证的密码。如果私钥不需要密码，则不需要此参数。如果私钥需要密码，但不提供此参数，则在连接时将提示用户输入密码。  显示设置 |  |
| 显示设置 |
| color-scheme | 用于SSH连接使用的terminal的配色方案。每个配色方案都会指定终端的默认前景和背景颜色。打印文本时指定颜色的程序将覆盖这些默认值。默认使用灰色字体和黑色背景。可选参数：black-white、gray-black、green-black、white-black |  |
| font-name | 使用的字体名称。该参数为可选的。默认使用monospace字体 |  |
| font-size | 使用的字体大小。默认字体大小为12 |  |
| 运行命令（而不是shell） |
| command | 执行SSH会话的命令（如果有）。此参数是可选的。如果没有指定，SSH会话将使用用户的默认shell。 |  |




* 字体设置

```
mkdir -p /usr/share/fonts/chinese
# 将 simhei.ttf(黑体) 与 simsun.ttc(宋体) 拷贝至此文件夹
ttmkfdir -e /usr/share/X11/fonts/encodings/encodings.dir

vi /etc/fonts/fonts.conf
<dir>/usr/share/fonts/chinese</dir>
fc-cache
fc-list
```
