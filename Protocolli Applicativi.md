### 1. DNS

**54. Cos’è il DNS?**

1. **Definizione formale** **DNS (Domain Name System)** è un sistema distribuito e gerarchico che opera al Livello di Applicazione e fornisce il servizio di **risoluzione dei nomi a dominio** (URL) in indirizzi **IP**.
2. **Spiegazione semplificata** È l'"elenco telefonico" di Internet. Poiché i computer comunicano solo tramite indirizzi IP (numeri), ma per gli umani è facile ricordare nomi come *google.com*, il DNS fa da traduttore, convertendo il nome simbolico (URL) nell'indirizzo numerico IP necessario per il routing.
3. **Punti chiave da memorizzare**
   4. Protocollo di **Livello Applicativo**.
   5. Traduce nomi (URL) in **indirizzi IP**.
   6. Struttura **gerarchica e distribuita** (non centralizzata).
7. **Esempio concreto** Quando digiti www.majorana.gov.it nel browser, il DNS risolve questo nome nell'indirizzo IP, ad esempio, 62.149.142.190, permettendo al browser di connettersi fisicamente al server.
8. **Possibile domanda di approfondimento orale** Quali problemi riscontreremmo se il DNS fosse implementato in modo completamente centralizzato (server unico)?

**56. Porta utilizzata dal DNS.**

1. **Definizione formale** Il DNS utilizza standardisticamente la **Porta 53**. Per la maggior parte delle **query client-server** (risoluzione di nomi), impiega l'affidabilità e la velocità dell'**UDP** (User Datagram Protocol). Tuttavia, per operazioni più complesse come i trasferimenti di zona tra server, può utilizzare il **TCP**.
2. **Spiegazione semplificata** Il servizio DNS sta in ascolto sulla porta 53. Generalmente usa UDP perché le richieste sono piccole e veloci, e la velocità è cruciale. Se una richiesta si perde (UDP non è affidabile), il client semplicemente la ripete.
3. **Punti chiave da memorizzare**
   4. Porta standard: **53**.
   5. Protocollo predefinito per le query: **UDP**.
   6. UDP è scelto per **velocità e leggerezza**.
7. **Esempio concreto** Quando il tuo computer invia una richiesta DNS al server 8.8.8.8, il segmento di trasporto (UDP) avrà la porta di destinazione impostata a **53** per identificare il processo DNS sul server remoto.
8. **Possibile domanda di approfondimento orale** Perché il DNS è vulnerabile ad alcuni tipi di attacchi informatici, dato che utilizza prevalentemente UDP?

**57. Tipi principali di record DNS.**

1. **Definizione formale** I record DNS (o *Resource Record*) sono voci strutturate all'interno del database DNS, ognuna con un ruolo specifico nel definire le risorse di un dominio. I tipi più importanti includono:
   * **A:** Associa un nome di dominio a un indirizzo **IPv4**.
   * **AAAA:** Associa un nome di dominio a un indirizzo **IPv6**.
   * **CNAME:** Definisce un **alias** (nome canonico) che punta a un altro nome a dominio.
   * **MX:** Definisce i **mail exchanger** (server che gestiscono la posta) per il dominio.
   * **NS:** Indica i **nameserver autorevoli** (server DNS competenti) per la zona.
2. **Spiegazione semplificata** Sono come i diversi tipi di schede in un archivio. Il record A è il più comune e dice "questo nome è questo IP". L'MX dice "per inviare la posta a questo dominio, usa questo server". Il CNAME dice "questo nome è solo un soprannome per quest'altro nome principale".
3. **Punti chiave da memorizzare**
   * **A** e **AAAA** mappano nomi a indirizzi IP (v4 e v6).
   * **CNAME** crea un alias.
   * **MX** è fondamentale per l'invio delle email.
   * Ne esistono oltre 80 tipi, ma solo pochi sono usati regolarmente.
4. **Esempio concreto** Se un'azienda utilizza Google Workspace, il suo dominio (es. *azienda.it*) avrà un record **MX** che punta ai server di posta di Google per garantire che la posta arrivi correttamente.
5. **Possibile domanda di approfondimento orale** Perché si usano i record CNAME, invece di definire più record A che puntano allo stesso indirizzo IP?

