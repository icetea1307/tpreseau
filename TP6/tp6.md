TP6 : Des bo services dans des bo LANs
I. Le setup







2. Client


```powershell
☀️ Prouvez que...
```
```powershell
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host noprefixroute
       valid_lft forever preferred_lft forever
2: enp0s3: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc fq_codel state UP group default qlen 1000
    link/ether 08:00:27:fd:f8:8b brd ff:ff:ff:ff:ff:ff
    inet 10.6.1.38/24 metric 100 brd 10.6.1.255 scope global dynamic enp0s3
       valid_lft 43037sec preferred_lft 43037sec
    inet6 fe80::a00:27ff:fefd:f88b/64 scope link
       valid_lft forever preferred_lft forever
3: enp0s8: <BROADCAST,MULTICAST> mtu 1500 qdisc noop state DOWN group default qlen 1000
    link/ether 08:00:27:33:f0:db brd ff:ff:ff:ff:ff:ff
```powershell
☀️ Déterminer sur quel port écoute le serveur NGINX
```
```powershell
[root@web ~]# sudo ss -lnpt | grep 80
LISTEN 0      511          0.0.0.0:80        0.0.0.0:*    users:(("nginx",pid=1447,fd=6),("nginx",pid=1446,fd=6),("nginx",pid=1445,fd=6))
LISTEN 0      511             [::]:80           [::]:*    users:(("nginx",pid=1447,fd=7),("nginx",pid=1446,fd=7),("nginx",pid=1445,fd=7))
```