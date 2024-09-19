搭建 Shadowsocks-rust， V2ray+ Nginx + WebSocket 和 Reality, Hysteria2 代理脚本，支持 Debian、Ubuntu、Centos，并支持甲骨文ARM平台。

简单点讲，没域名的用户可以安装 Reality 和 hy2 代理，有域名的可以安装 V2ray+ Nginx + WebSocket 代理，各取所需。

# 运行脚本：

```
bash <(curl -Ls https://raw.githubusercontent.com/vb197701/v2-ws/refs/heads/main/tcp-wss.sh)
```
或者
```
wget https://raw.githubusercontent.com/vb197701/v2-ws/refs/heads/main/tcp-wss.sh && bash tcp-wss.sh
```

已测试系统如下：

Debian 9, 10, 11, 12

Ubuntu 16.04, 18.04, 20.04, 22.04

CentOS 7

WSS客户端配置信息保存在：
`cat /usr/local/etc/v2ray/client.json`

Shadowsocks客户端配置信息：
`cat /etc/shadowsocks/config.json`

Reality客户端配置信息保存在：
`cat /usr/local/etc/xray/reclient.json`

Hysteria2客户端配置信息保存在：
`cat /etc/hysteria/hyclient.json`

# 卸载

卸载ss-rust：
```
systemctl stop shadowsocks

rm /usr/local/bin/ssserver

rm /etc/systemd/system/shadowsocks.service

systemctl daemon-reload
```
卸载 v2ray-wss:
```
systemctl stop v2ray

systemctl stop nginx

bash <(curl -L https://raw.githubusercontent.com/v2fly/fhs-install-v2ray/master/install-release.sh) --remove

apt purge nginx -y

systemctl daemon-reload
```
卸载 Reality:
```
systemctl stop xray

bash -c "$(curl -L https://github.com/XTLS/Xray-install/raw/main/install-release.sh)" @ remove
```
卸载 Hysteria2:
```
bash <(curl -fsSL https://get.hy2.sh/) --remove
```

**提醒：连不上的朋友，建议先检查一下服务器自带防火墙有没有关闭？**
