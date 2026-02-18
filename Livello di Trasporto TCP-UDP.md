### 1. TCP

**82. Cos’è TCP?**

1. **Definizione formale** **TCP (Transmission Control Protocol)** è un protocollo di **Livello di Trasporto** che stabilisce una comunicazione logica **affidabile**, **orientata alla connessione**, e di tipo **full-duplex** tra due processi (applicazioni) su host diversi.
2. **Spiegazione semplificata** È il protocollo che garantisce che tutti i dati inviati arrivino a destinazione **corretti, integri e nello stesso identico ordine** in cui sono partiti. Prima di iniziare a trasferire dati, stabilisce una connessione (il *handshake*) e, in caso di errori, chiede la ritrasmissione.
3. **Punti chiave da memorizzare**
   4. È **Affidabile** (garantisce integrità e ordine).
   5. È **Orientato alla Connessione** (usa il 3-Way Handshake).
   6. Utilizza il **Sequence Number** (per l'ordine) e il **Checksum** (per l'integrità).
   7. Implementato tra **host** (processi).
8. **Esempio concreto** **HTTP/HTTPS** si appoggiano su TCP, perché se anche un solo segmento di una pagina HTML fosse perso o fuori ordine, la pagina risulterebbe illeggibile o corrotta.
9. **Possibile domanda di approfondimento orale** Come viene gestito il **controllo di flusso** in TCP e qual è il ruolo del campo **Window** nell'header?.

**84. Cos’è il Three-Way Handshake?**

1. **Definizione formale** Il **TCP 3-Way Handshake** è la sequenza di tre segmenti scambiati tra un client e un server che precede la trasmissione dei dati applicativi. Serve a **stabilire e sincronizzare** la connessione orientata tra i due host, concordando i numeri di sequenza iniziali (ISN - Initial Sequence Number).
2. **Spiegazione semplificata** È il rito in tre passaggi per aprire una linea di comunicazione.
   3. Il Client chiede di sincronizzarsi (SYN=1).
   4. Il Server accetta e chiede a sua volta la sincronizzazione (SYN=1, ACK=1).
   5. Il Client conferma di aver ricevuto l'accettazione (ACK=1). Una volta completato, la connessione è aperta e monitorata.
6. **Punti chiave da memorizzare**
   7. Sequenza di tre segmenti (SYN, SYN-ACK, ACK).
   8. Scopo: **stabilire e sincronizzare** la connessione.
   9. Avviene **prima** della trasmissione dei dati applicativi.
   10. Utilizza i flag **SYN** (Synchronize) e **ACK** (Acknowledge).
11. **Esempio concreto** Un attacco **DDOS** (Distributed Denial of Service) può sfruttare il Three-Way Handshake bombardando il server con messaggi SYN senza mai completare l'ultimo ACK, esaurendo le risorse del server e impedendo risposte legittime.
12. **Possibile domanda di approfondimento orale** Spiega la funzione del **Sequence Number** e dell'**Acknowledgement Number** nello scambio dei tre segmenti del Handshake.

**85. Funzione del Sequence Number.**

1. **Definizione formale** Il **Sequence Number** è un campo presente nell'header del segmento TCP la cui funzione è numerare i **byte dei dati applicativi sequenzialmente**. Questo permette all'host ricevente di **riordinare correttamente i segmenti** che possono essere arrivati in ordine sparso (tipico delle reti a commutazione di pacchetto).
2. **Spiegazione semplificata** È il contatore dei dati. Il TCP numera ogni singolo byte del messaggio originale. Il *Sequence Number* di un segmento è semplicemente il numero assegnato al **primo byte di quel segmento**. Quando i pacchetti arrivano disordinati, il sistema operativo usa questi numeri per rimettere insieme il messaggio finale.
3. **Punti chiave da memorizzare**
   4. Si trova nell'header del segmento TCP.
   5. Numera i **byte** dei dati (payload) sequenzialmente.
   6. Garantisce il **corretto ordine** dei dati.
   7. È un meccanismo cruciale per l'**affidabilità** del TCP.
