# Aanvullingen
Deze github dient als aanvulling/uitbreiding op verschillende overlopen onderdelen van de Bachelorproef: "Modulair framework voor toegang- en netwerkbeheer in bedrijfsomgevingen: Een onderzoek naar optimale integratie van cybersecuritytools". Deze github bevat extra configuraties, uitleg, codefragmenten en afbeeldingen.

# Inhoudstafel
- [Opzetting](#opzetting)
  - [Volledige opzetting Wazuh](#volledige-opzetting-wazuh)
    - [Opzetting Wazuh server](#opzetting-wazuh-server)
    - [Opzetting Wazuh Linux host](#opzetting-wazuh-linux-host)
    - [Opzetting Wazuh Windows host](#opzetting-wazuh-windows-host)
  - [Opzetting Security Onion](#opzetting-security-onion)
    - [Opzetting Security Onion server](#opzetting-security-onion-server)
    - [Opzetting Security Onion Linux host](#opzetting-security-onion-linux-host)
    - [Opzetting Security Onion Windows host](#opzetting-security-onion-windows-host)
  - [Opzetting Kali VM](#opzetting-kali-vm)
  - [Aanvallen](#aanvallen)

---

# Opzetting

Opzettingen van de servers voor elk onderdeel.

*Onderstaande sectie bevat extra uitleg en aanvullende commando’s die in de bachelorproef worden gebruikt.*


## Volledige opzetting Wazuh

Dit zijn de servers in de Wazuh setup.

### Opzetting Wazuh server

De extra basis stappen van deze server: 

- Pak de file uit met een archiveringsprogramma zoals 7-ZIP of WinRAR.
- Open VirtualBox, en klik 'nieuw' aan, kies Linux en Ubuntu (64-bit), kies 'volgende'.
- Kies RAM en CPU instellingen, voorbeeld 15.6 GB en 12 CPU, kies 'volgende'.
- Kies bestaande vdi gebruiken, en navigeer naar de gedownloade en uitgepakte file, kies 'volgende' en 'maken'.
- Ga in 'instellingen' naar 'netwerk' en zet de adapter op Bridged Adapter en start de vm.
- Log in met gebruiker en wachtwoord ubuntu, zet de interface op en stel het adres en dg in met de commando's:
 ```
 sudo ip link set eth0 up
 sudo ip addr add 192.168.192.2/24 dev eth0
 sudo ip route add default via 192.168.192.1
```


#### Logging ssh connectie
Soms faalt de default opzet van een linux vm logging van een ssh connectie.
Dit kan opgelost worden in: ``` sudo nano /var/ossec/etc/ossec.conf```
Met de toevoeging van:
```
<localfile>
  <log_format>syslog</log_format>
  <location>/var/log/auth.log</location>
</localfile>

<localfile>
  <log_format>syslog</log_format>
  <location>/var/log/syslog</location>
</localfile>

```
    
### Opzetting wazuh linux host

De extra basis stappen van deze server: 

- Pak de file uit met een archiveringsprogramma zoals 7-ZIP of WinRAR.
- Open VirtualBox, en klik 'nieuw' aan, kies Linux en Ubuntu (64-bit), kies 'volgende'.
- Kies RAM en CPU instellingen, voorbeeld 4096 MB en één CPU, kies 'volgende'.
- Kies bestaande vdi gebruiken, en navigeer naar de gedownloade en uitgepakte file, kies 'volgende' en 'maken'.
- Ga in 'instellingen' naar 'netwerk' en zet de adapter op Bridged Adapter en start de vm.
- Log in met gebruiker en wachtwoord ubuntu, zet de interface op en stel het adres en dg in met de commando's:
```
sudo ip link set eth0 up
sudo ip addr add 192.168.192.3/24 dev eth0
sudo ip route add default via 192.168.192.1
```

### Opzetting wazuh windows host

De extra basis stappen van deze server: 

- Open VirtualBox, en klik 'nieuw' aan, kies Microsoft Windows en Windows 10 (64-bit), kies 'volgende'.
- Selecteer onder opties de gekozen iso voor de machine.
- Kies RAM en CPU instellingen, voorbeeld 4096 MB en twee CPU's, kies 'volgende'.
- Kies nieuwe vdi aanmaken, klik op machine 'aanmaken'.
- Selecteer de iso als opstartmedium, en start op.
- Ga in 'instellingen' naar 'netwerk' en zet de adapter op Bridged Adapter en start de vm.
- Open een command prompt en stel het adres en dg in met de commando's:
```netsh interface ip set address name="Ethernet" static 192.168.192.4 255.255.255.0 192.168.192.1```



## Volledige opzetting Security Onion

Dit zijn de servers in de Security Onion setup.

### Opzetting Security Onion

De extra basis stappen van deze server: 

- Download de ISO van de online documentatie SecurityOnionDocs2024.
- Open VirtualBox, en klik 'nieuw' aan, kies Linux} en Ubuntu (64-bit), kies 'volgende'.
- Kies RAM en CPU instellingen, 15.6 GB en 12 CPU, kies 'volgende'.
- Kies in vdi voor nieuwe, en geef genoeg ruimte, zoals 200GB.
- Selecteer de iso als opstartmedium, en start op.
- Soms moet je bij error hierna in instellingen, onder 'opslag' onder 'iso' de juiste iso nogmaals selecteren.
- Ga in 'instellingen' naar 'netwerk' en zet de adapter op Bridged Adapter en start de vm.
- Log in met gebruiker en wachtwoord ubuntu.

### Opzetting Security Onion linux host

De extra basis stappen van deze server: 

- Pak de file uit met een archiveringsprogramma zoals 7-ZIP of WinRAR.
- Open VirtualBox, en klik 'nieuw' aan, kies Linux en Ubuntu (64-bit), kies 'volgende'.
- Kies RAM en CPU instellingen, voorbeeld 4096 MB en één CPU, kies 'volgende'.
- Kies bestaande vdi gebruiken, en navigeer naar de gedownloade en uitgepakte file, kies 'volgende' en 'maken'.
- Ga in 'instellingen' naar 'netwerk' en zet de adapter op Bridged Adapter en start de vm.
- Log in met gebruiker en wachtwoord ubuntu, zet de interface op en stel het adres en dg in met de commando's:
```
sudo ip link set eth0 up
sudo ip addr add 192.168.192.4/24 dev eth0
sudo ip route add default via 192.168.192.3
```

### Opzetting Security Onion windows host

De extra basis stappen van deze server: 

- Open VirtualBox, en klik 'nieuw' aan, kies Microsoft Windows en Windows 10 (64-bit), kies 'volgende'.
- Selecteer onder opties de gekozen iso voor de machine.
- Kies RAM en CPU instellingen, voorbeeld 4096 MB en twee CPU's, kies 'volgende'.
- Kies nieuwe vdi aanmaken, klik op machine 'aanmaken'.
- Selecteer de iso als opstartmedium, en start op.
- Ga in 'instellingen' naar 'netwerk' en zet de adapter op Bridged Adapter en start de vm.
- Open een command prompt en stel het adres en dg in met de commando's:
```netsh interface ip set address name="Ethernet" static 192.168.192.6 255.255.255.0 192.168.192.3```


## Opzetting Kali vm

De extra basis stappen van deze server: 

- Pak de file uit met een archiveringsprogramma zoals 7-ZIP of WinRAR.
- Open VirtualBox, en klik 'nieuw' aan, kies Linux en Debian (64-bit), kies 'volgende'.
- Kies RAM en CPU instellingen, voorbeeld 8192 MB en twee CPU's, kies 'volgende'.
- Kies bestaande vdi gebruiken, en navigeer naar de gedownloade en uitgepakte file, kies 'volgende' en 'maken'.
- Ga in 'instellingen' naar 'netwerk' en zet de adapter op Bridged Adapter en start de vm.
- Log in met gebruiker en wachtwoord kali, zet de interface op en stel het adres en dg in met de commando's:
```
sudo ip link set eth0 up
sudo ip addr add 192.168.192.10/24 dev eth0
sudo ip route add default via 192.168.192.3
```


## Aanvallen




