### Aguer Hugo 

# I. Simplest LAN
1. Quelques pings

🌞 Prouvez que votre configuration est effective
```powershell
PS C:\Windows\system32> Get-NetIPAddress -InterfaceAlias "Ethernet"
```
```Powershell
IPAddress         : fe80::e789:73b9:7261:d95b%6
InterfaceIndex    : 6
InterfaceAlias    : Ethernet
AddressFamily     : IPv6
Type              : Unicast
PrefixLength      : 64
PrefixOrigin      : WellKnown
SuffixOrigin      : Link
AddressState      : Deprecated
ValidLifetime     :
PreferredLifetime :
SkipAsSource      : False
PolicyStore       : ActiveStore

IPAddress         : 169.254.86.6
InterfaceIndex    : 6
InterfaceAlias    : Ethernet
AddressFamily     : IPv4
Type              : Unicast
PrefixLength      : 16
PrefixOrigin      : WellKnown
SuffixOrigin      : Link
AddressState      : Tentative
ValidLifetime     :
PreferredLifetime :
SkipAsSource      : False
PolicyStore       : ActiveStore

IPAddress         : 10.100.100.13
InterfaceIndex    : 6
InterfaceAlias    : Ethernet
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
🌞 Tester que votre LAN + votre adressage IP est fonctionnel
```powershell
PS C:\Windows\system32> ping 10.100.100.14
```
Résultat
```powershell
Envoi d’une requête 'Ping'  10.100.100.14 avec 32 octets de données :
Réponse de 10.100.100.14 : octets=32 temps=3 ms TTL=64
Réponse de 10.100.100.14 : octets=32 temps=3 ms TTL=64
Réponse de 10.100.100.14 : octets=32 temps=4 ms TTL=64
Réponse de 10.100.100.14 : octets=32 temps=3 ms TTL=64

Statistiques Ping pour 10.100.100.14:
    Paquets : envoyés = 4, reçus = 4, perdus = 0 (perte 0%),
Durée approximative des boucles en millisecondes :
    Minimum = 3ms, Maximum = 4ms, Moyenne = 3ms
```
# II. Utilisation des ports
1. Animal numérique
```powershell 
  TCP    0.0.0.0:9999           0.0.0.0:0              LISTENING
 [nc.exe]
 ```
 🌞 Sur le PC client

 ```powershell
 PS C:\Users\hugoa\Downloads\netcat-win32-1.11 (1)\netcat-1.11> .\nc.exe 10.100.100.14 9999
salut
a
a
a
a
```
🌞 Utilisez une commande qui permet de voir la connexion en cours
```powershell
PS C:\Windows\system32> netstat -abn | findstr "9999"
```
Résultat
```powershell
  TCP    10.100.100.13:48885    10.100.100.14:9999     ESTABLISHED
  ```
  🌞 Inversez les rôles
  ```powershell
PS C:\Users\hugoa\Downloads\netcat-win32-1.11 (1)\netcat-1.11> .\nc.exe  -l -p 48885
salut
salut
salut
a
```
