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