8. **Esempio concreto** Se invii un file da 1000 byte diviso in due segmenti (S1 e S2), S1 avrà un Sequence Number *X* e S2 avrà un Sequence Number *X + 500* (ipotizzando 500 byte per segmento). Se S2 arriva prima di S1, il Sequence Number permette di rimetterli nell'ordine corretto.
9. **Possibile domanda di approfondimento orale** Spiega come il Sequence Number si collega al campo **Acknowledgement Number** per garantire l'affidabilità.

**86. Funzione del Checksum.**

1. **Definizione formale** Il **Checksum** è un campo di 16 bit nell'header del segmento TCP (e anche nell'header del frame Ethernet) la cui funzione è garantire l'**integrità** dei dati. Il mittente calcola un valore hash basato su una funzione matematica e lo inserisce nel campo Checksum. Il ricevente ripete lo stesso calcolo sui dati ricevuti e confronta il risultato con il Checksum ricevuto.
2. **Spiegazione semplificata** È la "prova di non manomissione" del segmento. Prima di inviare, il sistema calcola una specie di "somma di controllo" e la allega. Se, durante il viaggio, anche un solo bit viene alterato, la somma di controllo ricalcolata dal destinatario non corrisponderà più a quella allegata, indicando che il segmento è corrotto.
3. **Punti chiave da memorizzare**
   4. Garantisce l'**integrità** e la correttezza dei dati.
   5. È una **funzione matematica** applicata ai dati.
   6. Se i valori non coincidono, si richiede la **ritrasmissione**.
   7. Presente sia nel Livello di Trasporto (TCP/UDP) che in Data-Link (Frame Check Sequence).
8. **Esempio concreto** Se un rumore sulla linea altera un bit di un segmento TCP, il Checksum non corrisponderà. Il TCP scarterà il segmento corrotto e utilizzerà il meccanismo di Acknowledgement per richiedere al mittente la ritrasmissione del segmento non valido.
9. **Possibile domanda di approfondimento orale** Qual è la differenza tra l'uso del Checksum in TCP e l'uso di una Funzione di Hash crittografica (come SHA) per l'integrità nel TLS Record Protocol?.

### 2, UDP

**88. Cos’è UDP?**

1. **Definizione formale** **UDP (User Datagram Protocol)** è un protocollo di **Livello di Trasporto** che si basa sul concetto di trasmissione di **datagrammi**. È un protocollo **non orientato alla connessione** e **non affidabile**, che privilegia la velocità e la bassa latenza sulla garanzia di consegna e l'ordine dei pacchetti.
2. **Spiegazione semplificata** È un protocollo molto veloce e leggero perché non si preoccupa di stabilire una connessione preventiva, né di verificare se i dati sono arrivati a destinazione, in che ordine o integri. Se il dato viene perso, non chiede la ritrasmissione. È veloce perché non ha il sovraccarico di TCP (niente Handshake, niente Sequence Number, niente richieste di ritrasmissione).
3. **Punti chiave da memorizzare**
   4. **Non affidabile** e **Non orientato alla connessione**.
   5. **Veloce** (ha minore *overhead* rispetto a TCP).
   6. Non utilizza il *Sequence Number* e non richiede la ritrasmissione in caso di errore.
   7. Utilizzato quando la velocità è prioritaria rispetto alla garanzia di consegna (es. streaming).
8. **Esempio concreto** Il **DNS (Domain Name System)** utilizza prevalentemente UDP (Porta 53) per le query client-server, perché le richieste sono piccole e la velocità di risposta è cruciale. Se una query fallisce, il client la ripete, senza il bisogno dell'overhead di TCP.
9. **Possibile domanda di approfondimento orale** Quali problemi di sicurezza possono nascere dal fatto che il DNS utilizza prevalentemente UDP?

**89. Differenze TCP vs UDP.**

1. **Confronto diretto**

|  |  |  |
| --- | --- | --- |
| Caratteristica | TCP (Transmission Control Protocol) | UDP (User Datagram Protocol) |
| Affidabilità | **Affidabile** (garantisce ordine, integrità, ritrasmissione). | **Non Affidabile** (non garantisce ordine o ritrasmissione). |
| Connessione | **Orientato alla connessione** (usa 3-Way Handshake). | **Non orientato alla connessione**. |
| Ordine/Controlli | Riordina i segmenti (Sequence Number) e verifica integrità (Checksum). | Non riordina; non richiede ritrasmissione se il Checksum fallisce. |
| Velocità | **Lento** (maggiore overhead per i controlli). | **Veloce** (minore overhead). |
| Applicazioni | Web (HTTP/HTTPS), Email (SMTP, IMAP, POP3), Trasferimento file (FTP). | Risoluzione nomi (DNS), Streaming video, Gaming online. |

