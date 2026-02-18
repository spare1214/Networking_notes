
## P. Concetti trasversali

**130. Perché la crittografia moderna è ibrida?**

1. **Definizione formale** La crittografia moderna è **ibrida** perché combina i **vantaggi** della crittografia **simmetrica** (velocità ed efficienza nella cifratura di grandi volumi di dati) con i **vantaggi** della crittografia **asimmetrica** (gestione sicura della chiave e autenticazione).
2. **Spiegazione semplificata** L'asimmetrica (lenta) viene usata solo una volta all'inizio della comunicazione per scambiarsi in modo segreto la **chiave di sessione** (chiave unica). Una volta scambiata la chiave, tutta la comunicazione (i dati veri e propri) avviene tramite crittografia simmetrica (veloce).
3. **Punti chiave da memorizzare**
   4. **Simmetrica** (AES) garantisce la **segretezza dei dati** (velocità).
   5. **Asimmetrica** (RSA/DH) garantisce lo **scambio sicuro della chiave di sessione** (sicurezza).
   6. L'efficienza è la motivazione chiave.
7. **Esempio concreto** Il protocollo **TLS** (usato in HTTPS) è l'esempio standard di crittografia ibrida. La Cipher Suite definisce quali algoritmi simmetrici e asimmetrici vengono usati per le diverse fasi.
8. **Possibile domanda di approfondimento orale** Spiega la differenza, nel contesto ibrido, tra l'uso dell'RSA per lo scambio chiavi e l'uso di algoritmi come **Diffie-Hellman** (DH) o **ECDH**.

**131. Differenza tra crittografia e steganografia.**

1. **Definizione formale**
   * **Crittografia:** Disciplina che mira a rendere il contenuto di un messaggio **incomprensibile** (segreto) a terzi tramite processi di cifratura (trasformazione del testo in chiaro in testo cifrato).
   * **Steganografia:** Tecnica che mira a **nascondere l'esistenza stessa** della comunicazione o del messaggio all'interno di un altro mezzo, come un'immagine o un file audio.