Basandoci sui materiali forniti, è probabile che tu ti riferisca alla distinzione tra le modalità di **interrogazione (Query)** che avvengono nel sistema DNS, specificamente tra **Ricorsiva** e **Iterativa**, oppure alla direzione della risoluzione (Diretta vs Inversa).

Ecco la distinzione basata sui documenti:

**1. Tipi di Interrogazione (Query DNS)** Questa è la distinzione tecnica fondamentale nel funzionamento del protocollo:

* **Query Ricorsiva ("Reciproca" nel senso di delega completa):**
  + È quella utilizzata tipicamente dagli **utenti finali** (i client/PC) verso il loro server DNS locale.
  + Il client chiede al server: "Dammi l'indirizzo IP di questo sito".
  + Il server DNS si fa carico di tutto il lavoro: se non ha il dato, contatta lui stesso i vari livelli gerarchici (Root, TLD, Authoritative) e restituisce al client solo la risposta finale.
* **Query Iterativa:**
  + È utilizzata principalmente **tra i server DNS**.
  + Il server risponde con la migliore informazione che ha al momento, che spesso è un rinvio a un altro server. Esempio: "Non conosco l'IP finale, ma conosco il server che gestisce i domini *.it*, chiedi a lui".
  + Chi ha fatto la domanda deve quindi ripetere l'operazione con il nuovo server indicato.

**2. Direzione della Risoluzione** Se intendevi la differenza funzionale nei dati:

* **Risoluzione Diretta:** Associa un **Nome di Dominio** (es. www.google.com) a un **Indirizzo IP** (es. 142.250.x.x). Utilizza record di tipo **A** (IPv4) o **AAAA** (IPv6).
* **Risoluzione Inversa (Reciproca):** Anche se meno dettagliata nei testi forniti, è il processo opposto: risalire da un Indirizzo IP al Nome di Dominio associato.

**Strumento di analisi:** Per vedere questi passaggi in azione, si utilizza il comando **dig** con l'opzione +trace, che mostra tutta la catena di risoluzione iterativa.

**59. Cos’è NSLOOKUP?**

1. **Definizione formale** **NSLOOKUP** (Name Server Lookup) è una utility da riga di comando disponibile su vari sistemi operativi, utilizzata per eseguire **interrogazioni dirette** a un server DNS, permettendo di diagnosticare problemi di risoluzione e visualizzare i dettagli dei record DNS associati a un nome di dominio.
2. **Spiegazione semplificata** È uno strumento per "chiedere" al DNS. Ti consente di specificare il nome che vuoi risolvere e, se lo desideri, quale server DNS (diverso dal tuo predefinito) vuoi interrogare, così puoi vedere come avviene la traduzione da nome a IP.
3. **Punti chiave da memorizzare**
   4. Utility da **riga di comando** per interrogare il DNS.
   5. Permette di fare query **interattive**.
   6. Serve a diagnosticare i problemi di **risoluzione dei nomi**.
7. **Esempio concreto** Digitando nslookup e poi il nome di un sito, lo strumento mostrerà l'indirizzo IP restituito e il DNS che ha fornito la risposta.
8. **Possibile domanda di approfondimento orale** Qual è la differenza tra l'uso di nslookup e l'uso di dig per l'analisi del DNS?

**60. Cos’è DIG?**

1. **Definizione formale** **DIG (Domain Information Groper)** è un *tool* da riga di comando, più potente e flessibile di NSLOOKUP, utilizzato per interrogare i server DNS e visualizzare la risoluzione DNS completa. L'opzione +trace permette di visualizzare il processo di risoluzione **iterativa** passo dopo passo, partendo dai server root fino al server autoritativo.
2. **Spiegazione semplificata** È il cugino avanzato di NSLOOKUP. Non solo ti dice l'IP finale, ma, se richiesto con l'opzione +trace, ti mostra l'intero viaggio che il resolver compie: prima chiede al server Root, poi al server TLD (Top Level Domain), e infine arriva al server Autorativo, offrendo una visione completa della gerarchia DNS.
3. **Punti chiave da memorizzare**
   4. Strumento avanzato per l'interrogazione DNS.
   5. L'opzione +trace mostra la risoluzione **iterativa completa**.
   6. Permette di vedere i vari server coinvolti (Root, TLD, Autoritativo).
