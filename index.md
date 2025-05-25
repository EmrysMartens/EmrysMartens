# Aanvullingen
Deze github dient als aanvulling/uitbreiding op verschillende overlopen onderdelen van de Bachelorproef: "Modulair framework voor toegang- en netwerkbeheer in bedrijfsomgevingen: Een onderzoek naar optimale integratie van cybersecuritytools".

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

De extra stappen van deze server: 

- Pak de file uit met een archiveringsprogramma zoals 7-ZIP of WinRAR.
- Open VirtualBox, en klik 'nieuw' aan, kies Linux en Ubuntu (64-bit), kies 'volgende'.
- Kies RAM en CPU instellingen, voorbeeld 15.6 GB en 12 CPU, kies 'volgende'.
- Kies bestaande vdi gebruiken, en navigeer naar de gedownloade en uitgepakte file, kies 'volgende' en 'maken'.

    
### opzetting wazuh linux host



### opzetting wazuh windows host


## Volledige opzetting Security Onion

Dit zijn de servers in de Wazuh setup.

### Opzetting Security Onion

De extra stappen van deze server: 
  ```bash
  sudo ip link set eth0 up
  sudo ip addr add 10.0.31.100/24 dev eth0
  sudo ip route add default via 10.0.31.1
  ```

### opzetting Security Onion linux host



### opzetting Security Onion windows host
  ```bash
  sudo ip link set eth0 up
  sudo ip addr add 10.0.31.100/24 dev eth0
  sudo ip route add default via 10.0.31.1
  ```



