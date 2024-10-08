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
   ```powershell
   ☀️ Affichez votre table ARP
   ```
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
  ```powershell
  ☀️ Déterminez l'adresse MAC de la passerelle du réseau de l'école
  ```