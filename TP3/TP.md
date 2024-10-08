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