1. **Spiegazione semplificata** TCP è una comunicazione che si preoccupa della **qualità** (affidabilità) e usa meccanismi di controllo (numeri di sequenza, checksum, Handshake) per assicurare che il messaggio finale sia perfetto. UDP sacrifica la perfezione per la **velocità**. UDP è per i flussi dove la perdita di qualche pacchetto è accettabile (es. voce o video), TCP è per i dati che devono arrivare intatti (es. file e pagine web).
2. **Punti chiave da memorizzare**
   3. **TCP** è cruciale per la ricostruzione corretta del messaggio, poiché i pacchetti possono arrivare in ordine sparso.
   4. UDP non ha la logica per **riordinare i segmenti**.
   5. TCP richiede il **3-Way Handshake** prima di ogni trasmissione.
6. **Esempio concreto** **FTP** e **HTTP** usano TCP perché è necessario che il codice HTML o un file da trasferire arrivino perfettamente integri. Lo streaming video (live) usa spesso UDP per minimizzare la latenza.

Guardare un video su YouTube in streaming può usare UDP (perché perdere un po' di dati non ferma il video), ma scaricare un file immagine usa TCP, perché l'immagine deve essere scaricata perfettamente e completamente.

1. **Possibile domanda di approfondimento orale** Come gestisce TCP il problema della **congestione** e del **flusso** per evitare di sovraccaricare il ricevente?

A quale livello si verifica la **segmentazione** dei dati e come viene definita la dimensione massima (MTU) del segmento?.

**90. Applicazioni tipiche TCP.**

1. **Definizione formale** Le applicazioni tipiche che utilizzano **TCP** sono quelle che richiedono **affidabilità** e la garanzia che i dati arrivino completi e nell'ordine corretto.
2. **Spiegazione semplificata** Sono tutti quei servizi dove anche una singola perdita o un errore potrebbero rendere inutilizzabile il dato, come la navigazione web, l'invio di email, o il download di file.
3. **Punti chiave da memorizzare**
   4. **HTTP/HTTPS** (navigazione web).
   5. **FTP** (trasferimento file).
   6. **SMTP, POP3, IMAP** (posta elettronica).
   7. **SSH** (accesso remoto sicuro).
8. **Esempio concreto** **HTTP** si appoggia su TCP (Porta 80) e **HTTPS** su TCP (Porta 443) per garantire che l'ipertesto (HTML) non venga corrotto o perso.
9. **Possibile domanda di approfondimento orale** Descrivi come un router che riceve un segmento TCP ne riconosce la destinazione (ovvero il processo).

**91. Applicazioni tipiche UDP.**

1. **Definizione formale** Le applicazioni tipiche che utilizzano **UDP** sono quelle che privilegiano la **bassa latenza** e la **velocità** di trasmissione, e che possono tollerare la perdita occasionale di datagrammi.
2. **Spiegazione semplificata** Sono i servizi che hanno bisogno di rapidità e dove il costo di rimediare a un errore sarebbe maggiore del beneficio, come i servizi di base di rete o le comunicazioni in tempo reale.
3. **Punti chiave da memorizzare**
   4. **DNS** (risoluzione dei nomi).
   5. **DHCP** (configurazione dinamica IP).
   6. **SNMP** (monitoraggio di rete).
   7. Applicazioni di **streaming** e **gaming** (dove la perdita di un pacchetto è accettabile, ma il ritardo no).
8. **Esempio concreto** Il protocollo **TFTP (Trivial File Transfer Protocol)** è un esempio che si appoggia su UDP, scelto per la sua velocità in operazioni semplici come il boot remoto.
9. **Possibile domanda di approfondimento orale** Perché il protocollo **TFTP** (che trasferisce file) è considerato "Trivial" e utilizza UDP, a differenza del normale FTP che usa TCP?