2. **Spiegazione semplificata** La **Crittografia** nasconde il *significato* del messaggio (tutti vedono che mandi un messaggio, ma non sanno cosa c'è scritto). La **Steganografia** nasconde l'*esistenza* del messaggio (nessuno sa che hai mandato un messaggio perché è nascosto in una foto innocua).
3. **Punti chiave da memorizzare**
   * **Crittografia:** Rende il contenuto **segreto**.
   * **Steganografia:** Rende l'esistenza del messaggio **invisibile**.
4. **Esempio concreto** Cifrare una password con AES è **crittografia**. Nascondere un intero file di testo all'interno dei bit meno significativi di un'immagine JPEG è **steganografia**.
5. **Possibile domanda di approfondimento orale** Quale delle due tecniche (crittografia o steganografia) è più efficace in un contesto di reti aziendali, e perché?

**132. Relazione tra sicurezza e prestazioni.**

1. **Definizione formale** Esiste una relazione inversamente proporzionale tra **sicurezza** e **prestazioni**. L'implementazione di robusti meccanismi di sicurezza (come crittografia, firewall e autenticazione) introduce un **overhead** computazionale o di rete che **rallenta** la trasmissione e l'elaborazione dei dati.
2. **Spiegazione semplificata** Più è sicuro, più è lento. I calcoli complessi richiesti per cifrare e decifrare i dati (crittografia) e i controlli aggiuntivi sui pacchetti (firewall, routing dinamico) consumano tempo e risorse del processore.
3. **Punti chiave da memorizzare**
   4. La sicurezza introduce **overhead**.
   5. La crittografia **asimmetrica** è l'operazione più costosa in termini di tempo.
   6. Protocolli affidabili (**TCP**) sono più lenti di protocolli non affidabili (**UDP**).
7. **Esempio concreto** L'uso del protocollo **TLS** (sicurezza) è più lento del semplice **HTTP** (prestazioni) perché aggiunge le fasi di Handshake, calcolo MAC e cifratura/decifratura dei dati.
8. **Possibile domanda di approfondimento orale** Come la crittografia **ibrida** risolve il compromesso tra sicurezza e prestazioni?

**133. Perché la gestione delle chiavi è critica?**

1. **Definizione formale** La gestione delle chiavi è critica perché la **sicurezza di un sistema crittografico risiede nella segretezza della chiave, non nell'algoritmo**. Se una chiave viene compromessa (intercettata o rubata), l'attaccante può accedere a tutti i dati cifrati con quella chiave, annullando l'efficacia del sistema.
2. **Spiegazione semplificata** La chiave è il segreto assoluto. Se l'algoritmo (la serratura) è noto a tutti, la chiave (il codice segreto) deve essere custodita. Se la chiave viene rubata, è come se non avessi mai usato la crittografia, e tutti i messaggi sono esposti.
3. **Punti chiave da memorizzare**
   4. La sicurezza risiede nella **segretezza della chiave**.
   5. La crittografia **simmetrica** ha il problema primario dello scambio sicuro della chiave.
   6. La compromissione della chiave privata di un server può permettere la decrittazione dello **storico delle comunicazioni**.
   7. **PKI** e **Certificati Digitali** sono strutture create per gestire in modo sicuro l'associazione tra chiave pubblica e identità.
8. **Esempio concreto** Se la chiave privata di una **Certification Authority** viene rubata, essa può essere usata per firmare falsi certificati, compromettendo l'intera infrastruttura di fiducia (PKI).
9. **Possibile domanda di approfondimento orale** Spiega come il concetto di **chiave effimera** (usata in alcuni algoritmi di Key Exchange) cerca di limitare il danno in caso di compromissione di una chiave privata.

 **Sicurezza per Livelli OSI (Tabella di Sintesi)**

Questa tabella è cruciale per rispondere a domande trasversali ("Come proteggiamo la rete a tutti i livelli?").

|                     |                                                 |                                                                                                           |
| ------------------- | ----------------------------------------------- | --------------------------------------------------------------------------------------------------------- |
| **Livello OSI**     | **Minaccia Principale**                         | **Tecnologia/Contromisura**                                                                               |
| **1. Fisico**       | Accesso fisico, taglio cavi, sniffing hardware. | Controllo accessi locali, cavi in fibra (più difficili da sniffare), ridondanza fisica.                   |
| **2. Data Link**    | MAC Spoofing, ARP Poisoning, VLAN Hopping.      | **Port Security** (mac-address sticky), **VLAN** (segmentazione), **802.1X** (autenticazione port-based). |
| **3. Rete**         | IP Spoofing, Sniffing, Accesso non autorizzato. | **IPsec** (confidenzialità), **Firewall** (Packet Filter), ACL sui router.                                |
| **4. Trasporto**    | Port Scanning, SYN Flood, Session Hijacking.    | **Firewall Stateful**, TLS (confine L4/L5), TCP Wrapper.                                                  |
| **7. Applicazione** | SQL Injection, XSS, Malware, Phishing.          | **WAF** (Web Application Firewall), **NGFW** (DPI), **Proxy**, Antivirus, Input Validation.               |

**Concetti Avanzati per l'Orale (Pillole da 10/10)**

* **Defense in Depth (Difesa in Profondità):** Non affidarsi a un singolo perimetro (es. solo firewall). La sicurezza deve essere a strati: sicurezza fisica + sicurezza perimetrale + sicurezza host + sicurezza applicativa + sicurezza dati. Se un livello fallisce, l'altro protegge (modello "a cipolla").
* **Principio del Privilegio Minimo (Least Privilege):** Ogni utente o processo deve avere *solo* i diritti strettamente necessari per svolgere il proprio compito. Questo limita il danno in caso di compromissione (es. un malware su un account guest fa meno danni che su un account admin).
* **Zero Trust Architecture:** "Non fidarti mai, verifica sempre". Non esiste più una zona "sicura" (LAN). Ogni richiesta, anche se proviene dall'interno, deve essere autenticata, autorizzata e cifrata.
* **Risk Analysis & Business Continuity:** La sicurezza non è assoluta ma basata sul rischio.
  + **RPO (Recovery Point Objective):** Quanto dati posso perdere? (Definisce la frequenza dei backup).
  + **RTO (Recovery Time Objective):** Quanto tempo posso stare fermo? (Definisce le tecnologie di HA/Cluster).

**SUGGERIMENTI PER DOMANDE D'ESAME TRASVERSALI**

Utilizza queste domande per testare la preparazione integrata:

1. *"Candidato, mi parli della differenza tra sicurezza del canale (IPsec/TLS) e sicurezza del perimetro (Firewall). Perché servono entrambe?"*
2. *"Come mitigherebbe un attacco Man-in-the-Middle a livello 2 (ARP) e come lo mitigherebbe a livello 3/4 (IP/TCP)?"*
3. *"Mi progetti un'architettura sicura per un Web Server aziendale, includendo DMZ, Firewall e Reverse Proxy. Quali regole metterebbe sul firewall?"*
4. *"Perché un Packet Filter non è sufficiente a bloccare un attacco SQL Injection? Quale dispositivo dovrei usare?"* (Risposta attesa: Perché opera a L3/L4, mentre l'SQLi è un payload L7; serve un WAF/NGFW).