7. **Esempio concreto** Il comando dig +trace www.google.com mostra l'interrogazione che parte dai *Root Servers* (che risolvono il .com), poi i *TLD Servers* per il .com, fino ad arrivare ai server che conoscono l'IP esatto di www.google.com.
8. **Possibile domanda di approfondimento orale** Spiega la differenza tra una query DNS **ricorsiva** (usata dal client) e una query **iterativa** (usata dai server tra loro).

### 2. HTTP / HTTPS

**61. Cos’è HTTP?**

1. **Definizione formale** **HTTP (HyperText Transfer Protocol)** è un protocollo di **Livello Applicativo** che si basa sul **TCP** e definisce l'insieme di regole per la trasmissione di **ipertesti** (principalmente file HTML) e altri dati multimediali sul World Wide Web.
2. **Spiegazione semplificata** È il protocollo fondamentale per il funzionamento del web, quello che regola come il tuo browser deve chiedere una pagina web (la *richiesta*) e come il server deve rispondere (la *risposta*). Ogni volta che navighi, anche in una pagina sicura (HTTPS), i dati sono comunque formattati secondo le regole HTTP, anche se poi vengono cifrati.
3. **Punti chiave da memorizzare**
   4. Protocollo di **Livello Applicativo**.
   5. Si basa su **TCP** (Porta 80).
   6. È usato per la trasmissione di **ipertesti** (HTML).
   7. È un protocollo **stateless** (senza stato).
8. **Esempio concreto** Quando il browser invia un messaggio per richiedere la home page, invia un messaggio HTTP di tipo **GET** contenente l'URL della risorsa richiesta.
9. **Possibile domanda di approfondimento orale** Perché, nonostante HTTP sia stateless, un sito web sembra "ricordarsi" chi siamo?

**63. Cos’è un protocollo stateless?**

1. **Definizione formale** Un protocollo è definito **stateless** (senza stato) quando né il server né il client mantengono, a livello del protocollo stesso, alcuna **informazione** relativa ai messaggi scambiati in **precedenza**. Ogni richiesta è trattata come se fosse la prima.
2. **Spiegazione semplificata** Significa che il server "dimentica" ogni interazione subito dopo averla completata. Se fai due richieste a distanza di un secondo, il server le gestisce come due richieste completamente separate e non correlate. Non ha memoria delle transazioni precedenti.
3. **Punti chiave da memorizzare**
   4. Né client né server mantengono memoria delle **richieste passate**.
   5. Ogni richiesta è **indipendente**.
   6. HTTP è l'esempio classico di protocollo *stateless*.
7. **Esempio concreto** Se ti autentichi con successo a un sito (richiesta 1) e poi chiedi una seconda pagina (richiesta 2), senza un meccanismo aggiuntivo (come i **Cookie**), il server, essendo *stateless*, non si ricorderebbe che sei già loggato e ti chiederebbe di autenticarti nuovamente.
8. **Possibile domanda di approfondimento orale** Come viene superato il limite di *statelessness* in applicazioni web complesse?

**65. Cos’è una URL?**

1. **Definizione formale** Una **URL (Uniform Resource Locator)** è una stringa standardizzata (definita nella RFC 2396) che fornisce un indirizzo univoco per identificare una specifica **risorsa** (file, pagina, immagine) su Internet e definisce come tale risorsa può essere acceduta.
2. **Spiegazione semplificata** È l'indirizzo completo di un oggetto sul web, quello che digiti nella barra del browser. Contiene tutto il necessario: il protocollo da usare, il nome del server e il percorso esatto della risorsa richiesta.
3. **Punti chiave da memorizzare**
   4. **Identificatore univoco** di una risorsa.
   5. Specifica la **posizione** e il **metodo di accesso**.
   6. Comprende Host, Porta, Path, e può includere Fragment e Query.
7. **Esempio concreto** Nell'URL http://www.unina.it/immatricolazioni.htm#ingegneria:
   8. http:// è il protocollo.
   9. www.unina.it è l'Host (il server).
   10. /immatricolazioni.htm è il Path (la risorsa).
   11. #ingegneria è il Fragment (un punto preciso all'interno della risorsa).
12. **Possibile domanda di approfondimento orale** A cosa serve la parte ?query di una URL?

### 3. FTP

**68. Cos’è FTP?**

