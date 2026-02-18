
**Integrazione: Sicurezza Infrastrutturale e Continuità Operativa**

**1. Sicurezza Infrastrutturale di Rete: Il protocollo IPsec**

**IPsec (Internet Protocol Security)** non è un singolo protocollo, ma una suite di protocolli standardizzati (IETF) che operano al **Livello 3 (Rete)** del modello OSI. Il suo scopo principale è garantire la sicurezza delle comunicazioni su reti IP (come Internet) attraverso l'autenticazione e la cifratura di ogni pacchetto IP in una sessione di comunicazione.

A differenza di TLS (che opera a livello applicativo/sessione), IPsec è trasparente alle applicazioni: protegge tutto il traffico tra due endpoint di rete, indipendentemente dal protocollo di trasporto (TCP/UDP) o dall'applicazione utilizzata.

**1.1 Architettura e Componenti Fondamentali**

IPsec si basa su due protocolli principali per la gestione del traffico e uno per la gestione delle chiavi:

* **AH (Authentication Header - RFC 2402):**
  + Fornisce **autenticazione** dell'origine e **integrità** dei dati (tramite Hashing).
  + Garantisce che il pacchetto non sia stato modificato e provenga davvero dalla sorgente dichiarata.
  + **NON fornisce cifratura (confidenzialità):** il payload rimane leggibile.
  + Protegge anche parti dell'intestazione IP originale.
