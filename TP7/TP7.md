➜ On démarre le service web NGINX
```powershell
🌞 Lister les ports en écoute sur la machine
```
```powershell
[root@web hugoa]# sudo ss -lnpt | grep nginx
LISTEN 0      511          0.0.0.0:80        0.0.0.0:*    users:(("nginx",pid=1686,fd=6),("nginx",pid=1685,fd=6),("nginx",pid=1684,fd=6))
LISTEN 0      511             [::]:80           [::]:*    users:(("nginx",pid=1686,fd=7),("nginx",pid=1685,fd=7),("nginx",pid=1684,fd=7))
```
```powershell
🌞 Ouvrir le port dans le firewall de la machine
```
```powershell
[root@web hugoa]# sudo firewall-cmd --permanent --add-port=80/tcp
success
```
```powershell
[root@web hugoa]# sudo firewall-cmd --reload
success
```
C. Tests client
```powershell
🌞 Vérifier que ça a pris effet
```
```powershell
hugo@client1:~$ ping sitedefou.tp7.b1
PING sitedefou.tp7.b1 (10.7.1.11) 56(84) bytes of data.
64 bytes from sitedefou.tp7.b1 (10.7.1.11): icmp_seq=1 ttl=64 time=1.14 ms
64 bytes from sitedefou.tp7.b1 (10.7.1.11): icmp_seq=2 ttl=64 time=0.419 ms
64 bytes from sitedefou.tp7.b1 (10.7.1.11): icmp_seq=3 ttl=64 time=4.25 ms
64 bytes from sitedefou.tp7.b1 (10.7.1.11): icmp_seq=4 ttl=64 time=1.54 ms
^C
--- sitedefou.tp7.b1 ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 3148ms
rtt min/avg/max/mdev = 0.419/1.835/4.250/1.450 ms
```
```powershell
hugo@client1:~$ curl sitedefou.tp7.b1
meow !
```
D. Analyze
```powershell
🌞 Capture tcp_http.pcap
```
```powershell
🌞 Voir la connexion établie
```
```powershell
hugo@client1:~$ ss -t -a
```
```powershell
ESTAB           0               0                                   10.7.1.101:50254                              10.7.1.11:http

```
```powershell
hugo@client1:~$ curl http://sitedefou.tp7.b1
meow !
```
2. On rajoute un S
A. Config
```powershell
🌞 Lister les ports en écoute sur la machine
```
```powershell
[root@web hugoa]# sudo ss -lnpt
State    Recv-Q   Send-Q     Local Address:Port      Peer Address:Port   Process
LISTEN   0        511            10.7.1.11:443            0.0.0.0:*       users:(("nginx",pid=1473,fd=6),("nginx",pid=1472,fd=6),("nginx",pid=1471,fd=6))
```
🌞 Gérer le firewall
```powershell
[root@web hugoa]# sudo firewall-cmd --permanent --add-port=443/tcp
success
```
```powershell
[root@web hugoa]# sudo firewall-cmd --reload
success
```
```powershell
[root@web hugoa]# sudo firewall-cmd --permanent --remove-port=80/tcp
success
```
```powershell
[root@web hugoa]# sudo firewall-cmd --reload
success
```
III. Serveur VPN
1. Install et conf Wireguard
```powershell
🌞 Prouvez que vous avez bien une nouvelle carte réseau wg0
```powershell
[root@vpn hugoa]# ip a
```
```powershell  
       valid_lft forever preferred_lft forever
4: wg0: <POINTOPOINT,NOARP,UP,LOWER_UP> mtu 1420 qdisc noqueue state UNKNOWN group default qlen 1000
    link/none
    inet 10.7.200.1/24 scope global wg0
       valid_lft forever preferred_lft forever
```
🌞 Déterminer sur quel port écoute Wireguard
```powershell
[root@vpn hugoa]# sudo ss -lnpu | grep 51820
State          Recv-Q         Send-Q                 Local Address:Port                  Peer Address:Port        Process

UNCONN         0              0                            0.0.0.0:51820                      0.0.0.0:*

UNCONN         0              0                               [::]:51820                         [::]:*
```
🌞 Ouvrez ce port dans le firewall
```powershell
[root@vpn hugoa]# sudo sysctl -w net.ipv4.ip_forward=1
net.ipv4.ip_forward = 1
[root@vpn hugoa]# sudo sysctl -w net.ipv6.conf.all.forwarding=1
net.ipv6.conf.all.forwarding = 1
[root@vpn hugoa]# sudo firewall-cmd --add-interface=wg0 --zone=public --permanent
success
[root@vpn hugoa]# sudo firewall-cmd --add-masquerade --permanent
success
[root@vpn hugoa]# sudo firewall-cmd --reload
success
```
2. Ajout d'un client VPN