1. **Definizione formale** **FTP (File Transfer Protocol)** è un protocollo di **Livello Applicativo**, basato su **TCP**, specificamente progettato per il **trasferimento di file** tra un client e un server connessi in rete.
2. **Spiegazione semplificata** È il protocollo che permette di copiare file da un computer all'altro in rete. La sua peculiarità è che, a differenza della maggior parte dei protocolli, stabilisce **due connessioni parallele** tra client e server per separare i comandi dai dati.
3. **Punti chiave da memorizzare**
   4. Protocollo di **Livello Applicativo** per il trasferimento di file.
   5. Si basa su **TCP** per garantire l'integrità dei dati.
   6. Utilizza **due connessioni separate** (Controllo e Dati).
   7. Nella versione base non è sicuro, in quanto i dati viaggiano **in chiaro**.
8. **Esempio concreto** Quando un webmaster carica (fa un put o *upload*) una pagina web sul server, usa FTP. Il comando put viaggia sul canale di controllo (Porta 21) mentre il contenuto del file viaggia sul canale dati (Porta 20).
9. **Possibile domanda di approfondimento orale** Perché l'FTP originale è insicuro e come è stato risolto questo problema?

**69. Perché FTP usa due connessioni?**

1. **Definizione formale** FTP usa due connessioni TCP parallele per separare logicamente e fisicamente la comunicazione. Il **Canale di Controllo** (Porta 21) è persistente e gestisce i comandi tra client e server, mentre il **Canale Dati** (Porta 20 o porta alta) è temporaneo e viene aperto e chiuso solo per il trasferimento effettivo dei file (dati).
2. **Spiegazione semplificata** È come avere due linee telefoniche: una per "chiacchierare" (es. dare comandi come *login* o *get file*), che rimane aperta per tutta la sessione, e una seconda linea che si apre solo per il tempo necessario a spedire il file richiesto. Questo mantiene separati i comandi dal flusso di dati.
3. **Punti chiave da memorizzare**
   4. Separazione tra **comandi** e **dati**.
   5. **Control Channel** (Porta 21) è persistente.
   6. **Data Channel** (Porta 20 o porta alta) è temporaneo, usato solo per il trasferimento.
7. **Esempio concreto** Se l'utente invia il comando dir (lista file) sul Canale di Controllo, la lista dei file (il dato) viene restituita attraverso il Canale Dati.
8. **Possibile domanda di approfondimento orale** Quali sono le due modalità principali di funzionamento del Canale Dati e come si distinguono per l'iniziativa della connessione?

**71. Cos’è FTP attivo?**

1. **Definizione formale** In **Active FTP** (FTP Attivo), dopo che il client ha stabilito la Connessione di Controllo (Porta 21), è il **server FTP** che **inizia la Connessione Dati** verso il client. Il server usa la sua Porta 20 come sorgente e si connette a una porta alta (maggiore di 1024) specificata dal client.
2. **Spiegazione semplificata** Il client dice al server "voglio il file, collegati alla mia porta X per inviarmelo". Il server, quindi, funge da iniziatore della connessione dati. Questo meccanismo spesso fallisce se il client si trova dietro un firewall o un NAT, perché il firewall blocca le connessioni entranti non richieste.
3. **Punti chiave da memorizzare**
   4. Il **server** avvia la connessione Dati.
   5. Il server usa la **Porta 20** come sorgente.
   6. Il client riceve i dati su una porta alta.
   7. Spesso problematico con **firewall/NAT** lato client.
8. **Esempio concreto** Un client invia un comando GET sulla porta 21. Il server risponde aprendo una connessione dalla sua porta 20 verso una porta casuale, ad esempio 50000, sul lato client.
9. **Possibile domanda di approfondimento orale** Qual è il problema specifico che si verifica nell'FTP Attivo quando il client è dietro un NAT (*masquerading*)?

**72. Cos’è FTP passivo?**

1. **Definizione formale** In **Passive FTP** (FTP Passivo), sia la Connessione di Controllo (Porta 21) sia la **Connessione Dati** sono **iniziate dal client**. Il client si connette a una porta alta (maggiore di 1024) sul server, che viene negoziata preventivamente attraverso il canale di controllo.
2. **Spiegazione semplificata** Il client chiede al server di mettersi in ascolto su una porta alta. Il server obbedisce e aspetta. Dopodiché, è il client stesso che apre la connessione verso quella porta alta. Questo funziona meglio con i firewall, perché le connessioni in uscita (dal client) sono generalmente permesse, risolvendo il problema dell'FTP Attivo.
3. **Punti chiave da memorizzare**
   4. Il **client** avvia la connessione Dati.
   5. Il client si connette a una **porta alta sul server**.
   6. È la modalità preferita quando il client è protetto da un **firewall**.
