I.Récolte d'informations

🌞 Adresses IP de ta machine
```powershell

PS C:\Users\hugoa> ipconfig

Carte réseau sans fil Wi-Fi :

   Suffixe DNS propre à la connexion. . . :
   Adresse IPv6 de liaison locale. . . . .: fe80::2926:efc4:87ac:1d25%10
   Adresse IPv4. . . . . . . . . . . . . .: 10.33.77.164
   Masque de sous-réseau. . . . . . . . . : 255.255.240.0
   Passerelle par défaut. . . . . . . . . : 10.33.79.254

PS C:\Users\hugoa> ipconfig

Carte Ethernet Ethernet :

   Statut du média. . . . . . . . . . . . : Média déconnecté
   Suffixe DNS propre à la connexion. . . :
```
-----------------------------------------------------------------------------------------------------------------
🌞 Si t'as un accès internet normal, d'autres infos sont forcément dispos...
```powershell

PS C:\Users\hugoa> ipconfig /all

Carte réseau sans fil Wi-Fi :

   Suffixe DNS propre à la connexion. . . :
   Description. . . . . . . . . . . . . . : Intel(R) Wi-Fi 6E AX211 160MHz
   Adresse physique . . . . . . . . . . . : D4-E9-8A-61-17-A0
   DHCP activé. . . . . . . . . . . . . . : Oui
   Configuration automatique activée. . . : Oui
   Adresse IPv6 de liaison locale. . . . .: fe80::2926:efc4:87ac:1d25%10(préféré)
   Adresse IPv4. . . . . . . . . . . . . .: 10.33.77.164(préféré)
   Masque de sous-réseau. . . . . . . . . : 255.255.240.0
   Bail obtenu. . . . . . . . . . . . . . : jeudi 26 septembre 2024 08:58:03
   Bail expirant. . . . . . . . . . . . . : samedi 28 septembre 2024 08:41:42
   Passerelle par défaut. . . . . . . . . : 10.33.79.254
   Serveur DHCP . . . . . . . . . . . . . : 10.33.79.254
   IAID DHCPv6 . . . . . . . . . . . : 97839498
   DUID de client DHCPv6. . . . . . . . : 00-01-00-01-2E-68-7F-B4-D4-93-90-39-C2-6B
   Serveurs DNS. . .  . . . . . . . . . . : 8.8.8.8
                                       1.1.1.1
   NetBIOS sur Tcpip. . . . . . . . . . . : Activé
```
---------------------------------------------------------------------------------------------------------
🌟 BONUS : Détermine s'il y a un pare-feu actif sur ta machine
```powershell

PS C:\Users\hugoa> Get-NetFirewallProfile | ft Name,Enabled


Name    Enabled
----    -------
Domain     True
Private    True
Public     True


PS C:\Users\hugoa> Get-NetFirewallRule

Name                          : WFDPRINT-SPOOL-Out-Active
DisplayName                   : Utilisation de spouleur Wi-Fi Direct (Sortie)
Description                   : Règle de trafic sortant relative à l’utilisation d’imprimantes WSD sur des réseaux Wi-Fi Direct.
DisplayGroup                  : Découverte de réseau Wi-Fi Direct
Group                         : @FirewallAPI.dll,-36851
Enabled                       : True
Profile                       : Public
Platform                      : {}
Direction                     : Outbound
Action                        : Allow
EdgeTraversalPolicy           : Block
LooseSourceMapping            : False
LocalOnlyMapping              : False
Owner                         :
PrimaryStatus                 : OK
Status                        : La règle a été analysée à partir de la banque. (65536)
EnforcementStatus             : NotApplicable
PolicyStoreSource             : PersistentStore
PolicyStoreSourceType         : Local
RemoteDynamicKeywordAddresses : {}
PolicyAppId                   :
```
------------------------------------------------------------------------------------------------------------
II.Utiliser le réseau
🌞 Envoie un ping vers...
```powershell


PS C:\Users\hugoa> ping  10.33.77.164

Envoi d’une requête 'Ping'  10.33.77.164 avec 32 octets de données :
Réponse de 10.33.77.164 : octets=32 temps<1ms TTL=128
Réponse de 10.33.77.164 : octets=32 temps<1ms TTL=128
Réponse de 10.33.77.164 : octets=32 temps<1ms TTL=128
Réponse de 10.33.77.164 : octets=32 temps<1ms TTL=128

Statistiques Ping pour 10.33.77.164:
    Paquets : envoyés = 4, reçus = 4, perdus = 0 (perte 0%),
Durée approximative des boucles en millisecondes :
    Minimum = 0ms, Maximum = 0ms, Moyenne = 0ms


PS C:\Users\hugoa> ping 127.0.0.1

Envoi d’une requête 'Ping'  127.0.0.1 avec 32 octets de données :
Réponse de 127.0.0.1 : octets=32 temps<1ms TTL=128
Réponse de 127.0.0.1 : octets=32 temps<1ms TTL=128
Réponse de 127.0.0.1 : octets=32 temps<1ms TTL=128
Réponse de 127.0.0.1 : octets=32 temps<1ms TTL=128

Statistiques Ping pour 127.0.0.1:
    Paquets : envoyés = 4, reçus = 4, perdus = 0 (perte 0%),
Durée approximative des boucles en millisecondes :
    Minimum = 0ms, Maximum = 0ms, Moyenne = 0ms
```
 -------------------------------------------------------------------------------------------------------
 🌞 On continue avec ping. Envoie un ping vers...  
 ```powershell
   

 PS C:\Users\hugoa> ping 10.33.77.254

 Envoi d’une requête 'Ping'  10.33.77.254 avec 32 octets de données :
Réponse de 10.33.77.164 : Impossible de joindre l’hôte de destination.
Réponse de 10.33.77.164 : Impossible de joindre l’hôte de destination.
Réponse de 10.33.77.164 : Impossible de joindre l’hôte de destination.
Réponse de 10.33.77.164 : Impossible de joindre l’hôte de destination.

Statistiques Ping pour 10.33.77.254:
    Paquets : envoyés = 4, reçus = 4, perdus = 0 (perte 0%),

PS C:\Users\hugoa> ping 10.33.77.208

Envoi d’une requête 'Ping'  10.33.77.208 avec 32 octets de données :
Réponse de 10.33.77.208 : octets=32 temps=5 ms TTL=128
Réponse de 10.33.77.208 : octets=32 temps=7 ms TTL=128
Réponse de 10.33.77.208 : octets=32 temps=6 ms TTL=128
Réponse de 10.33.77.208 : octets=32 temps=5 ms TTL=128

Statistiques Ping pour 10.33.77.208:
    Paquets : envoyés = 4, reçus = 4, perdus = 0 (perte 0%),
Durée approximative des boucles en millisecondes :
    Minimum = 5ms, Maximum = 7ms, Moyenne = 5ms

PS C:\Users\hugoa> ping youtube.com

Envoi d’une requête 'ping' sur youtube.com [142.250.203.238] avec 32 octets de données :
Réponse de 142.250.203.238 : octets=32 temps=16 ms TTL=113
Réponse de 142.250.203.238 : octets=32 temps=16 ms TTL=113
Réponse de 142.250.203.238 : octets=32 temps=15 ms TTL=113
Réponse de 142.250.203.238 : octets=32 temps=16 ms TTL=113

Statistiques Ping pour 142.250.203.238:
    Paquets : envoyés = 4, reçus = 4, perdus = 0 (perte 0%),
Durée approximative des boucles en millisecondes :
    Minimum = 15ms, Maximum = 16ms, Moyenne = 15ms



```

