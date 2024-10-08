TP3 Aguer hugo
### I. ARP basics
☀️ Avant de continuer...
```powershell
PS C:\Users\hugoa> ipconfig /all
```
```powershell
  Suffixe DNS propre à la connexion. . . :
   Description. . . . . . . . . . . . . . : Intel(R) Wi-Fi 6E AX211 160MHz
   Adresse physique . . . . . . . . . . . : D4-E9-8A-61-17-A0
   ```
   
   ☀️ Affichez votre table ARP

   ```powershell
   PS C:\Users\hugoa> arp -a
   ```
   ```powershell
   Interface : 10.33.77.164 --- 0xa
  Adresse Internet      Adresse physique      Type
  10.33.65.63           44-af-28-c3-6a-9f     dynamique
  10.33.73.77           98-8d-46-c4-fa-e5     dynamique
  10.33.77.160          c8-94-02-f8-ab-97     dynamique
  10.33.79.254          7c-5a-1c-d3-d8-76     dynamique
  10.33.79.255          ff-ff-ff-ff-ff-ff     statique
  224.0.0.22            01-00-5e-00-00-16     statique
  224.0.0.251           01-00-5e-00-00-fb     statique
  224.0.0.252           01-00-5e-00-00-fc     statique
  239.255.255.250       01-00-5e-7f-ff-fa     statique
  255.255.255.255       ff-ff-ff-ff-ff-ff     statique

Interface : 192.168.56.1 --- 0x13
  Adresse Internet      Adresse physique      Type
  192.168.56.255        ff-ff-ff-ff-ff-ff     statique
  224.0.0.22            01-00-5e-00-00-16     statique
  224.0.0.251           01-00-5e-00-00-fb     statique
  224.0.0.252           01-00-5e-00-00-fc     statique
  239.255.255.250       01-00-5e-7f-ff-fa     statique
  ```
 
  ☀️ Déterminez l'adresse MAC de la passerelle du réseau de l'école
 
  ```powershell
  PS C:\Users\hugoa> ipconfig
  PS C:\Users\hugoa> arp -a
  ```
  ```powershell
  10.33.79.254          7c-5a-1c-d3-d8-76     dynamique
  ```
  ☀️ Supprimez la ligne qui concerne la passerelle
 
  ```powershell
  PS C:\Windows\system32> arp -d 10.33.79.254
  ```
  ☀️ Prouvez que vous avez supprimé la ligne dans la table ARP
  ```powershell
Interface : 10.33.77.164 --- 0xa
  Adresse Internet      Adresse physique      Type
  10.33.65.63           44-af-28-c3-6a-9f     dynamique
  10.33.73.77           98-8d-46-c4-fa-e5     dynamique
  10.33.77.160          c8-94-02-f8-ab-97     dynamique
  10.33.79.255          ff-ff-ff-ff-ff-ff     statique
  224.0.0.22            01-00-5e-00-00-16     statique
  224.0.0.251           01-00-5e-00-00-fb     statique
  224.0.0.252           01-00-5e-00-00-fc     statique
  239.255.255.250       01-00-5e-7f-ff-fa     statique
  255.255.255.255       ff-ff-ff-ff-ff-ff     statique

Interface : 192.168.56.1 --- 0x13
  Adresse Internet      Adresse physique      Type
  192.168.56.255        ff-ff-ff-ff-ff-ff     statique
  224.0.0.22            01-00-5e-00-00-16     statique
  224.0.0.251           01-00-5e-00-00-fb     statique
  224.0.0.252           01-00-5e-00-00-fc     statique
  239.255.255.250       01-00-5e-7f-ff-fa     statique
  ```
  ☀️ Wireshark
  ```powershell
  PS C:\Windows\system32> arp -d 10.33.79.254
  ```
### II. ARP dans un réseau local
# 1. Basics
☀️ Déterminer
```powershell
PS C:\Windows\system32> ipconfig /all
```