7. **Esempio concreto** Un client invia un comando PASV sulla porta 21. Il server risponde indicando una porta alta (es. 50001). Il client, dalla sua porta alta (es. 60000), si connette alla 50001 del server per ricevere il file.
8. **Possibile domanda di approfondimento orale** Perché la Passive FTP, pur risolvendo i problemi lato client, può creare problemi per i firewall lato server?

### 4. Email

**73. Cos’è SMTP?**

1. **Definizione formale** **SMTP (Simple Mail Transfer Protocol)** è il protocollo di **Livello Applicativo** utilizzato per l'**invio di email** tra **server di posta elettronica** (MTA, Mail Transfer Agent).
2. **Spiegazione semplificata** È il "postino" digitale che trasferisce il messaggio dal tuo server di posta a quello del destinatario. Lavora in background per assicurare che l'email lasci il mittente e arrivi correttamente nella casella postale del ricevente.
3. **Punti chiave da memorizzare**
   4. Protocollo di **Livello Applicativo**.
   5. Utilizzato per l'**invio/trasferimento** di email tra server (MTA).
   6. Si basa su **TCP**.
   7. Porta standard: **25** (non crittografata) o **465** (crittografata).
8. **Esempio concreto** Quando clicchi "Invia" nel tuo client di posta (MUA), il client inoltra il messaggio al suo server di posta in uscita utilizzando il protocollo SMTP.
9. **Possibile domanda di approfondimento orale** Come fa l'MTA (server di posta) a sapere a quale server di destinazione inviare l'email?

**74. Cos’è POP3?**

1. **Definizione formale** **POP3 (Post Office Protocol v3)** è un protocollo di **Livello Applicativo** utilizzato da un **client di posta** (MUA) per **ricevere e scaricare i messaggi** dalla casella di posta sul server (mailserver) al proprio dispositivo locale.
2. **Spiegazione semplificata** È come andare all'ufficio postale (il server) e svuotare la cassetta. Tradizionalmente, il comportamento di default è che l'email venga scaricata e poi **rimossa dal server**.
3. **Punti chiave da memorizzare**
   4. Protocollo di **Livello Applicativo** per la **ricezione**.
   5. Il comportamento classico è **scaricare e liberare il server**.
   6. Porta standard: **110** (non crittografata) o **995** (crittografata).
   7. La conversazione avviene tipicamente in tre fasi: **Autorizzazione, Transazione, Update**.
8. **Esempio concreto** Una volta, quando lo spazio sul server era costoso, POP3 era usato per scaricare tutte le email sul disco locale del PC, liberando spazio sul server.
9. **Possibile domanda di approfondimento orale** Descrivi la fase di **Transaction** nella conversazione POP3.

**75. Cos’è IMAP?**

1. **Definizione formale** **IMAP (Internet Message Access Protocol)** è un protocollo di **Livello Applicativo** per l'**accesso remoto alle email** che permette al client di **sincronizzare e gestire** i messaggi direttamente sul server, senza necessariamente scaricarli localmente.
2. **Spiegazione semplificata** A differenza di POP3, IMAP ti permette di lavorare sulla tua casella postale "sul posto". Il messaggio rimane sul server, consentendoti di vederlo, gestirlo, e organizzarlo (es. in cartelle) da qualsiasi dispositivo.
3. **Punti chiave da memorizzare**
   4. Protocollo di **Livello Applicativo** per l'**accesso remoto**.
   5. Il messaggio rimane sul **server** per la sincronizzazione.
   6. Offre maggiore **flessibilità** e funzionalità (es. cartelle).
   7. Porta standard: **143** (non crittografata) o **993** (crittografata).
