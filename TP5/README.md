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
```powershell
Ping client 2 vers client 1
hugo@hugo-VirtualBox:~$ ping 10.5.1.11
PING 10.5.1.11 (10.5.1.11) 56(84) bytes of data
64 bytes from 10.5.1.11: icmp_seq=1 ttl=64 time=15.2 ms
64 bytes from 10.5.1.11 icmp_seq=2 ttl=64 time=1.68 ms
64 bytes from 10.5.1.11: icmp_seq=3 ttl=64 time=2.03 ms
64 bytes from 10.5.1.11: icmp_seq=4 ttl=64 time=2.33 ms
```
II. Accès internet pour tous
1. Accès internet routeur
```powershell
☀️ Déjà, prouvez que le routeur a un accès internet
```
```powershell
hugo@hugo ~]# ping ynov.com
PING ynov.com (104.26.11.233) 56(84) bytes of data.
64 bytes from 104.26.11.233 (104.26.11.233): icmp_seq=1 ttl=46 time=35.5 ms
64 bytes from 104.26.11.233 (104.26.11.233): icmp_seq=2 ttl=46 time=34.0 ms
64 bytes from 104.26.11.233 (104.26.11.233): icmp_seq=3 ttl=46 time=33.3 ms
--- ynov.com ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2028ms
rtt min/avg/max/mdev = 33.367/35.587/37.451/1.639 ms
```
2.Accès internet clients
```powershell
☀️ Prouvez que les clients ont un accés internet
```
```powershell
hugo@hugo-VirtualBox:~$ ping www.ynov.com
PING www.ynov.com (104.26.10.233) 56(84) bytes of data.
64 bytes from 104.26.10.233: icmp_seq=1 ttl=51 time=15.6 ms
64 bytes from 104.26.10.233: icmp_seq=2 ttl=51 time=14.8 ms
64 bytes from 104.26.10.233: icmp_seq=3 ttl=51 time=16.1 ms
64 bytes from 104.26.10.233: icmp_seq=4 ttl=51 time=14.6 ms
64 bytes from 104.26.10.233: icmp_seq=5 ttl=51 time=16.2 ms
```
```powershell
☀️ Montrez-moi le contenu final du fichier de configuration de l'interface réseau:
```
```powershell
Client2
hugo@hugo-VirtualBox:~$ cat /etc/netplan/01-netcfg.yaml
network:
  version: 2
  renderer: networkd
  ethernets:
    enp0s3:
      dhcp4: no
      addresses: [10.5.1.12/24]
      gateway4: 10.5.1.254
      nameservers:
        addresses: { 1.1.1.1 }
```
III.Serveur SSH
```powershell
☀️ Sur routeur.tp5.b1, déterminer sur quel port écoute le serveur SSH
```
```powershell
[hugo@hugo ~]# sudo ss -lnpt| grep 22
LISTEN 0      128          0.0.0.0:22        0.0.0.0:*    users:(("sshd",pid=707,fd=3))
LISTEN 0      128             [::]:22           [::]:*    users:(("sshd",pid=707,fd=4))    
```
```powershell
☀️ Sur routeur.tp5.b1, vérifier que ce port est bien ouvert
```
```powershell
[hugo@hugo ~]# sudo firewall-cmd --list-all
public (active)
  target: default
  icmp-block-inversion: no
  interfaces: enp0s3 enp0s8
  sources:
  services: cockpit dhcpv6-client ssh
  ports: 22/tcp
  protocols:
  forward: yes
  masquerade: yes
  forward-ports:
  source-ports:
  icmp-blocks:
  rich rules:
[root@routeur hugo]#
```
IV. Serveur DHCP
1. Le but
```powershell
☀️ Installez et configurez un serveur DHCP sur la machine routeur.tp5.b1
```
```powershell
[hugo@hugo ~]# dnf -y install dhcp-server
[hugo@hugo ~]# sudo nano dhcpd.conf
```