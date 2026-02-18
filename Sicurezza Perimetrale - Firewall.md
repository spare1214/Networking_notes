**Sicurezza Perimetrale – Classificazione dei Firewall**

**Spiegazione Concettuale** Un Firewall è una barriera deterministica che separa domini di sicurezza con diversi livelli di fiducia (Trust Zones), filtrando il traffico in base a regole (Policy).

**Classificazione Tecnologica**

1. **Packet Filtering (Stateless):** Opera ai livelli **L3/L4**. Esamina ogni pacchetto isolatamente controllando IP e Porte. È veloce ma poco sicuro perché non "ricorda" le connessioni precedenti.
2. **Stateful Inspection:** Opera ai livelli **L3/L4** ma mantiene una *Tabella di Stato*. Capisce se un pacchetto appartiene a una connessione legittima già stabilita (es. la risposta a una richiesta uscita dall'interno). È lo standard minimo di sicurezza.
3. **Proxy / Application Firewall:** Opera a livello **L7**. Agisce come intermediario totale, interrompendo la connessione diretta tra interno ed esterno. Analizza il *payload* (contenuto), offrendo sicurezza alta ma introducendo latenza.
4. **Next Generation Firewall (NGFW):** Integra in un'unica piattaforma le funzioni classiche con **Deep Packet Inspection (DPI)**, IPS (Intrusion Prevention) e consapevolezza dell'applicazione (Application Awareness), superando la logica delle sole porte/IP.

**Zone di Sicurezza e DMZ** Il firewall non divide solo "dentro" e "fuori", ma gestisce zone:

* **Green Zone:** Rete interna (LAN), alta fiducia.
* **Red Zone:** Internet, nessuna fiducia.
* **Orange Zone (DMZ - Demilitarized Zone):** Una zona isolata per i servizi pubblici (es. Web Server). Se un attaccante compromette il server web nella DMZ, non ha comunque accesso diretto alla Green Zone (LAN aziendale).

👉 **Collegamento alla Sicurezza:** Una difesa efficace richiede un approccio *Defense in Depth*, combinando Firewall di Rete (NGFW) sul perimetro e Firewall Host-based sui singoli dispositivi.

**Sicurezza delle Reti Wireless**

**Spiegazione Concettuale** Le reti wireless estendono il perimetro di sicurezza oltre i confini fisici, rendendo l'accesso e l'intercettazione possibili senza collegamento via cavo.

**Protocolli di Sicurezza**

* **WEP:** Obsoleto e insicuro.
* **WPA2:** Standard attuale robusto che utilizza crittografia avanzata (AES). Introduce il concetto di **4-Way Handshake**.
* **4-Way Handshake:** È il protocollo che permette all'Access Point e al Client di negoziare una chiave di cifratura temporanea per la sessione, confermando la reciproca conoscenza della password (PSK) senza mai trasmetterla in chiaro.

**Autenticazione Enterprise (802.1X e RADIUS)** Nelle reti aziendali, una password unica per tutti (PSK) è insicura. Si utilizza l'architettura **802.1X**:

* L'autenticazione è demandata a un server centrale **RADIUS**.
* Ogni utente accede con credenziali personali.
* Il server RADIUS verifica l'identità e autorizza l'accesso alla rete, garantendo un controllo granulare e centralizzato.

👉 **Collegamento alla Sicurezza:** Il wireless richiede autenticazione forte (RADIUS) e cifratura del canale (WPA2/AES) per garantire Confidenzialità e Integrità su un mezzo trasmissivo intrinsecamente insicuro.

---
Firewall Avanzati e Architettura Perimetrale**

Il firewall è una barriera deterministica che separa domini di trust differenti.

**Evoluzione Tecnologica:**

1. **Packet Filtering (Stateless):** Filtra in base a IP e Porte (L3/L4). Veloce ma insicuro (non ricorda lo stato). Vulnerabile a IP Spoofing.
2. **Stateful Inspection:** Mantiene una **Tabella di Stato**. Capisce se un pacchetto appartiene a una sessione legittima già aperta (es. "questo pacchetto ACK è la risposta a un SYN che ho visto uscire?").
3. **Proxy Firewall (Application Gateway):** Interrompe la connessione (L7). Il client parla col firewall, il firewall parla col server. Ispezione profonda ma lento.
4. **Next Generation Firewall (NGFW):** Integra **DPI (Deep Packet Inspection)**. Non guarda solo la porta 80, ma analizza il payload per capire se è traffico Facebook, SQL Injection o Malware, indipendentemente dalla porta usata. Include spesso funzionalità IDS/IPS (Intrusion Prevention System).

**Architettura Perimetrale a Zone:**

* **Green Zone (LAN):** Rete interna ad alta fiducia. Accesso verso Internet permesso, accesso da Internet negato.
* **Red Zone (WAN/Internet):** Rete esterna a fiducia zero.
* **Orange Zone (DMZ - Demilitarized Zone):** Zona cuscinetto contenente i **Bastion Host** (Server Web, Mail, DNS pubblici).
  + *Regola d'oro:* Internet può accedere alla DMZ. La DMZ *non può* accedere alla Green Zone (LAN). Se il Web Server viene compromesso, la LAN aziendale resta sicura.

**C. Proxy e Reverse Proxy**

I proxy agiscono come intermediari a livello Applicativo (L7).

|  |  |  |
| --- | --- | --- |
| **Caratteristica** | **Forward Proxy** | **Reverse Proxy** |
| **Posizione** | Davanti ai **Client** (nella LAN). | Davanti ai **Server** (nel Datacenter). |
| **Scopo** | Proteggere/Controllare gli utenti interni. | Proteggere/Ottimizzare i server. |
| **Funzioni** | **Filtering** (blocca siti), **Caching**, Anonimato utenti. | **Load Balancing** (smista carico), **SSL Offloading** (gestisce crittografia), Protezione da attacchi diretti al server. |
| **Esempio** | Un'azienda blocca l'accesso a Facebook ai dipendenti. | Cloudflare protegge un sito web; Nginx bilancia il traffico verso backend server. |

**D. Soluzioni Reali di Sicurezza (Casi Studio)**

**1. Cisco ASA (Adaptive Security Appliance)** Standard di fatto per la sicurezza enterprise hardware.

* **Funzioni:** Firewall Stateful, VPN Concentrator (gestisce migliaia di tunnel IPsec/SSL), IPS integrato.
* **Ruolo:** Gateway di sicurezza perimetrale per grandi aziende.

**2. IPFire** Distribuzione Linux open-source dedicata alla sicurezza (firewall software).

* **Uso Didattico/PMI:** Permette di configurare visualmente (via web) zone (Green, Red, Orange), regole di firewall, Proxy (Squid), e VPN.
* **Vantaggio:** Trasforma un PC generico con due schede di rete in un firewall potente e configurabile.