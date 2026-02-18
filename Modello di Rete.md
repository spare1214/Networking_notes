
## J. Modelli di rete

**92. Cos’è il modello OSI?**

1. **Definizione formale** Il **Modello ISO-OSI (Open Systems Interconnection)** è un modello concettuale a **sette strati** sviluppato da ISO (International Standards Organisation) per standardizzare le regole di comunicazione, permettendo l'interconnessione di sistemi informatici eterogenei.
2. **Spiegazione semplificata** È un framework teorico creato per suddividere il complesso processo di comunicazione in rete in sette compiti logici (livelli). È nato quando le reti erano proprietarie, e serviva a stabilire regole comuni universali.
3. **Punti chiave da memorizzare**
   4. Modello concettuale a **sette livelli**.
   5. Scopo: stabilire **regole comuni (protocolli)** per l'interconnessione.
   6. **OSI** sta per *Open System Interconnection* (sistema aperto).
7. **Esempio concreto** Il concetto di **Livello di Sessione (Livello 5)** è un esempio di un livello concettuale definito da OSI, dove opera logicamente **TLS**.
8. **Possibile domanda di approfondimento orale** Perché si dice che il modello ISO-OSI è stato dimostrato "troppo complesso"?

**93. Livelli del modello OSI.**

1. **Definizione formale** Il modello OSI è composto da sette livelli, dal più basso (fisico) al più alto (applicativo), ognuno responsabile di specifiche funzionalità.
2. **Spiegazione semplificata** I sette livelli sono: Fisico (1), Data-Link (2), Rete (3), Trasporto (4), Sessione (5), Presentazione (6), e Applicazione (7).
3. **Punti chiave da memorizzare**
   4. **Livello 2 (Data-Link):** Utilizza il **MAC Address** e gestisce i **Frame**.
   5. **Livello 3 (Rete):** Utilizza l'**IP** e gestisce i **Packet** (routing).
   6. **Livello 4 (Trasporto):** Utilizza le **Porte** e gestisce i **Segmenti** (TCP/UDP).
   7. **Livello 7 (Applicazione):** Protocolli per l'utente finale (HTTP, DNS, SMTP).
8. **Esempio concreto** Quando un router instrada un pacchetto, opera al **Livello 3 (Rete)** leggendo l'indirizzo IP, il PDU (Protocol Data Unit) di questo livello è chiamato **Packet**.
9. **Possibile domanda di approfondimento orale** Descrivi il ruolo del **Livello di Presentazione (Livello 6)**.

**94. Cos’è il modello TCP/IP?**

1. **Definizione formale** Il modello **TCP/IP** è il modello architetturale a **quattro strati** effettivamente implementato, chiamato così dai due protocolli più importanti che contiene: **TCP** (Livello 4 - Trasporto) e **IP** (Livello 3 - Rete/Internet).
2. **Spiegazione semplificata** È la versione semplificata e pratica del modello OSI. Accorpa i livelli Sessione, Presentazione e Applicazione di OSI in un unico livello di **Applicazione**.
3. **Punti chiave da memorizzare**
   4. Modello a **quattro strati** (Host-to-Network, Internet/Network, Transport, Application).
   5. È il **modello reale** implementato su Internet.
   6. **TCP** e **IP** sono i protocolli chiave.
7. **Esempio concreto** Il protocollo **HTTP** (Livello Applicativo in TCP/IP) si appoggia direttamente sul **TCP** (Livello Trasporto in TCP/IP) per la trasmissione dei dati.
8. **Possibile domanda di approfondimento orale** Qual è il nome dato al PDU (Protocol Data Unit) del livello più basso (Host-to-Network)?

**95. Differenze OSI vs TCP/IP.**

1. **Confronto diretto**

|  |  |  |
| --- | --- | --- |
| Caratteristica | Modello OSI | Modello TCP/IP |
| Numero livelli | **Sette** (sette separazioni logiche). | **Quattro** (semplificazione pratica). |
| Focus | **Concettuale/Teorico** (standardizzazione). | **Implementato/Pratico** (funzionalità). |
| Livelli superiori | Sessione (5), Presentazione (6), Applicazione (7) separati. | Accorpati in un unico livello **Applicativo**. |

1. **Spiegazione semplificata** OSI è stato creato per stabilire regole universali, ma era troppo dettagliato. TCP/IP ha preso la parte funzionale (Livello 3 Rete e Livello 4 Trasporto) e l'ha implementata, semplificando la parte applicativa (Livelli 5, 6, 7 in uno solo).
2. **Punti chiave da memorizzare**
   3. TCP/IP è la **versione semplificata** che ha avuto successo nell'implementazione.
   4. La separazione tra i livelli 5, 6, 7 di OSI è la principale differenza strutturale.
5. **Esempio concreto** La **Crittografia** (come TLS) è concettualmente vista nel Livello di Sessione (OSI), ma nel modello TCP/IP viene implementata nel Livello di **Applicazione**.
6. **Possibile domanda di approfondimento orale** A quale livello si verifica l'operazione di **incapsulamento** e come cambia l'header del PDU ad ogni livello?