8. **Esempio concreto** I moderni servizi di webmail e gli smartphone utilizzano IMAP, perché garantisce che le modifiche fatte su un dispositivo (es. segnare un'email come letta) siano immediatamente visibili su tutti gli altri.
9. **Possibile domanda di approfondimento orale** Perché IMAP è particolarmente vantaggioso per gli utenti che accedono alla posta da postazioni "remoti o mobili"?.

**76. Differenze tra POP3 e IMAP.**

1. **Confronto diretto**

|  |  |  |
| --- | --- | --- |
| Caratteristica | POP3 (Post Office Protocol v3) | IMAP (Internet Message Access Protocol) |
| Obiettivo | Ricezione e **download** dei messaggi. | **Accesso remoto** e gestione dei messaggi. |
| Messaggio sul Server | Tipicamente rimosso dal server dopo il download. | Messaggio **sincronizzato** e mantenuto sul server. |
| Uso delle Risorse | **Libera spazio** sul server (basso uso di storage). | **Alto uso di storage** sul server. |
| Accesso Multiplo | Poco adatto all'accesso da più dispositivi. | Ideale per l'accesso da **più dispositivi** (sincronizzazione). |

1. **Spiegazione semplificata** La differenza fondamentale riguarda dove viene gestita la casella: POP3 tende a trattare il server come un ufficio postale (scarichi la posta e la porti via), mentre IMAP tratta il server come un archivio centrale remoto (lavori sui documenti mantenuti in archivio).
2. **Punti chiave da memorizzare**
   3. **Persistenza:** IMAP mantiene, POP3 rimuove (di default).
   4. **Sincronizzazione:** IMAP permette la gestione centralizzata; POP3 è pensato per un singolo client.
5. **Esempio concreto** Se utilizzi POP3 sul tuo PC di casa, l'email potrebbe non essere più disponibile quando provi a leggerla con il telefono. Con IMAP, l'email è accessibile ovunque finché non la cancelli esplicitamente.
6. **Possibile domanda di approfondimento orale** Qual è la funzione del protocollo **MIME** nell'ambito della posta elettronica e a quale problema storico risponde?.

**77. Porte standard SMTP, POP3, IMAP.**

1. **Definizione formale** Le porte standard (note come *well-known ports* se non crittografate, da 0 a 1023) per i protocolli di posta elettronica sono:
   * **SMTP:** Porta **25** (non crittografata) e **465** (crittografata).
   * **POP3:** Porta **110** (non crittografata) e **995** (crittografata).
   * **IMAP:** Porta **143** (non crittografata) e **993** (crittografata).
2. **Spiegazione semplificata** Questi numeri di porta sono standardizzati per far sì che i client (che non hanno porte fisse) sappiano a quale "sportello" (processo) rivolgersi sul server per inviare (SMTP) o ricevere/accedere (POP3/IMAP) la posta.
3. **Punti chiave da memorizzare**
   * **SMTP:** 25 e 465 (sicuro).
   * **POP3:** 110 e 995 (sicuro).
   * **IMAP:** 143 e 993 (sicuro).
   * L'uso delle porte crittografate (es. 465, 995, 993) implica l'uso di **SSL/TLS**.
4. **Esempio concreto** Se tenti una connessione SMTP sulla porta 25, la comunicazione viaggerà **in chiaro**. Se invece configuri il client per usare la porta 465, la comunicazione sarà cifrata da TLS.
5. **Possibile domanda di approfondimento orale** Perché i client utilizzano porte dinamiche (o private) mentre i server utilizzano porte *well-known* come la 25?.

### 5. Accesso remoto – Telnet/SSH

**78. Cos’è Telnet?**

1. **Definizione formale** **Telnet (TElecommunication NETwork)** è un protocollo di **Livello Applicativo** client-server basato su **TCP** che permette di aprire una **sessione di comunicazione bidirezionale in chiaro (non crittografata)** tra due host, consentendo all'utente di lavorare sulla macchina remota tramite linea di comando.
2. **Spiegazione semplificata** È uno dei protocolli più vecchi per accedere a un computer o a un dispositivo di rete (come un router o uno switch) a distanza, usando solo testo. È come avere la riga di comando del PC remoto sul tuo schermo.
3. **Punti chiave da memorizzare**
   4. Protocollo di **Livello Applicativo**.
   5. Trasmette dati **in chiaro** (non sicuro).
   6. Si basa su **TCP** (porta **23**).
   7. Permette l'accesso **testuale** (riga di comando).
8. **Esempio concreto** Un tecnico di rete può usare il Telnet Client per connettersi a un router (che funge da Telnet Server) per eseguire comandi di configurazione, ad esempio per settare la password di *enable secret*.
9. **Possibile domanda di approfondimento orale** Qual è il concetto di **Network Virtual Terminal (NVT)** in relazione al funzionamento di Telnet?.

**79. Perché Telnet è insicuro?**

1. **Definizione formale** Telnet è insicuro perché prevede la **trasmissione di tutti i dati tra client e server solo in chiaro**, senza alcuna crittografia. Ciò include le credenziali di accesso (username e password), che possono essere facilmente intercettate da un attaccante con strumenti di *packet sniffing*.
2. **Spiegazione semplificata** È come inviare una cartolina: chiunque intercetti il traffico di rete può leggere il contenuto, incluse le password, poiché non è cifrato.
3. **Punti chiave da memorizzare**
   4. Dati trasmessi **in chiaro**.
   5. Le **credenziali** (password) sono esposte.
   6. Manca la **mutua autenticazione** e la protezione della comunicazione.
7. **Esempio concreto** Se un attaccante si trova sulla stessa rete e lancia un attacco **Man-in-the-Middle**, può catturare facilmente i pacchetti Telnet e leggere la password del *root* o *admin* in chiaro.
8. **Possibile domanda di approfondimento orale** A quale livello del modello TCP/IP si trova la minaccia legata al Telnet?

**80. Cos’è SSH?**

1. **Definizione formale** **SSH (Secure Shell)** è un protocollo di **Livello Applicativo** che sostituisce Telnet. SSH stabilisce una **sessione remota cifrata** tramite interfaccia a riga di comando, garantendo sia la **mutua autenticazione** del client e del server, sia la **protezione della comunicazione** durante l’intera sessione di lavoro.
2. **Spiegazione semplificata** È la versione crittografata e sicura di Telnet. Sfrutta la crittografia per creare un **canale criptato** attraverso il quale tutti i comandi e i dati scambiati (incluse le password) sono protetti e non leggibili.
3. **Punti chiave da memorizzare**
   4. Versione **sicura** di Telnet.
   5. Realizza un **canale criptato**.
   6. Garantisce la **mutua autenticazione** e la protezione.
   7. È un protocollo di **Livello Applicativo**.
8. **Esempio concreto** Un amministratore di sistema usa SSH per connettersi a un server Linux per manutenzione. Anche se il traffico passa su Internet, un *sniffer* vedrebbe solo dati crittografati, proteggendo la sessione e le credenziali.
9. **Possibile domanda di approfondimento orale** Quali sono gli algoritmi di crittografia (simmetrica o asimmetrica) che SSH utilizza per stabilire il canale sicuro?

**81. Differenze tra Telnet e SSH.**

1. **Confronto diretto**

|  |  |  |
| --- | --- | --- |
| Caratteristica | Telnet (TElecommunication NETwork) | SSH (Secure Shell) |
| Sicurezza | **In chiaro** (non crittografato). | **Cifrato** (canale criptato). |
| Funzione | Accesso remoto semplice (solo comandi). | Accesso remoto sicuro e port forwarding. |
| Autenticazione | Solo autenticazione del client (esposta). | **Mutua autenticazione** (client e server). |
| Porta standard | **23** (TCP). | **22** (TCP). |
| Stato | Obsoleto, sconsigliato per la sicurezza. | **Standard** per l'accesso remoto sicuro. |

1. **Spiegazione semplificata** La differenza critica è la sicurezza: Telnet è come inviare una mail senza busta, mentre SSH è come inviare una raccomandata sigillata e crittografata. SSH è il sostituto moderno e sicuro di Telnet.
2. **Punti chiave da memorizzare**
   3. **Crittografia:** SSH la usa, Telnet no.
   4. **Porte:** Telnet (23), SSH (22).
   5. **Utilizzo:** SSH è lo standard per la gestione remota in ambienti professionali.
6. **Esempio concreto** Telnet può essere utile in diagnostica solo per verificare rapidamente se una porta è aperta (es. Porta 80). SSH è usato quotidianamente per la gestione remota di server e router, anche su reti non fidate.
7. **Possibile domanda di approfondimento orale** Come si abilita SSH (o Telnet) su uno Switch di Livello 2, dato che gli switch non hanno nativamente un indirizzo IP?.