------------------------------------------------------------------------------------------------------
🌞 Faire une requête DNS à la main
```powershell

PS C:\Users\hugoa> nslookup 

Serveur par dÚfaut :   dns.google
Address:  8.8.8.8

>


PS C:\Users\hugoa> nslookup www.thinkerview.com

Serveur :   dns.google
Address:  8.8.8.8

Réponse ne faisant pas autorité :
Nom :    www.thinkerview.com
Addresses:  2a06:98c1:3121::7
          2a06:98c1:3120::7
          188.114.96.7
          188.114.97.7

PS C:\Users\hugoa> nslookup www.wikileaks.org

Serveur :   dns.google
Address:  8.8.8.8

Réponse ne faisant pas autorité :
Nom :    wikileaks.org
Addresses:  51.159.197.136
          80.81.248.21
Aliases:  www.wikileaks.org

PS C:\Users\hugoa> nslookup www.torproject.org

Serveur :   dns.google
Address:  8.8.8.8

Réponse ne faisant pas autorité :
Nom :    www.torproject.org
Addresses:  2620:7:6002:0:466:39ff:fe7f:1826
          2a01:4f9:c010:19eb::1
          2620:7:6002:0:466:39ff:fe32:e3dd
          2a01:4f8:fff0:4f:266:37ff:feae:3bbc
          2a01:4f8:fff0:4f:266:37ff:fe2c:5d19
          116.202.120.165
          95.216.163.36
          204.8.99.146
          116.202.120.166
          204.8.99.144

```
-------------------------------------------------------------------------------------------------------------------       
III. Sniffer le réseau  
🌞 Effectue un scan du réseau auquel tu es connecté
```powershell

PS C:\Users\hugoa> nmap.exe -sn -PR  192.168.1.0/24
Starting Nmap 7.95 ( https://nmap.org ) at 2024-10-06 16:35 Paris, Madrid (heure dÆÚtÚ)
Nmap scan report for 192.168.1.3
Host is up (0.083s latency).
MAC Address: 44:6F:F8:0B:53:89 (Dyson Limited)
Nmap scan report for 192.168.1.4
Host is up (0.014s latency).
MAC Address: 60:AB:D2:A9:67:16 (Bose)
Nmap scan report for 192.168.1.22
Host is up (0.17s latency).

```
>#### Comme les adresse ip entre la 192.168.1.4 et 192.168.1.22 ne sont pas apparuent , alors j'en déduis que elles ne sont pas attribuées.Donc pour la suite je vais modifier mon adresse ip par 192.168.1.13 :
🌞 Changer d'adresse IP
```powershell

PS C:\Windows\system32> New-NetIPAddress -InterfaceAlias Wi-Fi -IPAddress 192.168.1.13 -PrefixLength 24 -DefaultGateway 192.168.1.254


IPAddress         : 192.168.1.13
InterfaceIndex    : 10
InterfaceAlias    : Wi-Fi
AddressFamily     : IPv4
Type              : Unicast
PrefixLength      : 24
PrefixOrigin      : Manual
SuffixOrigin      : Manual
AddressState      : Tentative
ValidLifetime     :
PreferredLifetime :
SkipAsSource      : False
PolicyStore       : ActiveStore

```
