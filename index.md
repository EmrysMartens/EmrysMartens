# Inhoudstafel

- [Opzetting](#opzetting)
  - [Volledige opzetting Wazuh](#volledige-opzetting-wazuh)
    - [Opzetting Wazuh server](#opzetting-wazuh-server)
  - [Opzetting Security Onion](#opzetting-security-onion)
  - [Opzetting Kali VM](#opzetting-kali-vm)
  - [Aanvallen](#aanvallen)

---

# Opzetting

Nu volgen de eigenlijke opzetting, aanvallen en vergelijkingen in de testomgeving zoals beschreven in het fysieke onderzoek.

## Volledige opzetting Wazuh

Deze opzetting vindt plaats op het VLAN van Alsic met drie initiële VM's:
1. **Wazuh server** – 16 GB RAM, 12 CPU cores, 100 GB opslag.
2. **Ubuntu Linux host** – 2 GB RAM, 1 CPU core, 20 GB opslag.
3. **Windows 10 host** – 4 GB RAM, 2 CPU cores, 20 GB opslag.

Daarnaast raken er twee extra componenten betrokken:
4. **Kali aanval VM**
5. **Windows hostcomputer** (voor RDP naar de Windows VM's)

*Onderstaande sectie bevat extra uitleg en aanvullende commando’s die in de bachelorproef worden gebruikt.*

### Opzetting Wazuh server

Volg de volgende stappen voor de opzet van de Wazuh server:

- **1. Uitpakken van de VDI-file**  
  Pak het gedownloade VDI-bestand uit met een archiveringsprogramma zoals 7-ZIP of WinRAR.

- **2. Nieuwe VM aanmaken in VirtualBox**  
  1. Open VirtualBox en klik op **"New"**.  
  2. Kies voor **Linux** en **Ubuntu (64-bit)** en klik op **"Next"**.  
  3. Stel de geheugen- en CPU-instellingen in, bijvoorbeeld 15.6 GB RAM en 12 CPU's, en klik op **"Next"**.  
  4. Selecteer *"Use an existing virtual hard disk file"*, navigeer naar de uitgepakte VDI en klik op **"Create"**.

- **3. Netwerkinstelling**
  - Ga in de VM-instellingen naar het tabblad **Network** en zet de adapter op **Bridged Adapter**.  
  - Start vervolgens de VM.

- **4. Interface Configuratie**  
  Log in op de Wazuh server (gebruiker/wachtwoord: `ubuntu`) en voer de volgende commando’s uit om de netwerkinterface in te stellen:

  ```bash
  sudo ip link set eth0 up
  sudo ip addr add 10.0.31.100/24 dev eth0
  sudo ip route add default via 10.0.31.1