```powershell
Carte réseau sans fil Wi-Fi :

   Suffixe DNS propre à la connexion. . . :
   Description. . . . . . . . . . . . . . : Intel(R) Wi-Fi 6E AX211 160MHz
   Adresse physique . . . . . . . . . . . : D4-E9-8A-61-17-A0
   ```
   ```powershell
      Passerelle par défaut. . . . . . . . . : 192.168.80.115
```
```powershell
PS C:\Windows\system32> arp -a
```
```powershell
 192.168.80.115        56-3d-07-f5-7b-07     dynamique
 ```
 ☀️ DIY
 ```powershell
 Carte réseau sans fil Wi-Fi :

   Suffixe DNS propre à la connexion. . . :
   Adresse IPv6 de liaison locale. . . . .: fe80::2926:efc4:87ac:1d25%10
   Adresse IPv4. . . . . . . . . . . . . .: 192.168.80.113
   Masque de sous-réseau. . . . . . . . . : 255.255.255.0
   Passerelle par défaut. . . . . . . . . : 192.168.80.115
   ```
   ☀️ Pingz !
   ```powershell
   PS C:\Windows\system32> ping 192.168.80.126
   ```
   ```powershell
   Envoi d’une requête 'Ping'  192.168.80.126 avec 32 octets de données :
Réponse de 192.168.80.126 : octets=32 temps=13 ms TTL=128
Réponse de 192.168.80.126 : octets=32 temps=70 ms TTL=128
Réponse de 192.168.80.126 : octets=32 temps=75 ms TTL=128
Réponse de 192.168.80.126 : octets=32 temps=49 ms TTL=128

Statistiques Ping pour 192.168.80.126:
    Paquets : envoyés = 4, reçus = 4, perdus = 0 (perte 0%),
Durée approximative des boucles en millisecondes :
    Minimum = 13ms, Maximum = 75ms, Moyenne = 51ms
    ```
    ```powershell
    PS C:\Windows\system32> ping youtube.com
    ```
    ```powershell
    Envoi d’une requête 'ping' sur youtube.com [172.217.20.206] avec 32 octets de données :
Réponse de 172.217.20.206 : octets=32 temps=78 ms TTL=113
Délai d’attente de la demande dépassé.
Réponse de 172.217.20.206 : octets=32 temps=68 ms TTL=113
Réponse de 172.217.20.206 : octets=32 temps=68 ms TTL=113

Statistiques Ping pour 172.217.20.206:
    Paquets : envoyés = 4, reçus = 3, perdus = 1 (perte 25%),
Durée approximative des boucles en millisecondes :
    Minimum = 68ms, Maximum = 78ms, Moyenne = 71ms
    ```
2. ARP
☀️ Affichez votre table ARP !
```powershell
PS C:\Windows\system32> arp -a
```
```powershell
Interface : 192.168.80.113 --- 0xa
  Adresse Internet      Adresse physique      Type
  192.168.80.69         98-bd-80-8b-c9-fa     dynamique
  192.168.80.115        56-3d-07-f5-7b-07     dynamique
  192.168.80.126        84-c5-a6-76-62-b8     dynamique
  192.168.80.169        98-bd-80-8b-c9-fa     dynamique
  192.168.80.200        2e-aa-24-77-3e-e2     dynamique
  192.168.80.255        ff-ff-ff-ff-ff-ff     statique
  224.0.0.22            01-00-5e-00-00-16     statique
  224.0.0.251           01-00-5e-00-00-fb     statique
  239.255.255.250       01-00-5e-7f-ff-fa     statique
  255.255.255.255       ff-ff-ff-ff-ff-ff     statique

Interface : 192.168.56.1 --- 0x13
  Adresse Internet      Adresse physique      Type
  192.168.56.255        ff-ff-ff-ff-ff-ff     statique
  224.0.0.22            01-00-5e-00-00-16     statique
  224.0.0.251           01-00-5e-00-00-fb     statique
  224.0.0.252           01-00-5e-00-00-fc     statique
  239.255.255.250       01-00-5e-7f-ff-fa     statique
  ```
