TP 5 AGUER HUGO

I. Setup
```powershell
☀️ Uniquement avec des commandes, prouvez-que :
```
```powershell
Routeur:
2: enp0s8: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc fq_codel state UP group default qlen 1000
link/ether 08:00:27:62:e8:0e brd ff:ff:ff:ff:ff:ff
inet 10.5.1.254/24 brd 10.5.1.255 global nopref ixroute enp0s8
```
```powershell
Client 1
2: enp0s8: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc fq_codel state UP group default qlen 1000
link/ether 08:00:27:84:cb:c6 brd ff:ff:ff:ff:ff:ff
inet 10.5.1.11/24 brd 10.5.1.255 scope global enp0s8
```
```powershell
Client 2
2: enp0s8: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc fq_codel state UP group default qlen 1000
link/ether 08:00:27:ef:cd:69 brd ff:ff:ff:ff:ff:ff
inet 10.5.1.12/24 brd 10.5.1.255 scope global enp0s8
```
Ping client 2 vers client 1
hugo@hugo-VirtualBox:~$ ping 10.5.1.11
PING 10.5.1.11 (10.5.1.11) 56(84) bytes of data
64 bytes from 10.5.1.11: icmp_seq=1 ttl=64 time=15.2 ms
64 bytes from 10.5.1.11 icmp_seq=2 ttl=64 time=1.68 ms
64 bytes from 10.5.1.11: icmp_seq=3 ttl=64 time=2.03 ms
64 bytes from 10.5.1.11: icmp_seq=4 ttl=64 time=2.33 ms
```