* **ESP (Encapsulating Security Payload - RFC 2406):**
  + È il protocollo più completo e utilizzato.
  + Fornisce **confidenzialità** (cifratura del payload), **autenticazione**, **integrità** e protezione anti-replay.
  + Incapsula il payload originale (o l'intero pacchetto) all'interno di una nuova struttura cifrata.

**1.2 Modalità di Funzionamento**

IPsec può operare in due modalità distinte, a seconda di cosa viene protetto:

1. **Transport Mode (Modalità Trasporto):**
   * Protegge solo il **payload** del pacchetto IP (i dati del livello superiore, es. segmento TCP).
   * L'intestazione IP originale **non viene cifrata** né modificata (eccetto per l'aggiunta dell'header IPsec).
   * **Utilizzo:** Comunicazioni End-to-End tra due host specifici (es. amministrazione remota sicura).
2. **Tunnel Mode (Modalità Tunnel):**
   * Protegge l'**intero pacchetto IP originale** (intestazione + payload).
   * Il pacchetto originale viene cifrato e incapsulato dentro un **nuovo pacchetto IP** con nuove intestazioni (spesso gli indirizzi dei gateway VPN).
   * **Utilizzo:** Standard per le **VPN Site-to-Site**, dove il traffico tra due LAN private viaggia su Internet. Nasconde la topologia interna della rete.

**1.3 Gestione delle Chiavi: Il protocollo IKE**

IPsec utilizza **IKE (Internet Key Exchange)** per negoziare automaticamente le chiavi crittografiche e stabilire le **SA (Security Associations)**. Il processo avviene in due fasi:

* **Fase 1 (IKE Phase 1):** I due dispositivi si autenticano (tramite Pre-Shared Key o Certificati) e stabiliscono un canale sicuro iniziale.
* **Fase 2 (IKE Phase 2):** All'interno del tunnel sicuro della Fase 1, vengono negoziati i parametri specifici per il traffico dati IPsec (algoritmi di cifratura/hash) e vengono generate le chiavi di sessione per ESP/AH.

**2. Firewalling e Sicurezza Perimetrale**

Il **Firewall** è un dispositivo (hardware o software) che applica una politica di sicurezza al traffico che attraversa i confini di una rete, agendo come filtro tra zone a diverso livello di fiducia (es. Internet vs LAN).

**2.1 Classificazione Tecnologica dei Firewall**

|  |  |  |  |
| --- | --- | --- | --- |
| **Tipologia** | **Livello OSI** | **Funzionamento Principale** | **Vantaggi/Svantaggi** |
| **Packet Filtering (Stateless)** | L3 / L4 | Esamina ogni pacchetto singolarmente basandosi solo sull'header (IP sorgente/dest, Porte, Protocollo). | **Pro:** Velocissimo, economico. **Contro:** Bassa sicurezza, non riconosce lo stato della connessione (facilmente aggirabile con IP Spoofing). |
| **Stateful Inspection** | L3 / L4 | Mantiene una **Tabella di Stato**. Traccia le connessioni attive (es. sa se un pacchetto in entrata è la risposta a una richiesta uscita dall'interno). | **Pro:** Molto più sicuro, gestisce sessioni dinamiche. Standard minimo attuale. **Contro:** Più oneroso in termini di CPU rispetto allo stateless. |
| **Proxy Firewall (Application)** | L7 | Agisce come intermediario totale. Interrompe la connessione diretta: il client parla col proxy, il proxy parla con la destinazione. | **Pro:** Ispezione profonda del contenuto (payload), massima sicurezza. **Contro:** Introduce latenza, può essere collo di bottiglia. |
| **Next Generation (NGFW)** | L2 - L7 | Integra Stateful Inspection con **DPI (Deep Packet Inspection)**, IPS (Intrusion Prevention), controllo applicativo e identità utente. | **Pro:** Visibilità completa, blocca minacce avanzate nel payload. **Contro:** Costo elevato, complessità di gestione. |

**2.2 DMZ (Demilitarized Zone) e Bastion Host**

* **DMZ:** È una sottorete logica o fisica che espone i servizi esterni (Web Server, Mail Server, DNS) a una rete non fidata (Internet). Isola questi servizi dalla LAN interna. Se un server nella DMZ viene compromesso, l'attaccante non ha accesso diretto alla rete interna aziendale.
* **Bastion Host:** È un computer specializzato, pesantemente fortificato e posizionato nella DMZ (o sul perimetro), progettato per resistere agli attacchi. Esegue solo i servizi essenziali (principio del *least privilege*) ed è il punto di contatto primario con l'esterno.

**3. NAT e PAT (Network Address Translation)**

Il NAT è una tecnica che modifica le intestazioni dei pacchetti IP mentre transitano attraverso un dispositivo di routing. Sebbene nato per conservare indirizzi IPv4, ha implicazioni importanti per l'architettura di rete.

**3.1 Tipologie di Traduzione**

1. **Static NAT (One-to-One):** Mappa un indirizzo IP privato specifico sempre allo stesso indirizzo IP pubblico. Usato per server interni che devono essere raggiungibili dall'esterno (es. Web Server).
2. **Dynamic NAT:** Mappa un indirizzo IP privato al primo indirizzo IP pubblico disponibile da un pool di indirizzi.
3. **PAT (Port Address Translation) o NAT Overload:** È la forma più comune. Mappa molteplici indirizzi IP privati a un **singolo indirizzo IP pubblico**, utilizzando le **porte sorgente** (Livello 4) per distinguere le diverse sessioni.

**3.2 Ruolo nella Sicurezza**

* **Esaurimento IPv4:** Il PAT ha ritardato l'esaurimento degli indirizzi IPv4 permettendo a intere aziende di uscire su Internet con un solo IP pubblico.
* **Sicurezza (Misconception):** Il NAT nasconde la topologia interna e impedisce connessioni dirette dall'esterno verso host interni non mappati. Tuttavia, **NAT non è un firewall**: non ispeziona il contenuto e non ferma malware in download o connessioni iniziate dall'interno (reverse shell).

**4. VLAN e Segmentazione**

La segmentazione è una strategia di sicurezza fondamentale che divide la rete in sottoreti logiche per limitare la diffusione di attacchi e il traffico di broadcast.

**4.1 Concetto di VLAN (Virtual LAN)**

Una VLAN crea un dominio di broadcast logico indipendente dalla cablatura fisica. Dispositivi su switch diversi possono appartenere alla stessa VLAN, e dispositivi sullo stesso switch possono essere isolati in VLAN diverse.

**4.2 Standard IEEE 802.1Q e Tagging**

Per far viaggiare il traffico di più VLAN su un singolo cavo tra switch, si usa il **Tagging**. Lo standard **802.1Q** inserisce un "tag" di 4 byte nell'intestazione del frame Ethernet originale. Questo tag contiene il **VLAN ID** (12 bit), permettendo allo switch ricevente di sapere a quale VLAN appartiene il frame.

**4.3 Porte Access vs Trunk**

* **Access Port:** Appartiene a una sola VLAN. Collega dispositivi finali (PC, stampanti) che non conoscono il concetto di VLAN. Lo switch rimuove il tag prima di inviare il frame al dispositivo.
* **Trunk Port:** Trasporta il traffico di molteplici VLAN. Collega switch tra loro o switch a router. Mantiene i tag 802.1Q intatti.

**4.4 Benefici di Sicurezza**

La segmentazione tramite VLAN limita il movimento laterale degli attaccanti. Se un PC nella VLAN "Ospiti" viene infettato, non può attaccare direttamente i server nella VLAN "Amministrazione", poiché il traffico deve passare per un router/firewall che applica regole di controllo (ACL).

**5. Continuità Operativa Avanzata: Cluster e Storage**

La sicurezza moderna include la **Resilienza**: la capacità del sistema di continuare a funzionare nonostante i guasti.

**5.1 Cluster Computing**

Un **Cluster** è un insieme di server indipendenti (nodi) che lavorano insieme come un unico sistema logico.

* **Cluster HA (High Availability):** Se un nodo fallisce, i servizi (o le VM) vengono riavviati su un altro nodo (*Failover*).
* **Load Balancing Cluster:** Distribuisce il traffico tra più nodi attivi per migliorare le prestazioni.

**5.2 Shared Storage e Replica**

Per permettere a un servizio di spostarsi da un server all'altro (migrazione/failover), i dati non possono risiedere sul disco locale del server.

* **SAN (Storage Area Network) / NAS:** Storage centralizzato accessibile da tutti i nodi del cluster. È il "cuore" dei dati.
* **Storage Replication:** Per evitare che lo storage condiviso sia un *Single Point of Failure*, i dati vengono replicati (in sincrono o asincrono) su un secondo storage o un sito remoto.

**5.3 Differenze Chiave: HA vs FT vs DR**

|  |  |  |  |
| --- | --- | --- | --- |
| Concetto | Obiettivo | Downtime | Scenario Reale |
| High Availability (HA) | Minimizzare le interruzioni. | Minuti (tempo di riavvio VM). | Un server si rompe; le VM ripartono automaticamente su un altro server del cluster. |
| Fault Tolerance (FT) | Continuità assoluta. | **Zero**. | Un componente hardware fallisce; il sistema speculare (lockstep) continua senza perdere nemmeno una connessione attiva. |
| Disaster Recovery (DR) | Sopravvivenza a catastrofi. | Ore/Giorni (RTO). | Un incendio distrugge il Data Center primario; l'azienda attiva il sito secondario e recupera i dati dai backup/replica. |
