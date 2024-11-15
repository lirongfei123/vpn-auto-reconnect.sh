# 配置
## 查看活跃的连接
nmcli con show --active
## 保存vpn密码
vi /etc/NetworkManager/system-connections/xianggang.nmconnection
```
[vpn]
gateway=XXX.XXX.XXX.XXX
ipsec-enabled=yes
ipsec-esp=aes128-sha1
ipsec-ike=aes128-sha1-modp2048
machine-auth-type=psk
password-flags=0
user=vpnuser
user-auth-type=password
service-type=org.freedesktop.NetworkManager.l2tp

[vpn-secrets]
ipsec-psk=***
password=***

[ipv4]
method=auto
route1=10.1.226.3/32,192.168.42.1
```
# vpn-auto-reconnect.sh

A simple bash script for autoreconnect to OpenVPN via NetworkManager command-line (nmcli).

## Usage:

1. Make the script executable "_chmod +x /path/to/the/vpn-auto-reconnect.sh_"

2. Copy "_vpn-config-sample.sh_" to "_vpn-config.sh_". Simply run "_cp vpn-config-sample.sh vpn-config.sh_".

3. Configure "_vpn-config.sh_". All the needed info on how to do that, is shown in the config comments.

4. _vpn-auto-reconnect.sh start_ -- starts and monitors VPN connection

5. _vpn-auto-reconnect.sh stop_ -- stops the monitor and also the VPN connection

## Source:

nmcli: https://wiki.gnome.org/Projects/NetworkManager/nmcli

Source: http://www.gabsoftware.com/tips/automatically-reconnect-to-your-vpn-on-linux/

Fork from: https://gist.github.com/antoniy/f925ae55410a092c9e75/ with changes for nmcli v0.9.10.

Script tested on fedora 21 with airvpn (OpenVPN).

# vpn-toggle.sh

A simple bash script to toggle an OpenVPN connection on and off via NetworkManager command-line (mncli).

## Usage:

1. Make the script executable "_chmod +x /path/to/the/vpn-toggle.sh_"

2. Copy "_vpn-config-sample.sh_" to "_vpn-config.sh_". Simply run "_cp vpn-config-sample.sh vpn-config.sh_".

3. Configure "_vpn-config.sh_". All the needed info on how to do that, is shown in the config comments.

4. _vpn-toggle.sh_ -- starts or stops your first set VPN connection

