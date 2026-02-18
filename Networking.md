Contents

[Sicurezza delle reti 2](#_Toc220925470)

[B. Crittografia simmetrica 3](#_Toc220925471)

[C. Crittografia asimmetrica 4](#_Toc220925472)

[E. Funzioni di Hash 6](#_Toc220925473)

[F. SSL / TLS 8](#_Toc220925474)

[G. Certificati digitali e PKI 12](#_Toc220925475)

[H. Protocolli Applicativi 15](#_Toc220925476)

[1. DNS 15](#_Toc220925477)

[2. HTTP / HTTPS 18](#_Toc220925478)

[3. FTP 20](#_Toc220925479)

[4. Email 22](#_Toc220925480)

[5. Accesso remoto – Telnet/SSH 25](#_Toc220925481)

[I. Livello di Trasporto 28](#_Toc220925482)

[1. TCP 28](#_Toc220925483)

[2, UDP 31](#_Toc220925484)

[J. Modelli di rete 34](#_Toc220925485)

[K. Routing e inoltro 36](#_Toc220925486)

[L. Protocolli di routing 40](#_Toc220925487)

[M. Autonomous Systems e Internet 46](#_Toc220925488)

[N. NAT e ARP 48](#_Toc220925489)

[O. Sicurezza di rete avanzata 53](#_Toc220925490)

[P. Concetti trasversali 56](#_Toc220925491)

[Risposta alle domande della Verifica 58](#_Toc220925492)

[Sicurezza Informatica 65](#_Toc220925493)

[A. Def: Sicurezza Informatica 65](#_Toc220925494)

[B. I Pilastri Infrastrutturali della Sicurezza (HA, FT, DR) 67](#_Toc220925495)

[C. Confronto e Collegamento dei Concetti 69](#_Toc220925496)

[Soluzioni Tecniche 70](#_Toc220925497)

# Sicurezza delle reti

**1. Cosa si intende per sicurezza nelle comunicazioni di rete?**

1. **Definizione formale** La sicurezza nelle comunicazioni di rete si riferisce all'insieme delle tecniche e delle discipline, come la **crittografia**, volte a garantire i tre pilastri fondamentali: la **segretezza** (confidenzialità), l'**autenticazione** e l'**integrità** dei dati scambiati tra i soggetti comunicanti.
2. **Spiegazione semplificata** Si tratta di assicurare che quando le informazioni viaggiano su una rete, non possano essere lette da terzi, che siamo certi dell'identità di chi invia e riceve, e che il messaggio non sia stato modificato durante il tragitto.
3. **Punti chiave da memorizzare**
   1. Obiettivo primario: proteggere lo scambio di informazioni.
   2. Si basa su tre principi fondamentali: **Segretezza, Integrità, Autenticazione**.
   3. La disciplina portante è la **Crittografia**.
4. **Esempio concreto** L'utilizzo di protocolli come **SSL/TLS** (Secure Socket Layer/Transport Layer Security) in una connessione **HTTPS** incarna la sicurezza di rete, fornendo queste tre funzionalità crittografiche ai protocolli applicativi.
5. **Possibile domanda di approfondimento orale** Quali meccanismi architetturali si utilizzano per garantire l'alta disponibilità (*High Availability*) e la tolleranza ai guasti (*Fault Tolerance*) di un sistema informatico?.

**2. Definisci: segretezza, integrità, autenticazione.**

1. **Definizione formale**
   * **Segretezza (Confidenzialità):** Garanzia che un messaggio possa passare senza che il suo contenuto, anche se intercettato, possa essere compreso da chi non è autorizzato a leggerlo.
   * **Integrità:** Garanzia che il messaggio in chiaro non sia stato modificato o alterato (manomesso) durante la sua trasmissione.
   * **Autenticazione:** Garanzia che il mittente del messaggio sia chi afferma di essere e che non si stia spacciando per qualcun altro.
2. **Spiegazione semplificata**
   * **Segretezza:** Nascondere il contenuto (Cifratura).
   * **Integrità:** Verificare che il messaggio sia arrivato intatto (Hash/Digest).
   * **Autenticazione:** Verificare chi ha inviato il messaggio (Firma Digitale).
3. **Punti chiave da memorizzare**
   * La Segretezza è ottenuta tramite **cifratura** (es. chiave pubblica del destinatario).
   * L'Autenticazione è ottenuta tramite **chiave privata** (firma).
   * L'Integrità è ottenuta tramite le **funzioni di Hash**.
4. **Esempio concreto** Quando si usa la **firma digitale**, si applica la funzione di Hash per garantire l'**integrità**, e poi si cifra il digest con la chiave privata del mittente per garantire l'**autenticazione**.
5. **Possibile domanda di approfondimento orale** Perché una funzione di Hash garantisce l'integrità, ma non la segretezza?.

## B. Crittografia simmetrica

**5. Cos’è la crittografia simmetrica?**

1. **Definizione formale** La crittografia simmetrica, definita anche **crittografia a chiave privata**, è un sistema di cifratura che impiega una **chiave unica** e segreta per eseguire sia l'operazione di cifratura del testo in chiaro da parte del mittente, sia la successiva decifratura da parte del ricevente.
2. **Spiegazione semplificata** È un metodo crittografico in cui si usa la stessa chiave per "chiudere" e "aprire" il messaggio. È il metodo più **veloce** per cifrare i dati perché le operazioni matematiche sono meno complesse rispetto all'asimmetrica.
3. **Punti chiave da memorizzare**
   1. Usa una **chiave unica** per cifrare e decifrare.
   2. È **veloce e sicura**.
   3. Il problema critico è la **condivisione sicura** della chiave.
   4. Algoritmi noti: **DES**, **3-DES**, **IDEA**, **AES**.
4. **Esempio concreto** L'algoritmo **AES** (Advanced Encryption Standard) è un cifrario simmetrico largamente utilizzato e preferito oggi, spesso impiegato all'interno di protocolli di sicurezza ibrida come TLS.
5. **Possibile domanda di approfondimento orale** Spiega in dettaglio la struttura di funzionamento di un cifrario a blocchi come il DES.

**7. Vantaggi e svantaggi della crittografia simmetrica.**

1. **Definizione formale**
   * **Vantaggio:** Il beneficio principale risiede nella sua **efficienza e velocità**, dovuta alla semplicità delle operazioni matematiche e al lavoro a blocchi, che la rende adatta alla cifratura di grandi volumi di dati.
   * **Svantaggio:** Il limite maggiore è la necessità di un canale sicuro per lo **scambio iniziale della chiave unica** tra mittente e destinatario.
2. **Spiegazione semplificata** È come avere un furgone veloce (la cifratura è rapida), ma la chiave per il furgone devi passarla di mano in mano in modo segreto. Se la chiave viene intercettata, tutta la merce (i dati) è a rischio.
3. **Punti chiave da memorizzare**
   * **Vantaggio:** Massima **velocità** nella cifratura/decifratura.
   * **Svantaggio:** Il **problema dello scambio della chiave** è la vulnerabilità principale.
   * Questo svantaggio viene mitigato combinandola con la crittografia asimmetrica (crittografia **ibrida**).
4. **Esempio concreto** Nel protocollo **TLS**, l'algoritmo simmetrico (come AES) è usato per cifrare i dati di sessione (vantaggio), ma la chiave di sessione stessa viene scambiata in modo sicuro usando l'RSA (crittografia asimmetrica, per superare lo svantaggio).
5. **Possibile domanda di approfondimento orale** Come è cambiata la gestione dello scambio chiavi nel TLS moderno rispetto ai vecchi metodi RSA, introducendo il concetto di **chiavi effimere**?.

## C. Crittografia asimmetrica

**15. Cos’è la crittografia asimmetrica?**

1. **Definizione formale** La crittografia asimmetrica, nota anche come **crittografia a chiave pubblica**, è un sistema che si basa sull'uso di **due chiavi interscambiabili** e correlate matematicamente: una **chiave pubblica**, nota a tutti, e una **chiave privata**, che deve rimanere segreta al proprietario.
2. **Spiegazione semplificata** Hai una coppia di chiavi: se cifri con la chiave pubblica, decifri con la chiave privata (per la **segretezza**); se cifri con la tua chiave privata, decifri con la tua chiave pubblica (per l'**autenticazione**). Permette a chiunque di inviarti messaggi segreti (usando la tua chiave pubblica) e a te di dimostrare la tua identità (usando la tua chiave privata).
3. **Punti chiave da memorizzare**
   1. Si basa su una **coppia di chiavi** (pubblica e privata).
   2. È usata per garantire **segretezza** e **autenticazione**.
   3. L'algoritmo più noto è l'**RSA**.
   4. È computazionalmente **più lenta** della simmetrica.
4. **Esempio concreto** Il funzionamento dell'algoritmo **RSA** si basa sulla difficoltà matematica di **fattorizzare numeri primi molto grandi**.
5. **Possibile domanda di approfondimento orale** In termini di sicurezza dei dati, quale delle due chiavi (pubblica o privata) deve essere custodita con assoluta segretezza e perché?.

**17. Come si garantisce la segretezza con chiavi asimmetriche?**

1. **Definizione formale** La segretezza si ottiene quando il mittente cifra il testo in chiaro utilizzando la **chiave pubblica del destinatario**. Dato che solo il destinatario possiede la corrispondente **chiave privata**, solo lui sarà in grado di decifrare il messaggio e ripristinare il testo in chiaro.
2. **Spiegazione semplificata** Se vuoi che solo il ricevente legga il messaggio, usi la sua chiave pubblica per nasconderlo. È come usare un lucchetto che tutti possono chiudere, ma solo il destinatario ha la chiave unica per aprirlo.
3. **Punti chiave da memorizzare**
   1. Mittente usa **Chiave Pubblica del Destinatario**.
   2. Destinatario usa **Chiave Privata propria**.
   3. Garantisce la **riservatezza** del contenuto.
4. **Esempio concreto** Durante l'Handshake TLS, il client cifra la **chiave di sessione** (o *pre master key*) utilizzando la **chiave pubblica del server** (ottenuta dal certificato). Questa chiave cifrata viene inviata al server, che la decifra con la sua chiave privata, garantendo la segretezza della chiave di sessione.
5. **Possibile domanda di approfondimento orale** Perché la segretezza non è l'unica proprietà necessaria? Se il messaggio è segreto, non potrebbe comunque essere stato alterato?.

**18. Come si garantisce l’autenticazione con chiavi asimmetriche?**

1. **Definizione formale** L'autenticazione è garantita quando il mittente usa la **propria chiave privata** per **firmare digitalmente** un messaggio (o, più comunemente, il suo *digest*). Qualsiasi utente può quindi verificare l'identità del mittente utilizzando la corrispondente **chiave pubblica** del mittente stesso.
2. **Spiegazione semplificata** Il mittente usa la sua chiave segreta per applicare un timbro unico al messaggio. Tutti possono vedere il timbro e, usando la chiave pubblica del mittente, possono confermare che quel timbro è autentico e che solo il possessore della chiave privata ha potuto crearlo.
3. **Punti chiave da memorizzare**
   1. Mittente usa la **Chiave Privata propria**.
   2. Si ottiene una **firma elettronica/digitale**.
   3. La verifica avviene con la **Chiave Pubblica del Mittente**.
   4. Garantisce la prova di **origine** del messaggio.
4. **Esempio concreto** Una **Certification Authority (CA)** autentica un **certificato digitale** apponendo la sua **Firma Digitale del Certificato** (generata con la sua chiave privata) sul contenuto del certificato (che include la chiave pubblica del server). Il browser verifica la CA usando la chiave pubblica della CA stessa.
5. **Possibile domanda di approfondimento orale** Spiega la relazione tra la **firma digitale** e la **funzione di Hash** nel processo di autenticazione asimmetrica.

## E. Funzioni di Hash

**26. Cos’è una funzione hash?**

1. **Definizione formale** Una funzione hash crittografica è una funzione **unidirezionale** e **irreversibile** che trasforma un input di **lunghezza arbitraria** in un output di **lunghezza fissa**. Questo output viene chiamato **hash** o **digest**.
2. **Spiegazione semplificata** È un meccanismo per creare un'**impronta digitale** unica e compatta di un qualsiasi dato. Non importa quanto sia grande il dato originale, il risultato (il digest) sarà sempre della stessa dimensione. La caratteristica cruciale è che non si può tornare indietro dal digest al dato originale.
3. **Punti chiave da memorizzare**
   1. È **Unidirezionale** e **Irreversibile**.
   2. L'output (Digest) ha **lunghezza fissa**.
   3. Fondamentale per garantire l'**integrità** dei dati.
   4. Esempi: **MD5**, famiglia **SHA**.
4. **Esempio concreto** Durante l'installazione di un software, il file scaricato è spesso accompagnato da un valore **SHA-256**. L'utente può calcolare l'hash del file scaricato e confrontarlo con quello fornito: se i due digest coincidono, il file è integro e non è stato modificato durante il download.
5. **Possibile domanda di approfondimento orale** Qual è il rischio critico legato all'uso di vecchie funzioni come MD5, che ha portato alla loro obsolescenza?.

**27. Caratteristiche principali delle funzioni hash.**

1. **Definizione formale** Le funzioni hash crittografiche sicure devono possedere:
   * **Irreversibilità:** Impossibilità di risalire all'input originale.
   * **Resistenza alle collisioni:** Difficoltà computazionale nel trovare due input diversi che producano lo stesso digest.
   * **Effetto Valanga:** Un piccolo cambiamento nell'input (es. 1 bit) deve provocare un cambiamento drastico nell'hash risultante.
   * **Deterministico:** Lo stesso input genera sempre lo stesso hash.
2. **Spiegazione semplificata** Devono essere totalmente imprevedibili e stabili: se inserisci lo stesso testo dieci volte, ottieni sempre lo stesso risultato, ma se cambi una virgola, il risultato cambia completamente. Inoltre, una volta ottenuto il risultato, non puoi decifrare il testo di partenza.
3. **Punti chiave da memorizzare**
   * **Irreversibilità** (non sono cifratura).
   * Necessaria **Resistenza alle collisioni**.
   * Garantiscono l'**Integrità** del messaggio.
   * Si usano spesso con il **Salt** per proteggere le password.
4. **Esempio concreto** Nel **TLS Record Protocol**, una funzione Hash (come SHA) calcola un **Message Authentication Code (MAC)** sul blocco di dati. Il ricevente ricalcola l'hash e lo confronta con il MAC ricevuto per verificare l'integrità, sfruttando l'effetto valanga per rilevare la minima alterazione.
5. **Possibile domanda di approfondimento orale** Spiega in che modo il **Salt** neutralizza gli attacchi basati sulle **Rainbow Tables**.

## F. SSL / TLS

**38. A cosa serve TLS?**

1. **Definizione formale** **TLS (Transport Layer Security)** è una *suite* di protocolli (evoluzione di SSL) standardizzata che opera tipicamente al di sopra del livello di trasporto (Livello 5 OSI - Sessione). Il suo scopo è offrire funzionalità crittografiche (segretezza, autenticazione, integrità) ai protocolli applicativi sovrastanti, stabilendo un **canale sicuro** di comunicazione tra client e server.
2. **Spiegazione semplificata** TLS è la "tutela" che rende sicure le comunicazioni internet. Permette al tuo browser e a un sito web di mettersi d'accordo su quale algoritmo usare, scambiarsi chiavi in modo segreto e poi cifrare tutti i dati scambiati, in modo che nessuno possa spiarli o modificarli.
3. **Punti chiave da memorizzare**
   1. È una **suite di protocolli**.
   2. Fornisce **Segretezza, Autenticazione e Integrità**.
   3. Composto da **Handshake Protocol** (negoziazione) e **Record Protocol** (trasmissione dati).
   4. Rende sicuri protocolli come **HTTP** (diventando HTTPS).
   5. Si usa la **crittografia ibrida**.
4. **Esempio concreto** Ogni volta che si effettua un acquisto online, l'uso di **HTTPS** garantisce che i dati della carta di credito siano cifrati e che il sito sia autentico, grazie all'impiego del protocollo TLS.
5. **Possibile domanda di approfondimento orale** Descrivi il ruolo di una **Cipher Suite** nel funzionamento del TLS Handshake.

**39. In quale livello OSI opera TLS?**

1. **Definizione formale** Il protocollo **TLS (Transport Layer Security)** è una suite di protocolli che, nel modello a strati TCP/IP, si posiziona al **Livello di Applicazione**. Nel modello OSI, opera tipicamente al **Livello di Sessione (Livello 5)** o immediatamente al di sopra del Livello di Trasporto, fornendo servizi crittografici ai protocolli applicativi sovrastanti.
2. **Spiegazione semplificata** Nonostante il suo nome (*Transport Layer Security*), il TLS lavora nella parte alta dello *stack*. Si trova tra il livello applicativo (dove operano HTTP o FTP) e il livello di trasporto (TCP). Funge da "strato intermedio" che rende sicura la comunicazione tra i due processi sul client e sul server.
3. **Punti chiave da memorizzare**
   1. Opera al **Livello di Sessione (OSI)** o immediatamente sopra il Trasporto.
   2. Nel modello **TCP/IP** è considerato al **Livello Applicativo**.
   3. Fornisce servizi crittografici (Segretezza, Autenticazione, Integrità) ai protocolli superiori.
4. **Esempio concreto** Quando si usa **HTTPS**, il browser (Applicazione) non parla direttamente con il TCP, ma con il **TLS** (Livello Sessione/Applicazione), che si occupa di cifrare i dati prima di passarli al TCP per l'invio.
5. **Possibile domanda di approfondimento orale** Perché TLS è descritto come un protocollo *ibrido*?

**40. Cos’è l’Handshake TLS?**

1. **Definizione formale** L’**Handshake Protocol** è una delle due componenti principali della *suite* TLS, responsabile della **negoziazione** e dell'accordo sui parametri di sicurezza tra il client e il server prima che inizi lo scambio di dati dell'applicazione.
2. **Spiegazione semplificata** È la "stretta di mano" iniziale. Il client e il server si scambiano informazioni, concordano su quale **Cipher Suite** (l'insieme di algoritmi crittografici) utilizzare per la sessione, verificano l'autenticità del server tramite il **Certificato Digitale**, e si scambiano la **chiave di sessione** in modo sicuro.
3. **Punti chiave da memorizzare**
   1. È la fase di **negoziazione** del TLS.
   2. Stabilisce i parametri di sicurezza per la sessione.
   3. Include l'autenticazione del server (tramite certificato).
   4. Il risultato finale è la definizione di una **chiave segreta condivisa** (chiave di sessione) per la cifratura simmetrica.
4. **Esempio concreto** Quando un browser stabilisce una connessione HTTPS, invia un Client Hello contenente un elenco di *Cipher Suite* supportate. Il server risponde con un Server Hello, scegliendo la *Cipher Suite* definitiva e inviando il suo certificato.
5. **Possibile domanda di approfondimento orale** Descrivi il meccanismo con cui la chiave di sessione viene scambiata in modo sicuro durante l'Handshake.

**42. Cos’è il TLS Record Protocol?**

1. **Definizione formale** Il **TLS Record Protocol** è il protocollo della *suite* TLS che gestisce la **trasmissione sicura dei dati applicativi** dopo che l'Handshake ha stabilito i parametri di sicurezza. Prende i dati dall'alto (Applicazione), li suddivide in blocchi (**Record Protocol Units**), calcola il **MAC** (Message Authentication Code), li cifra e li trasmette.
2. **Spiegazione semplificata** È la parte del TLS che lavora durante la sessione vera e propria, gestendo il flusso dei dati. Il suo compito è prendere i dati, assicurarsi che non siano stati alterati (calcolando il MAC/Hash), cifrarli usando l'algoritmo simmetrico concordato (es. AES) e aggiungere l'header TLS per l'invio.
3. **Punti chiave da memorizzare**
   1. Gestisce la **trasmissione dei dati applicativi**.
   2. Segmenta i dati in **Record Protocol Units**.
   3. Aggiunge integrità tramite il calcolo del **MAC** (con funzioni Hash).
   4. Garantisce la segretezza tramite la **cifratura simmetrica** (es. AES).
4. **Esempio concreto** Dopo l'Handshake, una pagina HTML (dato applicativo) viene suddivisa dal Record Protocol. Per ogni blocco, viene calcolato un MAC (per l'integrità), e poi il blocco viene cifrato con la chiave di sessione.
5. **Possibile domanda di approfondimento orale** Spiega la funzione del MAC all'interno del Record Protocol e perché è necessario se si usa già la cifratura.

**43. Cos’è una Cipher Suite?**

1. **Definizione formale** Una **Cipher Suite** (letteralmente "suite di cifratura") è una combinazione predefinita di algoritmi crittografici che specificano l'insieme esatto di metodi da utilizzare in una sessione TLS per garantire le quattro funzioni fondamentali: **scambio di chiavi**, **autenticazione**, **cifratura simmetrica** (segretezza), e **calcolo del MAC** (integrità).
2. **Spiegazione semplificata** È un "pacchetto di istruzioni" che definisce tutte le scelte crittografiche per una data connessione, come un menu fisso. Ad esempio, una *Cipher Suite* può indicare: usa RSA per lo scambio di chiavi, ECDSA per l'autenticazione, AES-256 per cifrare i dati e SHA-384 per il controllo di integrità.
3. **Punti chiave da memorizzare**
   1. Definisce gli algoritmi per **scambio chiavi, autenticazione, cifratura e MAC**.
   2. Viene negoziata durante l'**Handshake TLS**.
   3. È un esempio di implementazione della **crittografia ibrida**.
4. **Esempio concreto** Un esempio di *Cipher Suite* è TLS\_ECDH\_ECDSA\_WITH\_AES\_256\_CBC\_SHA384, dove ogni parte indica un algoritmo specifico per una funzione (es. ECDH per lo scambio, AES\_256\_CBC per la cifratura).
5. **Possibile domanda di approfondimento orale** Quali algoritmi asimmetrici conosci che sono utilizzati per lo *scambio di chiavi* in una Cipher Suite?

**45. Differenza tra HTTPS e HTTP.**

1. **Confronto diretto**

|  |  |  |
| --- | --- | --- |
| **Caratteristica** | **HTTP (HyperText Transfer Protocol)** | **HTTPS (HyperText Transfer Protocol Secure)** |
| **Definizione** | Protocollo di Livello Applicativo per la trasmissione di pagine web e dati. | Versione sicura di HTTP. |
| **Sicurezza** | Dati scambiati in chiaro (**non cifrati**). | Dati scambiati in forma cifrata (criptati). |
| **Protocollo base** | Si appoggia direttamente su **TCP** (Livello 4). | Si appoggia su **TLS/SSL** che a sua volta usa TCP. |
| **Porta standard** | **TCP Porta 80**. | **TCP Porta 443**. |
| **Funzionalità** | Solo trasferimento dati (stateless). | Trasferimento dati + Segretezza, Integrità, Autenticazione. |

1. **Spiegazione semplificata** HTTP è il modo normale e insicuro per navigare, dove tutti i dati (incluse password) viaggiano come testo semplice. HTTPS è esattamente la stessa cosa, ma incapsulata e cifrata dal protocollo **TLS**; in pratica, mette un "lucchetto" alla comunicazione, garantendo che nessuno possa leggere o manomettere i dati.
2. **Punti chiave da memorizzare**
   1. HTTPS = **HTTP + SSL/TLS** (crittografia).
   2. HTTP usa la porta **80**, HTTPS usa la porta **443**.
   3. HTTPS garantisce **segretezza** e **autenticazione** (tramite certificati).
3. **Esempio concreto** Quando digiti l'URL del tuo conto bancario, il prefisso https:// indica che tutti i dati scambiati, come le tue credenziali di accesso, vengono cifrati e protetti da TLS, rendendo sicura la trasmissione.
4. **Possibile domanda di approfondimento orale** Qual è il ruolo del Certificato Digitale X.509 in una connessione HTTPS?

## G. Certificati digitali e PKI

**47. Cos’è un certificato digitale?**

1. **Definizione formale** Un certificato digitale (spesso basato sullo standard **X.509**) è un documento elettronico emesso da una **Certification Authority (CA)**. Il suo scopo è stabilire una **relazione certa e indiscutibile** tra un soggetto (come un server o una persona) e la sua **chiave pubblica**.
2. **Spiegazione semplificata** È come un "passaporto" elettronico per un sito web o un utente. Contiene l'identità del proprietario e la sua chiave pubblica, ed è timbrato (firmato) da un ente fidato (la CA). Questo timbro certifica che la chiave pubblica appartiene davvero al soggetto dichiarato, prevenendo i furti d'identità (*spoofing*).
3. **Punti chiave da memorizzare**
   1. Rilasciato da una **Certification Authority (CA)**.
   2. Associa in modo indiscutibile un soggetto alla sua **chiave pubblica**.
   3. Standard più comune è **X.509**.
   4. Fondamentale per l'**autenticazione** in protocolli come HTTPS.
4. **Esempio concreto** Il certificato di un server web come *www.google.com* contiene la chiave pubblica di Google. La **Firma Digitale del Certificato** (apposta dalla CA) garantisce che quella chiave pubblica sia effettivamente di Google.
5. **Possibile domanda di approfondimento orale** Qual è il campo all'interno del certificato X.509 che definisce per quanto tempo il certificato è considerato valido?

**48. Cos’è un certificato X.509?**

1. **Definizione formale** X.509 è lo **standard internazionale** che definisce il formato e le specifiche che un certificato digitale deve rispettare. Un certificato X.509 contiene campi obbligatori come la **versione** dello standard, il **numero di serie**, l'**algoritmo di firma** usato dalla CA, il **periodo di validità**, il **nome distinto dell'emittente (CA)**, il **nome del soggetto** e le informazioni sulla **chiave pubblica del soggetto**.
2. **Spiegazione semplificata** È semplicemente la "carta d'identità" digitale con un formato standard riconosciuto a livello globale. Garantisce che tutti i programmi (come i browser) sappiano esattamente dove trovare le informazioni chiave, come la chiave pubblica e la firma della CA, perché sono sempre nello stesso formato.
3. **Punti chiave da memorizzare**
   1. È lo **standard** di formato per i certificati digitali.
   2. Contiene informazioni sul **soggetto**, la sua **chiave pubblica** e la **CA**.
   3. Include la **Firma Digitale del Certificato** creata dalla CA.
4. **Esempio concreto** Il campo **Periodo di Validità** del certificato X.509 stabilisce la data di inizio ("Not Before") e la data di fine ("Not After") in cui il certificato è ritenuto attendibile.
5. **Possibile domanda di approfondimento orale** Qual è la differenza tra il Nome Distinto del Soggetto (*Subject DN*) e l'Identificatore Univoco Soggetto (*Subject Unique Identifier*) in un certificato X.509?

**50. Cos’è una CA (Certification Authority)?**

1. **Definizione formale** Una **Certification Authority (CA)** è un ente terzo, fidato e riconosciuto (spesso a livello statale), che ha il compito di **emettere e firmare digitalmente** i certificati X.509, garantendo così l'associazione tra l'identità del soggetto (server/utente) e la sua chiave pubblica. Le CA sono il pilastro della Public Key Infrastructure (PKI).
2. **Spiegazione semplificata** È l'ente che agisce come un "notaio" sul web. Quando vuoi un certificato, la CA verifica la tua identità e poi appone la sua firma digitale sul tuo certificato. Poiché tutti i browser si fidano delle CA più importanti (le cui chiavi pubbliche sono preinstallate), quando vedono la loro firma sul certificato, sanno che il certificato è valido e non falsificato.
3. **Punti chiave da memorizzare**
   1. Ente di **terza parte fidata** e riconosciuta.
   2. Emette e **firma i certificati digitali**.
   3. Custodisce la propria **chiave privata** in modo estremamente sicuro.
   4. È il componente centrale della **PKI**.
4. **Esempio concreto** Quando si visita un sito, il browser controlla la validità del certificato. Per farlo, usa la **chiave pubblica della CA** (che ha firmato il certificato) per decifrare la **Firma Digitale del Certificato** e verificare che non sia stata alterata.
5. **Possibile domanda di approfondimento orale** Cosa succede se la chiave privata di una Certification Authority viene compromessa?

**53. Come il browser verifica un certificato?**

1. **Definizione formale** Il browser (client) verifica un certificato X.509 ricevuto dal server in due modi principali:ò
   1. **Integrità/Autenticità:** Utilizza la **chiave pubblica della Certification Authority (CA)**, che ha emesso il certificato, per decifrare la **Firma Digitale del Certificato** contenuta nel documento. Se la decifratura è coerente, il certificato è autentico.
   2. **Integrità del Contenuto:** Ricalcola la funzione **Hash** sul certificato e confronta il **digest** ottenuto con quello contenuto all'interno della firma appena decifrata. Se i *digest* coincidono, il certificato non è stato alterato.
2. **Spiegazione semplificata** Il browser ha in memoria una lista di chiavi pubbliche di CA fidate. Quando riceve il certificato del server, usa la chiave pubblica della CA per sbloccare la "firma" presente sul certificato. Poi verifica che le informazioni sul certificato non siano state modificate. Se la firma della CA è valida e i dati sono integri, il browser si fida del server.
3. **Punti chiave da memorizzare**
   1. Applica la **chiave pubblica della CA** per la verifica.
   2. Verifica l'**autenticità** della firma della CA.
   3. Confronta il **digest ricalcolato** con quello firmato per l'**integrità**.
   4. Controlla anche il **periodo di validità**.
4. **Esempio concreto** Il client calcola l'hash di tutto il certificato. Poi decifra il *Digest firmato* (Firma Digitale del Certificato) usando la chiave pubblica della CA e confronta i due hash. Se sono uguali, la comunicazione è considerata sicura.
5. **Possibile domanda di approfondimento orale** Qual è il vantaggio, dal punto di vista dell'integrità, di firmare solo l'Hash del certificato e non l'intero certificato?

La **PKI** (*Public Key Infrastructure*) è un'infrastruttura che comprende hardware, software, persone, politiche e procedure necessarie per creare, gestire, distribuire, utilizzare, archiviare e revocare i certificati digitali.

Il suo obiettivo principale è stabilire una **relazione certa e indiscutibile** tra un'identità (un soggetto, come un server web o una persona) e la sua **Chiave Pubblica**.

I componenti fondamentali della PKI sono:

* **Certification Authority (CA):** È l'ente terzo fidato che emette e firma digitalmente i certificati. La sua firma garantisce che la chiave pubblica contenuta nel certificato appartenga davvero al soggetto indicato.
* **Certificato Digitale (standard X.509):** È il documento elettronico che funge da "carta d'identità", associando la chiave pubblica all'identità del proprietario.

In pratica, la PKI è il sistema di fiducia che impedisce a un attaccante di spacciarsi per la tua banca fornendoti una chiave pubblica falsa (attacco *Man-in-the-Middle* o *Spoofing*).

## H. Protocolli Applicativi

### 1. DNS

**54. Cos’è il DNS?**

1. **Definizione formale** **DNS (Domain Name System)** è un sistema distribuito e gerarchico che opera al Livello di Applicazione e fornisce il servizio di **risoluzione dei nomi a dominio** (URL) in indirizzi **IP**.
2. **Spiegazione semplificata** È l'"elenco telefonico" di Internet. Poiché i computer comunicano solo tramite indirizzi IP (numeri), ma per gli umani è facile ricordare nomi come *google.com*, il DNS fa da traduttore, convertendo il nome simbolico (URL) nell'indirizzo numerico IP necessario per il routing.
3. **Punti chiave da memorizzare**
   1. Protocollo di **Livello Applicativo**.
   2. Traduce nomi (URL) in **indirizzi IP**.
   3. Struttura **gerarchica e distribuita** (non centralizzata).
4. **Esempio concreto** Quando digiti www.majorana.gov.it nel browser, il DNS risolve questo nome nell'indirizzo IP, ad esempio, 62.149.142.190, permettendo al browser di connettersi fisicamente al server.
5. **Possibile domanda di approfondimento orale** Quali problemi riscontreremmo se il DNS fosse implementato in modo completamente centralizzato (server unico)?

**56. Porta utilizzata dal DNS.**

1. **Definizione formale** Il DNS utilizza standardisticamente la **Porta 53**. Per la maggior parte delle **query client-server** (risoluzione di nomi), impiega l'affidabilità e la velocità dell'**UDP** (User Datagram Protocol). Tuttavia, per operazioni più complesse come i trasferimenti di zona tra server, può utilizzare il **TCP**.
2. **Spiegazione semplificata** Il servizio DNS sta in ascolto sulla porta 53. Generalmente usa UDP perché le richieste sono piccole e veloci, e la velocità è cruciale. Se una richiesta si perde (UDP non è affidabile), il client semplicemente la ripete.
3. **Punti chiave da memorizzare**
   1. Porta standard: **53**.
   2. Protocollo predefinito per le query: **UDP**.
   3. UDP è scelto per **velocità e leggerezza**.
4. **Esempio concreto** Quando il tuo computer invia una richiesta DNS al server 8.8.8.8, il segmento di trasporto (UDP) avrà la porta di destinazione impostata a **53** per identificare il processo DNS sul server remoto.
5. **Possibile domanda di approfondimento orale** Perché il DNS è vulnerabile ad alcuni tipi di attacchi informatici, dato che utilizza prevalentemente UDP?

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
   1. Utility da **riga di comando** per interrogare il DNS.
   2. Permette di fare query **interattive**.
   3. Serve a diagnosticare i problemi di **risoluzione dei nomi**.
4. **Esempio concreto** Digitando nslookup e poi il nome di un sito, lo strumento mostrerà l'indirizzo IP restituito e il DNS che ha fornito la risposta.
5. **Possibile domanda di approfondimento orale** Qual è la differenza tra l'uso di nslookup e l'uso di dig per l'analisi del DNS?

**60. Cos’è DIG?**

1. **Definizione formale** **DIG (Domain Information Groper)** è un *tool* da riga di comando, più potente e flessibile di NSLOOKUP, utilizzato per interrogare i server DNS e visualizzare la risoluzione DNS completa. L'opzione +trace permette di visualizzare il processo di risoluzione **iterativa** passo dopo passo, partendo dai server root fino al server autoritativo.
2. **Spiegazione semplificata** È il cugino avanzato di NSLOOKUP. Non solo ti dice l'IP finale, ma, se richiesto con l'opzione +trace, ti mostra l'intero viaggio che il resolver compie: prima chiede al server Root, poi al server TLD (Top Level Domain), e infine arriva al server Autorativo, offrendo una visione completa della gerarchia DNS.
3. **Punti chiave da memorizzare**
   1. Strumento avanzato per l'interrogazione DNS.
   2. L'opzione +trace mostra la risoluzione **iterativa completa**.
   3. Permette di vedere i vari server coinvolti (Root, TLD, Autoritativo).
4. **Esempio concreto** Il comando dig +trace www.google.com mostra l'interrogazione che parte dai *Root Servers* (che risolvono il .com), poi i *TLD Servers* per il .com, fino ad arrivare ai server che conoscono l'IP esatto di www.google.com.
5. **Possibile domanda di approfondimento orale** Spiega la differenza tra una query DNS **ricorsiva** (usata dal client) e una query **iterativa** (usata dai server tra loro).

### 2. HTTP / HTTPS

**61. Cos’è HTTP?**

1. **Definizione formale** **HTTP (HyperText Transfer Protocol)** è un protocollo di **Livello Applicativo** che si basa sul **TCP** e definisce l'insieme di regole per la trasmissione di **ipertesti** (principalmente file HTML) e altri dati multimediali sul World Wide Web.
2. **Spiegazione semplificata** È il protocollo fondamentale per il funzionamento del web, quello che regola come il tuo browser deve chiedere una pagina web (la *richiesta*) e come il server deve rispondere (la *risposta*). Ogni volta che navighi, anche in una pagina sicura (HTTPS), i dati sono comunque formattati secondo le regole HTTP, anche se poi vengono cifrati.
3. **Punti chiave da memorizzare**
   1. Protocollo di **Livello Applicativo**.
   2. Si basa su **TCP** (Porta 80).
   3. È usato per la trasmissione di **ipertesti** (HTML).
   4. È un protocollo **stateless** (senza stato).
4. **Esempio concreto** Quando il browser invia un messaggio per richiedere la home page, invia un messaggio HTTP di tipo **GET** contenente l'URL della risorsa richiesta.
5. **Possibile domanda di approfondimento orale** Perché, nonostante HTTP sia stateless, un sito web sembra "ricordarsi" chi siamo?

**63. Cos’è un protocollo stateless?**

1. **Definizione formale** Un protocollo è definito **stateless** (senza stato) quando né il server né il client mantengono, a livello del protocollo stesso, alcuna **informazione** relativa ai messaggi scambiati in **precedenza**. Ogni richiesta è trattata come se fosse la prima.
2. **Spiegazione semplificata** Significa che il server "dimentica" ogni interazione subito dopo averla completata. Se fai due richieste a distanza di un secondo, il server le gestisce come due richieste completamente separate e non correlate. Non ha memoria delle transazioni precedenti.
3. **Punti chiave da memorizzare**
   1. Né client né server mantengono memoria delle **richieste passate**.
   2. Ogni richiesta è **indipendente**.
   3. HTTP è l'esempio classico di protocollo *stateless*.
4. **Esempio concreto** Se ti autentichi con successo a un sito (richiesta 1) e poi chiedi una seconda pagina (richiesta 2), senza un meccanismo aggiuntivo (come i **Cookie**), il server, essendo *stateless*, non si ricorderebbe che sei già loggato e ti chiederebbe di autenticarti nuovamente.
5. **Possibile domanda di approfondimento orale** Come viene superato il limite di *statelessness* in applicazioni web complesse?

**65. Cos’è una URL?**

1. **Definizione formale** Una **URL (Uniform Resource Locator)** è una stringa standardizzata (definita nella RFC 2396) che fornisce un indirizzo univoco per identificare una specifica **risorsa** (file, pagina, immagine) su Internet e definisce come tale risorsa può essere acceduta.
2. **Spiegazione semplificata** È l'indirizzo completo di un oggetto sul web, quello che digiti nella barra del browser. Contiene tutto il necessario: il protocollo da usare, il nome del server e il percorso esatto della risorsa richiesta.
3. **Punti chiave da memorizzare**
   1. **Identificatore univoco** di una risorsa.
   2. Specifica la **posizione** e il **metodo di accesso**.
   3. Comprende Host, Porta, Path, e può includere Fragment e Query.
4. **Esempio concreto** Nell'URL http://www.unina.it/immatricolazioni.htm#ingegneria:
   1. http:// è il protocollo.
   2. www.unina.it è l'Host (il server).
   3. /immatricolazioni.htm è il Path (la risorsa).
   4. #ingegneria è il Fragment (un punto preciso all'interno della risorsa).
5. **Possibile domanda di approfondimento orale** A cosa serve la parte ?query di una URL?

### 3. FTP

**68. Cos’è FTP?**

1. **Definizione formale** **FTP (File Transfer Protocol)** è un protocollo di **Livello Applicativo**, basato su **TCP**, specificamente progettato per il **trasferimento di file** tra un client e un server connessi in rete.
2. **Spiegazione semplificata** È il protocollo che permette di copiare file da un computer all'altro in rete. La sua peculiarità è che, a differenza della maggior parte dei protocolli, stabilisce **due connessioni parallele** tra client e server per separare i comandi dai dati.
3. **Punti chiave da memorizzare**
   1. Protocollo di **Livello Applicativo** per il trasferimento di file.
   2. Si basa su **TCP** per garantire l'integrità dei dati.
   3. Utilizza **due connessioni separate** (Controllo e Dati).
   4. Nella versione base non è sicuro, in quanto i dati viaggiano **in chiaro**.
4. **Esempio concreto** Quando un webmaster carica (fa un put o *upload*) una pagina web sul server, usa FTP. Il comando put viaggia sul canale di controllo (Porta 21) mentre il contenuto del file viaggia sul canale dati (Porta 20).
5. **Possibile domanda di approfondimento orale** Perché l'FTP originale è insicuro e come è stato risolto questo problema?

**69. Perché FTP usa due connessioni?**

1. **Definizione formale** FTP usa due connessioni TCP parallele per separare logicamente e fisicamente la comunicazione. Il **Canale di Controllo** (Porta 21) è persistente e gestisce i comandi tra client e server, mentre il **Canale Dati** (Porta 20 o porta alta) è temporaneo e viene aperto e chiuso solo per il trasferimento effettivo dei file (dati).
2. **Spiegazione semplificata** È come avere due linee telefoniche: una per "chiacchierare" (es. dare comandi come *login* o *get file*), che rimane aperta per tutta la sessione, e una seconda linea che si apre solo per il tempo necessario a spedire il file richiesto. Questo mantiene separati i comandi dal flusso di dati.
3. **Punti chiave da memorizzare**
   1. Separazione tra **comandi** e **dati**.
   2. **Control Channel** (Porta 21) è persistente.
   3. **Data Channel** (Porta 20 o porta alta) è temporaneo, usato solo per il trasferimento.
4. **Esempio concreto** Se l'utente invia il comando dir (lista file) sul Canale di Controllo, la lista dei file (il dato) viene restituita attraverso il Canale Dati.
5. **Possibile domanda di approfondimento orale** Quali sono le due modalità principali di funzionamento del Canale Dati e come si distinguono per l'iniziativa della connessione?

**71. Cos’è FTP attivo?**

1. **Definizione formale** In **Active FTP** (FTP Attivo), dopo che il client ha stabilito la Connessione di Controllo (Porta 21), è il **server FTP** che **inizia la Connessione Dati** verso il client. Il server usa la sua Porta 20 come sorgente e si connette a una porta alta (maggiore di 1024) specificata dal client.
2. **Spiegazione semplificata** Il client dice al server "voglio il file, collegati alla mia porta X per inviarmelo". Il server, quindi, funge da iniziatore della connessione dati. Questo meccanismo spesso fallisce se il client si trova dietro un firewall o un NAT, perché il firewall blocca le connessioni entranti non richieste.
3. **Punti chiave da memorizzare**
   1. Il **server** avvia la connessione Dati.
   2. Il server usa la **Porta 20** come sorgente.
   3. Il client riceve i dati su una porta alta.
   4. Spesso problematico con **firewall/NAT** lato client.
4. **Esempio concreto** Un client invia un comando GET sulla porta 21. Il server risponde aprendo una connessione dalla sua porta 20 verso una porta casuale, ad esempio 50000, sul lato client.
5. **Possibile domanda di approfondimento orale** Qual è il problema specifico che si verifica nell'FTP Attivo quando il client è dietro un NAT (*masquerading*)?

**72. Cos’è FTP passivo?**

1. **Definizione formale** In **Passive FTP** (FTP Passivo), sia la Connessione di Controllo (Porta 21) sia la **Connessione Dati** sono **iniziate dal client**. Il client si connette a una porta alta (maggiore di 1024) sul server, che viene negoziata preventivamente attraverso il canale di controllo.
2. **Spiegazione semplificata** Il client chiede al server di mettersi in ascolto su una porta alta. Il server obbedisce e aspetta. Dopodiché, è il client stesso che apre la connessione verso quella porta alta. Questo funziona meglio con i firewall, perché le connessioni in uscita (dal client) sono generalmente permesse, risolvendo il problema dell'FTP Attivo.
3. **Punti chiave da memorizzare**
   1. Il **client** avvia la connessione Dati.
   2. Il client si connette a una **porta alta sul server**.
   3. È la modalità preferita quando il client è protetto da un **firewall**.
4. **Esempio concreto** Un client invia un comando PASV sulla porta 21. Il server risponde indicando una porta alta (es. 50001). Il client, dalla sua porta alta (es. 60000), si connette alla 50001 del server per ricevere il file.
5. **Possibile domanda di approfondimento orale** Perché la Passive FTP, pur risolvendo i problemi lato client, può creare problemi per i firewall lato server?

### 4. Email

**73. Cos’è SMTP?**

1. **Definizione formale** **SMTP (Simple Mail Transfer Protocol)** è il protocollo di **Livello Applicativo** utilizzato per l'**invio di email** tra **server di posta elettronica** (MTA, Mail Transfer Agent).
2. **Spiegazione semplificata** È il "postino" digitale che trasferisce il messaggio dal tuo server di posta a quello del destinatario. Lavora in background per assicurare che l'email lasci il mittente e arrivi correttamente nella casella postale del ricevente.
3. **Punti chiave da memorizzare**
   1. Protocollo di **Livello Applicativo**.
   2. Utilizzato per l'**invio/trasferimento** di email tra server (MTA).
   3. Si basa su **TCP**.
   4. Porta standard: **25** (non crittografata) o **465** (crittografata).
4. **Esempio concreto** Quando clicchi "Invia" nel tuo client di posta (MUA), il client inoltra il messaggio al suo server di posta in uscita utilizzando il protocollo SMTP.
5. **Possibile domanda di approfondimento orale** Come fa l'MTA (server di posta) a sapere a quale server di destinazione inviare l'email?

**74. Cos’è POP3?**

1. **Definizione formale** **POP3 (Post Office Protocol v3)** è un protocollo di **Livello Applicativo** utilizzato da un **client di posta** (MUA) per **ricevere e scaricare i messaggi** dalla casella di posta sul server (mailserver) al proprio dispositivo locale.
2. **Spiegazione semplificata** È come andare all'ufficio postale (il server) e svuotare la cassetta. Tradizionalmente, il comportamento di default è che l'email venga scaricata e poi **rimossa dal server**.
3. **Punti chiave da memorizzare**
   1. Protocollo di **Livello Applicativo** per la **ricezione**.
   2. Il comportamento classico è **scaricare e liberare il server**.
   3. Porta standard: **110** (non crittografata) o **995** (crittografata).
   4. La conversazione avviene tipicamente in tre fasi: **Autorizzazione, Transazione, Update**.
4. **Esempio concreto** Una volta, quando lo spazio sul server era costoso, POP3 era usato per scaricare tutte le email sul disco locale del PC, liberando spazio sul server.
5. **Possibile domanda di approfondimento orale** Descrivi la fase di **Transaction** nella conversazione POP3.

**75. Cos’è IMAP?**

1. **Definizione formale** **IMAP (Internet Message Access Protocol)** è un protocollo di **Livello Applicativo** per l'**accesso remoto alle email** che permette al client di **sincronizzare e gestire** i messaggi direttamente sul server, senza necessariamente scaricarli localmente.
2. **Spiegazione semplificata** A differenza di POP3, IMAP ti permette di lavorare sulla tua casella postale "sul posto". Il messaggio rimane sul server, consentendoti di vederlo, gestirlo, e organizzarlo (es. in cartelle) da qualsiasi dispositivo.
3. **Punti chiave da memorizzare**
   1. Protocollo di **Livello Applicativo** per l'**accesso remoto**.
   2. Il messaggio rimane sul **server** per la sincronizzazione.
   3. Offre maggiore **flessibilità** e funzionalità (es. cartelle).
   4. Porta standard: **143** (non crittografata) o **993** (crittografata).
4. **Esempio concreto** I moderni servizi di webmail e gli smartphone utilizzano IMAP, perché garantisce che le modifiche fatte su un dispositivo (es. segnare un'email come letta) siano immediatamente visibili su tutti gli altri.
5. **Possibile domanda di approfondimento orale** Perché IMAP è particolarmente vantaggioso per gli utenti che accedono alla posta da postazioni "remoti o mobili"?.

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
   1. **Persistenza:** IMAP mantiene, POP3 rimuove (di default).
   2. **Sincronizzazione:** IMAP permette la gestione centralizzata; POP3 è pensato per un singolo client.
3. **Esempio concreto** Se utilizzi POP3 sul tuo PC di casa, l'email potrebbe non essere più disponibile quando provi a leggerla con il telefono. Con IMAP, l'email è accessibile ovunque finché non la cancelli esplicitamente.
4. **Possibile domanda di approfondimento orale** Qual è la funzione del protocollo **MIME** nell'ambito della posta elettronica e a quale problema storico risponde?.

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
   1. Protocollo di **Livello Applicativo**.
   2. Trasmette dati **in chiaro** (non sicuro).
   3. Si basa su **TCP** (porta **23**).
   4. Permette l'accesso **testuale** (riga di comando).
4. **Esempio concreto** Un tecnico di rete può usare il Telnet Client per connettersi a un router (che funge da Telnet Server) per eseguire comandi di configurazione, ad esempio per settare la password di *enable secret*.
5. **Possibile domanda di approfondimento orale** Qual è il concetto di **Network Virtual Terminal (NVT)** in relazione al funzionamento di Telnet?.

**79. Perché Telnet è insicuro?**

1. **Definizione formale** Telnet è insicuro perché prevede la **trasmissione di tutti i dati tra client e server solo in chiaro**, senza alcuna crittografia. Ciò include le credenziali di accesso (username e password), che possono essere facilmente intercettate da un attaccante con strumenti di *packet sniffing*.
2. **Spiegazione semplificata** È come inviare una cartolina: chiunque intercetti il traffico di rete può leggere il contenuto, incluse le password, poiché non è cifrato.
3. **Punti chiave da memorizzare**
   1. Dati trasmessi **in chiaro**.
   2. Le **credenziali** (password) sono esposte.
   3. Manca la **mutua autenticazione** e la protezione della comunicazione.
4. **Esempio concreto** Se un attaccante si trova sulla stessa rete e lancia un attacco **Man-in-the-Middle**, può catturare facilmente i pacchetti Telnet e leggere la password del *root* o *admin* in chiaro.
5. **Possibile domanda di approfondimento orale** A quale livello del modello TCP/IP si trova la minaccia legata al Telnet?

**80. Cos’è SSH?**

1. **Definizione formale** **SSH (Secure Shell)** è un protocollo di **Livello Applicativo** che sostituisce Telnet. SSH stabilisce una **sessione remota cifrata** tramite interfaccia a riga di comando, garantendo sia la **mutua autenticazione** del client e del server, sia la **protezione della comunicazione** durante l’intera sessione di lavoro.
2. **Spiegazione semplificata** È la versione crittografata e sicura di Telnet. Sfrutta la crittografia per creare un **canale criptato** attraverso il quale tutti i comandi e i dati scambiati (incluse le password) sono protetti e non leggibili.
3. **Punti chiave da memorizzare**
   1. Versione **sicura** di Telnet.
   2. Realizza un **canale criptato**.
   3. Garantisce la **mutua autenticazione** e la protezione.
   4. È un protocollo di **Livello Applicativo**.
4. **Esempio concreto** Un amministratore di sistema usa SSH per connettersi a un server Linux per manutenzione. Anche se il traffico passa su Internet, un *sniffer* vedrebbe solo dati crittografati, proteggendo la sessione e le credenziali.
5. **Possibile domanda di approfondimento orale** Quali sono gli algoritmi di crittografia (simmetrica o asimmetrica) che SSH utilizza per stabilire il canale sicuro?

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
   1. **Crittografia:** SSH la usa, Telnet no.
   2. **Porte:** Telnet (23), SSH (22).
   3. **Utilizzo:** SSH è lo standard per la gestione remota in ambienti professionali.
3. **Esempio concreto** Telnet può essere utile in diagnostica solo per verificare rapidamente se una porta è aperta (es. Porta 80). SSH è usato quotidianamente per la gestione remota di server e router, anche su reti non fidate.
4. **Possibile domanda di approfondimento orale** Come si abilita SSH (o Telnet) su uno Switch di Livello 2, dato che gli switch non hanno nativamente un indirizzo IP?.

## I. Livello di Trasporto

### 1. TCP

**82. Cos’è TCP?**

1. **Definizione formale** **TCP (Transmission Control Protocol)** è un protocollo di **Livello di Trasporto** che stabilisce una comunicazione logica **affidabile**, **orientata alla connessione**, e di tipo **full-duplex** tra due processi (applicazioni) su host diversi.
2. **Spiegazione semplificata** È il protocollo che garantisce che tutti i dati inviati arrivino a destinazione **corretti, integri e nello stesso identico ordine** in cui sono partiti. Prima di iniziare a trasferire dati, stabilisce una connessione (il *handshake*) e, in caso di errori, chiede la ritrasmissione.
3. **Punti chiave da memorizzare**
   1. È **Affidabile** (garantisce integrità e ordine).
   2. È **Orientato alla Connessione** (usa il 3-Way Handshake).
   3. Utilizza il **Sequence Number** (per l'ordine) e il **Checksum** (per l'integrità).
   4. Implementato tra **host** (processi).
4. **Esempio concreto** **HTTP/HTTPS** si appoggiano su TCP, perché se anche un solo segmento di una pagina HTML fosse perso o fuori ordine, la pagina risulterebbe illeggibile o corrotta.
5. **Possibile domanda di approfondimento orale** Come viene gestito il **controllo di flusso** in TCP e qual è il ruolo del campo **Window** nell'header?.

**84. Cos’è il Three-Way Handshake?**

1. **Definizione formale** Il **TCP 3-Way Handshake** è la sequenza di tre segmenti scambiati tra un client e un server che precede la trasmissione dei dati applicativi. Serve a **stabilire e sincronizzare** la connessione orientata tra i due host, concordando i numeri di sequenza iniziali (ISN - Initial Sequence Number).
2. **Spiegazione semplificata** È il rito in tre passaggi per aprire una linea di comunicazione.
   1. Il Client chiede di sincronizzarsi (SYN=1).
   2. Il Server accetta e chiede a sua volta la sincronizzazione (SYN=1, ACK=1).
   3. Il Client conferma di aver ricevuto l'accettazione (ACK=1). Una volta completato, la connessione è aperta e monitorata.
3. **Punti chiave da memorizzare**
   1. Sequenza di tre segmenti (SYN, SYN-ACK, ACK).
   2. Scopo: **stabilire e sincronizzare** la connessione.
   3. Avviene **prima** della trasmissione dei dati applicativi.
   4. Utilizza i flag **SYN** (Synchronize) e **ACK** (Acknowledge).
4. **Esempio concreto** Un attacco **DDOS** (Distributed Denial of Service) può sfruttare il Three-Way Handshake bombardando il server con messaggi SYN senza mai completare l'ultimo ACK, esaurendo le risorse del server e impedendo risposte legittime.
5. **Possibile domanda di approfondimento orale** Spiega la funzione del **Sequence Number** e dell'**Acknowledgement Number** nello scambio dei tre segmenti del Handshake.

**85. Funzione del Sequence Number.**

1. **Definizione formale** Il **Sequence Number** è un campo presente nell'header del segmento TCP la cui funzione è numerare i **byte dei dati applicativi sequenzialmente**. Questo permette all'host ricevente di **riordinare correttamente i segmenti** che possono essere arrivati in ordine sparso (tipico delle reti a commutazione di pacchetto).
2. **Spiegazione semplificata** È il contatore dei dati. Il TCP numera ogni singolo byte del messaggio originale. Il *Sequence Number* di un segmento è semplicemente il numero assegnato al **primo byte di quel segmento**. Quando i pacchetti arrivano disordinati, il sistema operativo usa questi numeri per rimettere insieme il messaggio finale.
3. **Punti chiave da memorizzare**
   1. Si trova nell'header del segmento TCP.
   2. Numera i **byte** dei dati (payload) sequenzialmente.
   3. Garantisce il **corretto ordine** dei dati.
   4. È un meccanismo cruciale per l'**affidabilità** del TCP.
4. **Esempio concreto** Se invii un file da 1000 byte diviso in due segmenti (S1 e S2), S1 avrà un Sequence Number *X* e S2 avrà un Sequence Number *X + 500* (ipotizzando 500 byte per segmento). Se S2 arriva prima di S1, il Sequence Number permette di rimetterli nell'ordine corretto.
5. **Possibile domanda di approfondimento orale** Spiega come il Sequence Number si collega al campo **Acknowledgement Number** per garantire l'affidabilità.

**86. Funzione del Checksum.**

1. **Definizione formale** Il **Checksum** è un campo di 16 bit nell'header del segmento TCP (e anche nell'header del frame Ethernet) la cui funzione è garantire l'**integrità** dei dati. Il mittente calcola un valore hash basato su una funzione matematica e lo inserisce nel campo Checksum. Il ricevente ripete lo stesso calcolo sui dati ricevuti e confronta il risultato con il Checksum ricevuto.
2. **Spiegazione semplificata** È la "prova di non manomissione" del segmento. Prima di inviare, il sistema calcola una specie di "somma di controllo" e la allega. Se, durante il viaggio, anche un solo bit viene alterato, la somma di controllo ricalcolata dal destinatario non corrisponderà più a quella allegata, indicando che il segmento è corrotto.
3. **Punti chiave da memorizzare**
   1. Garantisce l'**integrità** e la correttezza dei dati.
   2. È una **funzione matematica** applicata ai dati.
   3. Se i valori non coincidono, si richiede la **ritrasmissione**.
   4. Presente sia nel Livello di Trasporto (TCP/UDP) che in Data-Link (Frame Check Sequence).
4. **Esempio concreto** Se un rumore sulla linea altera un bit di un segmento TCP, il Checksum non corrisponderà. Il TCP scarterà il segmento corrotto e utilizzerà il meccanismo di Acknowledgement per richiedere al mittente la ritrasmissione del segmento non valido.
5. **Possibile domanda di approfondimento orale** Qual è la differenza tra l'uso del Checksum in TCP e l'uso di una Funzione di Hash crittografica (come SHA) per l'integrità nel TLS Record Protocol?.

### 2, UDP

**88. Cos’è UDP?**

1. **Definizione formale** **UDP (User Datagram Protocol)** è un protocollo di **Livello di Trasporto** che si basa sul concetto di trasmissione di **datagrammi**. È un protocollo **non orientato alla connessione** e **non affidabile**, che privilegia la velocità e la bassa latenza sulla garanzia di consegna e l'ordine dei pacchetti.
2. **Spiegazione semplificata** È un protocollo molto veloce e leggero perché non si preoccupa di stabilire una connessione preventiva, né di verificare se i dati sono arrivati a destinazione, in che ordine o integri. Se il dato viene perso, non chiede la ritrasmissione. È veloce perché non ha il sovraccarico di TCP (niente Handshake, niente Sequence Number, niente richieste di ritrasmissione).
3. **Punti chiave da memorizzare**
   1. **Non affidabile** e **Non orientato alla connessione**.
   2. **Veloce** (ha minore *overhead* rispetto a TCP).
   3. Non utilizza il *Sequence Number* e non richiede la ritrasmissione in caso di errore.
   4. Utilizzato quando la velocità è prioritaria rispetto alla garanzia di consegna (es. streaming).
4. **Esempio concreto** Il **DNS (Domain Name System)** utilizza prevalentemente UDP (Porta 53) per le query client-server, perché le richieste sono piccole e la velocità di risposta è cruciale. Se una query fallisce, il client la ripete, senza il bisogno dell'overhead di TCP.
5. **Possibile domanda di approfondimento orale** Quali problemi di sicurezza possono nascere dal fatto che il DNS utilizza prevalentemente UDP?

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
   1. **TCP** è cruciale per la ricostruzione corretta del messaggio, poiché i pacchetti possono arrivare in ordine sparso.
   2. UDP non ha la logica per **riordinare i segmenti**.
   3. TCP richiede il **3-Way Handshake** prima di ogni trasmissione.
3. **Esempio concreto** **FTP** e **HTTP** usano TCP perché è necessario che il codice HTML o un file da trasferire arrivino perfettamente integri. Lo streaming video (live) usa spesso UDP per minimizzare la latenza.

Guardare un video su YouTube in streaming può usare UDP (perché perdere un po' di dati non ferma il video), ma scaricare un file immagine usa TCP, perché l'immagine deve essere scaricata perfettamente e completamente.

1. **Possibile domanda di approfondimento orale** Come gestisce TCP il problema della **congestione** e del **flusso** per evitare di sovraccaricare il ricevente?

A quale livello si verifica la **segmentazione** dei dati e come viene definita la dimensione massima (MTU) del segmento?.

**90. Applicazioni tipiche TCP.**

1. **Definizione formale** Le applicazioni tipiche che utilizzano **TCP** sono quelle che richiedono **affidabilità** e la garanzia che i dati arrivino completi e nell'ordine corretto.
2. **Spiegazione semplificata** Sono tutti quei servizi dove anche una singola perdita o un errore potrebbero rendere inutilizzabile il dato, come la navigazione web, l'invio di email, o il download di file.
3. **Punti chiave da memorizzare**
   1. **HTTP/HTTPS** (navigazione web).
   2. **FTP** (trasferimento file).
   3. **SMTP, POP3, IMAP** (posta elettronica).
   4. **SSH** (accesso remoto sicuro).
4. **Esempio concreto** **HTTP** si appoggia su TCP (Porta 80) e **HTTPS** su TCP (Porta 443) per garantire che l'ipertesto (HTML) non venga corrotto o perso.
5. **Possibile domanda di approfondimento orale** Descrivi come un router che riceve un segmento TCP ne riconosce la destinazione (ovvero il processo).

**91. Applicazioni tipiche UDP.**

1. **Definizione formale** Le applicazioni tipiche che utilizzano **UDP** sono quelle che privilegiano la **bassa latenza** e la **velocità** di trasmissione, e che possono tollerare la perdita occasionale di datagrammi.
2. **Spiegazione semplificata** Sono i servizi che hanno bisogno di rapidità e dove il costo di rimediare a un errore sarebbe maggiore del beneficio, come i servizi di base di rete o le comunicazioni in tempo reale.
3. **Punti chiave da memorizzare**
   1. **DNS** (risoluzione dei nomi).
   2. **DHCP** (configurazione dinamica IP).
   3. **SNMP** (monitoraggio di rete).
   4. Applicazioni di **streaming** e **gaming** (dove la perdita di un pacchetto è accettabile, ma il ritardo no).
4. **Esempio concreto** Il protocollo **TFTP (Trivial File Transfer Protocol)** è un esempio che si appoggia su UDP, scelto per la sua velocità in operazioni semplici come il boot remoto.
5. **Possibile domanda di approfondimento orale** Perché il protocollo **TFTP** (che trasferisce file) è considerato "Trivial" e utilizza UDP, a differenza del normale FTP che usa TCP?

## J. Modelli di rete

**92. Cos’è il modello OSI?**

1. **Definizione formale** Il **Modello ISO-OSI (Open Systems Interconnection)** è un modello concettuale a **sette strati** sviluppato da ISO (International Standards Organisation) per standardizzare le regole di comunicazione, permettendo l'interconnessione di sistemi informatici eterogenei.
2. **Spiegazione semplificata** È un framework teorico creato per suddividere il complesso processo di comunicazione in rete in sette compiti logici (livelli). È nato quando le reti erano proprietarie, e serviva a stabilire regole comuni universali.
3. **Punti chiave da memorizzare**
   1. Modello concettuale a **sette livelli**.
   2. Scopo: stabilire **regole comuni (protocolli)** per l'interconnessione.
   3. **OSI** sta per *Open System Interconnection* (sistema aperto).
4. **Esempio concreto** Il concetto di **Livello di Sessione (Livello 5)** è un esempio di un livello concettuale definito da OSI, dove opera logicamente **TLS**.
5. **Possibile domanda di approfondimento orale** Perché si dice che il modello ISO-OSI è stato dimostrato "troppo complesso"?

**93. Livelli del modello OSI.**

1. **Definizione formale** Il modello OSI è composto da sette livelli, dal più basso (fisico) al più alto (applicativo), ognuno responsabile di specifiche funzionalità.
2. **Spiegazione semplificata** I sette livelli sono: Fisico (1), Data-Link (2), Rete (3), Trasporto (4), Sessione (5), Presentazione (6), e Applicazione (7).
3. **Punti chiave da memorizzare**
   1. **Livello 2 (Data-Link):** Utilizza il **MAC Address** e gestisce i **Frame**.
   2. **Livello 3 (Rete):** Utilizza l'**IP** e gestisce i **Packet** (routing).
   3. **Livello 4 (Trasporto):** Utilizza le **Porte** e gestisce i **Segmenti** (TCP/UDP).
   4. **Livello 7 (Applicazione):** Protocolli per l'utente finale (HTTP, DNS, SMTP).
4. **Esempio concreto** Quando un router instrada un pacchetto, opera al **Livello 3 (Rete)** leggendo l'indirizzo IP, il PDU (Protocol Data Unit) di questo livello è chiamato **Packet**.
5. **Possibile domanda di approfondimento orale** Descrivi il ruolo del **Livello di Presentazione (Livello 6)**.

**94. Cos’è il modello TCP/IP?**

1. **Definizione formale** Il modello **TCP/IP** è il modello architetturale a **quattro strati** effettivamente implementato, chiamato così dai due protocolli più importanti che contiene: **TCP** (Livello 4 - Trasporto) e **IP** (Livello 3 - Rete/Internet).
2. **Spiegazione semplificata** È la versione semplificata e pratica del modello OSI. Accorpa i livelli Sessione, Presentazione e Applicazione di OSI in un unico livello di **Applicazione**.
3. **Punti chiave da memorizzare**
   1. Modello a **quattro strati** (Host-to-Network, Internet/Network, Transport, Application).
   2. È il **modello reale** implementato su Internet.
   3. **TCP** e **IP** sono i protocolli chiave.
4. **Esempio concreto** Il protocollo **HTTP** (Livello Applicativo in TCP/IP) si appoggia direttamente sul **TCP** (Livello Trasporto in TCP/IP) per la trasmissione dei dati.
5. **Possibile domanda di approfondimento orale** Qual è il nome dato al PDU (Protocol Data Unit) del livello più basso (Host-to-Network)?

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
   1. TCP/IP è la **versione semplificata** che ha avuto successo nell'implementazione.
   2. La separazione tra i livelli 5, 6, 7 di OSI è la principale differenza strutturale.
3. **Esempio concreto** La **Crittografia** (come TLS) è concettualmente vista nel Livello di Sessione (OSI), ma nel modello TCP/IP viene implementata nel Livello di **Applicazione**.
4. **Possibile domanda di approfondimento orale** A quale livello si verifica l'operazione di **incapsulamento** e come cambia l'header del PDU ad ogni livello?

## K. Routing e inoltro

**96. Cos’è un router?**

1. **Definizione formale** Un **Router** è un dispositivo di **Livello 3 (Rete)** il cui scopo principale è **instradare (routing)** i pacchetti (PDU di Livello 3) tra reti diverse. Il Router opera leggendo l'**header di Livello 3** (l'indirizzo IP di destinazione).
2. **Spiegazione semplificata** È il dispositivo che decide il percorso migliore per far viaggiare i dati attraverso Internet, che è un insieme di reti. Ogni pacchetto deve sapere dove uscire per raggiungere il *next hop* (passaggio successivo) verso la destinazione finale.
3. **Punti chiave da memorizzare**
   1. Dispositivo di **Livello 3**.
   2. Funzione primaria: **Instradamento (Routing)**.
   3. Prende decisioni basate sull'**indirizzo IP** di destinazione.
   4. Utilizza la **Routing Table** (Tabella di Routing).
4. **Esempio concreto** Il Router, per inoltrare un pacchetto su una rete diversa, distrugge l'header del *Frame* (Livello 2) e ne crea uno nuovo (nuovo MAC di sorgente e destinazione).
5. **Possibile domanda di approfondimento orale** Spiega il ruolo della **NVRAM** e della **RAM** in un router, e cosa contengono in termini di configurazione.

**97. Funzione della routing table.**

1. **Definizione formale** La **Routing Table** è una struttura dati, che risiede nella **RAM** del router, contenente l'elenco delle **reti conosciute** e le istruzioni necessarie per inoltrare i pacchetti verso tali reti, specificando l'**interfaccia di uscita** e l'indirizzo IP del **next hop** (passaggio successivo).
2. **Spiegazione semplificata** È la "mappa" del router. Quando arriva un pacchetto, il router cerca l'indirizzo di rete di destinazione nella tabella. La tabella gli dice, per quella specifica rete, dove deve inviare il pacchetto per il prossimo salto, non necessariamente la destinazione finale.
3. **Punti chiave da memorizzare**
   1. Si trova in **RAM**.
   2. Contiene le reti conosciute (connesse, statiche, dinamiche).
   3. Indica l'indirizzo del **Next Hop**.
4. **Esempio concreto** Se la tabella ha una voce ip route 0.0.0.0 0.0.0.0 <Next Hop, questa è una **rotta di default** (*Last Resort*) che viene utilizzata se il router non ha trovato una rotta più specifica per la destinazione.
5. **Possibile domanda di approfondimento orale** Qual è il vantaggio per la **Tolleranza ai Guasti (Fault Tolerance)** di avere più route verso la stessa destinazione all'interno della Tabella di Routing?

**98. Cos’è una route?**

1. **Definizione formale** Una **Route** è una singola voce all'interno della Tabella di Routing che definisce il percorso da seguire per raggiungere una specifica **rete di destinazione** o un host. Essa include l'indirizzo IP della rete, la *Subnet Mask* e l'indirizzo del *Next Hop*.
2. **Spiegazione semplificata** È un'istruzione specifica: "Per arrivare a questa rete (Destinazione), devi passare da questo router (Next Hop)".
3. **Punti chiave da memorizzare**
   1. Voce elementare della **Tabella di Routing**.
   2. Definisce il **percorso** (Next Hop) verso una rete specifica.
   3. Può essere **Statica** o **Dinamica**.
4. **Esempio concreto** Quando un amministratore definisce una rotta statica con il comando ip route 192.168.2.0 255.255.255.0 10.0.0.2, la voce *10.0.0.2* rappresenta il **Next Hop**.
5. **Possibile domanda di approfondimento orale** A cosa serve la **Subnet Mask** nell'identificazione di una route in una rete?

**99. Differenza tra next-hop e destinazione finale.**

1. **Definizione formale** La **Destinazione Finale** è l'indirizzo IP completo della rete o dell'host che il pacchetto deve raggiungere. Il **Next Hop** è l'indirizzo IP dell'**interfaccia del router adiacente** (il salto logico successivo) a cui il pacchetto deve essere inoltrato per proseguire il suo cammino verso la destinazione finale.
2. **Spiegazione semplificata** Il router non deve conoscere tutta la strada (Destinazione Finale), deve solo sapere chi è il **prossimo router** (Next Hop) a cui passare il pacchetto. È come dare un pacco al corriere: non serve sapere tutte le tappe, solo l'indirizzo del prossimo centro di smistamento.
3. **Punti chiave da memorizzare**
   1. Il router conosce solo il **Next Hop**.
   2. Il Next Hop è un **router adiacente**.
   3. La Destinazione Finale è l'obiettivo del pacchetto.
4. **Esempio concreto** Per un pacchetto destinato a Roma (Destinazione Finale), un router a Firenze avrà come Next Hop il router che si trova a Bologna, non direttamente Roma.
5. **Possibile domanda di approfondimento orale** Perché l'uso del **Time To Live (TTL)** è essenziale nei pacchetti IP per evitare che errori di routing (loop) rendano il pacchetto infinito?

**100. Cos’è il routing statico?**

1. **Definizione formale** Il **Routing Statico** è un metodo di instradamento in cui le rotte all'interno della Tabella di Routing sono **inserite manualmente** dall'amministratore di sistema e rimangono fisse, a meno di un intervento manuale.
2. **Spiegazione semplificata** L'amministratore definisce "a mano" ogni percorso. Funziona bene finché la rete non cambia, perché ogni modifica richiede un aggiornamento manuale su ogni router coinvolto.
3. **Punti chiave da memorizzare**
   1. Rotte **definite manualmente** (dal sistemista).
   2. La rotta è **sempre la stessa**.
   3. Ideale per **reti piccole** o per rotte di **default**.
4. **Esempio concreto** Il comando ip route 0.0.0.0 0.0.0.0 1.1.1.1 (Rotta di default) è un esempio di routing statico utilizzato come *Last Resort* (ultima risorsa) quando non c'è una rotta specifica.
5. **Possibile domanda di approfondimento orale** In termini di Distanza Amministrativa, qual è il valore assegnato al routing statico e perché è un valore basso?

**101. Vantaggi e limiti del routing statico.**

1. **Confronto diretto**

|  |  |  |
| --- | --- | --- |
| Caratteristica | Vantaggi (Punti di forza) | Limiti (Debolezze) |
| Complessità | **Facile da configurare** e non genera traffico di aggiornamento. | Non si adatta automaticamente ai **guasti** o ai cambiamenti di topologia. |
| Sicurezza | Non richiede lo scambio di informazioni di routing (più sicuro). | **Assenza di Fault Tolerance**: se l'interfaccia si stacca, la rotta sparisce e il sistema non la rimuove o la rimpiazza automaticamente. |
| Scalabilità | Minore overhead. | **Non scalabile**; richiede molto tempo per l'amministrazione in reti grandi. |

1. **Spiegazione semplificata** Il vantaggio è la semplicità e il minor carico sulla CPU del router. Il limite è l'elasticità: se qualcosa si rompe o cambia, il router continua a credere nella rotta manuale, bloccando il traffico.
2. **Punti chiave da memorizzare**
   1. Vantaggio: Efficienza e **leggerezza** (non genera traffico di routing).
   2. Limite: **Zero dinamicità** o adattabilità ai guasti.
3. **Esempio concreto** In un'azienda con un solo router per l'accesso a Internet, l'unica rotta statica (la rotta di default) è efficiente, ma in una rete con 50 router e più percorsi, diventerebbe ingestibile.
4. **Possibile domanda di approfondimento orale** Perché si usa il routing statico in combinazione con il routing dinamico?

**102. Cos’è il routing dinamico?**

1. **Definizione formale** Il **Routing Dinamico** è un metodo di instradamento in cui i router utilizzano **protocolli dinamici** (**Link State** o **Distance Vector**) e **algoritmi** (Dijkstra o Bellman-Ford) per **scambiarsi informazioni** sulla topologia di rete, decidendo autonomamente la **rotta ottimale** in base a una metrica o un *costo*.
2. **Spiegazione semplificata** I router "parlano" tra loro usando protocolli specifici (come OSPF o RIP) e si scambiano continuamente aggiornamenti sulla mappa della rete. Se una strada si rompe o ne appare una più veloce, i router lo sanno e aggiornano le loro tabelle automaticamente.
3. **Punti chiave da memorizzare**
   1. Si basa su **protocolli** e **algoritmi** (es. RIP, OSPF).
   2. Decide la rotta migliore in base a un **costo/metrica**.
   3. Garantisce la **Tolleranza ai guasti (Fault Tolerance)**.
   4. Crea **traffico di rete** (overhead per gli aggiornamenti).
4. **Esempio concreto** Quando un'interfaccia di rete si disattiva (guasto), i protocolli dinamici come OSPF inviano un **Link State Packet** per informare subito gli altri router, permettendo un ricalcolo rapido del percorso (Fault Tolerance).
5. **Possibile domanda di approfondimento orale** Qual è il nome dato alla metrica utilizzata da **RIP** e come viene calcolata?

## L. Protocolli di routing

**103. Cos’è RIP?**

1. **Definizione formale** **RIP (Routing Information Protocol)** è un protocollo di routing dinamico che appartiene alla categoria **Distance Vector Protocol**. La sua metrica è il **numero di router (Hop Count)** che il pacchetto deve attraversare per raggiungere la destinazione.
2. **Spiegazione semplificata** RIP cerca la strada con il minor numero di salti (router). Ogni router che deve attraversare vale "1". È facile e non tiene conto della qualità della linea (ampiezza di banda o traffico). Ha una **visione locale** della rete.
3. **Punti chiave da memorizzare**
   1. **Distance Vector Protocol**.
   2. Metrica: **Hop Count** (numero di router).
   3. Limite massimo: **15 salti** (adatto solo per reti piccole).
   4. Utilizza l'algoritmo di **Bellman-Ford**.
4. **Esempio concreto** Se ci sono due strade per una destinazione, una con 2 router e l'altra con 5, RIP sceglierà quella con 2 router, anche se la strada con 5 router ha una banda di trasmissione enormemente superiore.
5. **Possibile domanda di approfondimento orale** Perché RIP è considerato obsoleto per le reti moderne?

**104. Cos’è OSPF?**

1. **Definizione formale** **OSPF (Open Shortest Path First)** è un protocollo di routing dinamico che appartiene alla categoria **Link State Protocol**. Sceglie la rotta migliore calcolando un **costo (metrica)** che è inversamente proporzionale all'ampiezza di banda del collegamento.
2. **Spiegazione semplificata** OSPF è il protocollo dinamico moderno. Invia pacchetti informativi (Link State Packet) a tutti gli altri router della sua area (*flooding*), costruendo una **visione globale** della topologia. Usa la banda per determinare la qualità: più banda = costo minore.
3. **Punti chiave da memorizzare**
   1. **Link State Protocol**.
   2. Metrica: **Costo** (calcolato su base **ampiezza di banda**).
   3. Utilizza l'algoritmo di **Dijkstra**.
   4. Ha una **visione globale** della topologia di rete.
4. **Esempio concreto** Il Costo OSPF si calcola con la formula $Costo = \frac{Banda\ di\ riferimento}{Ampiezza\ di\ banda}$. Questo permette di dare un valore basso (migliore) a un collegamento veloce (es. fibra).
5. **Possibile domanda di approfondimento orale** Qual è l'importanza di configurare un'**Interfaccia di Loopback** in OSPF?

**105. Cos’è EIGRP?**

1. **Definizione formale** **EIGRP (Enhanced Interior Gateway Routing Protocol)** è un protocollo di routing dinamico **proprietario di Cisco** e un'evoluzione di IGRP. È considerato un protocollo ibrido avanzato che, oltre all'ampiezza di banda, tiene conto anche del **traffico di rete** e dei **ritardi** (*delays*) per calcolare la metrica.
2. **Spiegazione semplificata** È un protocollo molto sofisticato che non si basa solo sulla velocità teorica della linea (come OSPF), ma anche su quanto è congestionata in quel momento. Il router invia dei pacchetti per misurare i ritardi effettivi (*round-trip time*) e prende la decisione di routing più informata.
3. **Punti chiave da memorizzare**
   1. Protocollo **proprietario Cisco**.
   2. Evoluzione di **IGRP**.
   3. Calcola la metrica tenendo conto di **traffico e ritardi**.
   4. È più complesso da configurare ma è migliore di OSPF in termini di scelta del percorso.
4. **Esempio concreto** EIGRP può preferire un percorso con banda leggermente inferiore rispetto a OSPF, se sa che il percorso più veloce è cronicamente congestionato dal traffico (gestendo il bilanciamento di carico in modo intelligente).
5. **Possibile domanda di approfondimento orale** Nonostante EIGRP sia proprietario, a quale categoria (Distance Vector o Link State) è più vicino dal punto di vista concettuale?

**106. Differenza tra Distance Vector e Link State.**

1. **Confronto diretto**

|  |  |  |
| --- | --- | --- |
| Caratteristica | Distance Vector (es. RIP) | Link State (es. OSPF) |
| Algoritmo | **Bellman-Ford**. | **Dijkstra**. |
| Conoscenza topologia | **Visione locale** (conosce solo i vicini). | **Visione globale** (conosce tutta la mappa). |
| Aggiornamento | Scambio periodico delle **tabelle di routing** tra vicini. | **Flooding** di **Link State Packet** (LSP) a tutta l'area. |
| Velocità Convergenza | **Lento** (aggiornamenti graduali). | **Veloce** (flooding immediato delle modifiche). |

1. **Spiegazione semplificata** I protocolli **Distance Vector** sono semplici, i router si fidano ciecamente del vicino (visione locale) e aggiornano lentamente. I protocolli **Link State** sono complessi, costruiscono una mappa precisa della rete (visione globale) e diffondono le modifiche in modo rapido (flooding).
2. **Punti chiave da memorizzare**
   1. **RIP** (Distance Vector) usa **Hop Count** come metrica.
   2. **OSPF** (Link State) usa **Costo/Banda** come metrica.
   3. **Flooding** in Link State garantisce una **convergenza rapida**.
3. **Esempio concreto** Se un collegamento si interrompe, un protocollo Link State lo saprà quasi immediatamente grazie al *flooding* di un LSP, mentre un protocollo Distance Vector potrebbe impiegare molto più tempo (rischio di loop temporanei o ritardi).
4. **Possibile domanda di approfondimento orale** Qual è il vantaggio del *flooding* di un LSP nonostante crei più traffico sulla rete rispetto all'aggiornamento parziale delle tabelle di routing?

**107. Cos’è l’algoritmo di Bellman-Ford?**

1. **Definizione formale** L'algoritmo di **Bellman-Ford** è l'algoritmo matematico utilizzato dai protocolli **Distance Vector** (come RIP) per calcolare i percorsi nella rete. Si basa su una **formula ricorsiva** che calcola la distanza (*distance*) fino a una destinazione aggregando i dati ricevuti dai router vicini.
2. **Spiegazione semplificata** È la logica che permette al router di dire: "Se il mio vicino C mi dice che può raggiungere la rete X in 3 salti, io la raggiungerò in $3+1=4$ salti." La conoscenza si propaga passo dopo passo, in modo ricorsivo.
3. **Punti chiave da memorizzare**
   1. Algoritmo fondamentale per i **Distance Vector** (RIP).
   2. **Ricorsivo** nel calcolo della distanza.
   3. La sua lentezza è la causa del lento **tempo di convergenza** di RIP.
4. **Esempio concreto** Se un router riceve una tabella di routing da un vicino con un percorso a una rete che non conosceva, aggiorna la sua tabella sommando il costo del vicino più uno (o il costo del segmento di connessione).
5. **Possibile domanda di approfondimento orale** Come risolve l'algoritmo di Bellman-Ford il problema dei loop di routing?

**108. Cos’è l’algoritmo di Dijkstra?**

1. **Definizione formale** L'algoritmo di **Dijkstra** è l'algoritmo matematico utilizzato dai protocolli **Link State** (come OSPF). Dopo aver ricevuto i **Link State Packet** (LSP) da tutti i router, questo algoritmo calcola il **percorso più breve (shortest path)** verso tutte le destinazioni, creando un albero di percorso ottimale.
2. **Spiegazione semplificata** È l'algoritmo che, avendo la mappa completa della rete (visione globale), può calcolare con precisione il percorso totale con il costo minimo verso ogni punto.
3. **Punti chiave da memorizzare**
   1. Algoritmo fondamentale per i **Link State** (OSPF).
   2. Richiede una **visione globale** della rete.
   3. Calcola il **percorso ottimale** basandosi sul **costo**.
4. **Esempio concreto** Quando un router OSPF ha finito la fase di *flooding* e ha costruito il database della topologia, lancia l'algoritmo di Dijkstra per generare la sua Tabella di Routing ottimale (utilizzando etichette con costo e nome).
5. **Possibile domanda di approfondimento orale** Perché l'algoritmo di Dijkstra è più veloce in termini di convergenza rispetto a Bellman-Ford?

**109. Cos’è il Hop Count?**

1. **Definizione formale** L'**Hop Count** (Conteggio dei Salti) è la metrica utilizzata dal protocollo **RIP**. Misura il **costo** di una rotta semplicemente contando il **numero di router** che un pacchetto deve attraversare per raggiungere la destinazione.
2. **Spiegazione semplificata** È la misura di distanza più semplice in una rete. Ogni router che si incontra vale 1. Se devo fare un salto, l'Hop Count è 1; se devo fare due salti (passare per due router), l'Hop Count è 2.
3. **Punti chiave da memorizzare**
   1. Metrica specifica del protocollo **RIP**.
   2. Misura il **numero di router** attraversati.
   3. Non tiene conto della **qualità della linea** (banda).
4. **Esempio concreto** In un percorso RIP, un collegamento a 100 Mbps ha lo stesso costo (1 Hop) di un collegamento a 10 Gbps, assumendo che in entrambi i casi ci sia un solo router intermedio.
5. **Possibile domanda di approfondimento orale** Perché l'Hop Count non è una metrica sufficiente per le reti moderne ad alta velocità?

**110. Limite dei 15 hop in RIP.**

1. **Definizione formale** Il protocollo **RIP** impone un limite massimo di **15 Hop Count** per una rotta. Se una destinazione richiede 16 o più salti, viene considerata **irraggiungibile** (*infinity*).
2. **Spiegazione semplificata** È un meccanismo di sicurezza e un limite intrinseco del protocollo. Superare 15 salti significa che la rete è troppo grande per RIP. Questo limite serve anche per prevenire i *loop* (pacchetti che girano all'infinito), limitando il raggio d'azione di RIP.
3. **Punti chiave da memorizzare**
   1. Limite massimo di **15 router**.
   2. Una destinazione a 16 hop è considerata **irraggiungibile**.
   3. Indica che RIP è adatto solo per **reti di piccole dimensioni**.
4. **Esempio concreto** Se una rete aziendale ha 16 router in linea, RIP non sarà in grado di instradare i pacchetti dal primo all'ultimo router; in questo caso si deve usare OSPF o EIGRP.
5. **Possibile domanda di approfondimento orale** Perché i protocolli *Distance Vector* sono più inclini a problemi di loop rispetto ai *Link State Protocol*?

**111. Concetto di cost in OSPF.**

1. **Definizione formale** Il **Costo** in OSPF (detto anche metrica) è il valore numerico assegnato a ciascun collegamento di rete. Esso viene calcolato automaticamente ed è determinato dal rapporto tra una **Banda di Riferimento** (di default 10⁸ Hz) e l'**ampiezza di banda** del collegamento.
2. **Spiegazione semplificata** È la misura di "quanto è faticoso" attraversare una linea. Se la linea è molto veloce (ha alta banda), il costo sarà basso, e OSPF preferirà quel percorso. Se la linea è lenta, il costo sarà alto.
3. **Punti chiave da memorizzare**
   1. Metrica specifica di **OSPF**.
   2. Basato sull'**ampiezza di banda**.
   3. Formula: $Costo = \frac{Banda\ di\ riferimento}{Ampiezza\ di\ banda}$.
   4. Il percorso migliore è quello con il **costo minore**.
4. **Esempio concreto** Un collegamento Ethernet a 100 Mbps avrà un costo inferiore rispetto a un vecchio collegamento a 10 Mbps, e l'algoritmo di Dijkstra sceglierà automaticamente il percorso cumulativo meno costoso.
5. **Possibile domanda di approfondimento orale** L'amministratore può modificare il Costo in OSPF? In che modo e perché dovrebbe farlo?

**112. Cos’è il flooding.**

1. **Definizione formale** Il **Flooding** è la tecnica di diffusione utilizzata dai protocolli **Link State** (come OSPF) per scambiare i **Link State Packet (LSP)**. Consiste nell'**inondare** un'area di rete (tutti i router di una specifica area) con il pacchetto di aggiornamento, in modo che ogni router riceva le informazioni sullo stato dei collegamenti.
2. **Spiegazione semplificata** È una tecnica di propagazione veloce: quando un router rileva una modifica, grida l'informazione a tutti gli altri router della sua zona in modo che tutti aggiornino la mappa in tempo reale.
3. **Punti chiave da memorizzare**
   1. Tecnica di diffusione di **OSPF** (Link State).
   2. Scopo: **inondare** la rete con i **LSP**.
   3. Garantisce una **convergenza rapida**.
   4. Avviene in modalità **Multicast**.
4. **Esempio concreto** Quando un router si accende in un'area OSPF, manda un pacchetto di Link State a un indirizzo **Multicast (Classe D)**, e tutti i router di quell'area lo ricevono e lo inoltrano ai loro vicini che non l'hanno ancora visto.
5. **Possibile domanda di approfondimento orale** Quali informazioni essenziali sono contenute in un **Link State Packet**?

## M. Autonomous Systems e Internet

**113. Cos’è un Autonomous System (AS)?**

1. **Definizione formale** Un **Autonomous System (AS)** è una **collezione di reti amministrate da un'unica autorità** o entità (come un ISP, una grande azienda o un'università), che determina in autonomia le proprie **politiche di instradamento**. Ogni AS è identificato da un numero univoco (un numero di 16 bit).
2. **Spiegazione semplificata** Internet è troppo grande per essere gestita da un unico protocollo. Per questo è divisa in grandi "blocchi" di rete, e ogni blocco (AS) è gestito internamente da un'unica autorità che decide le proprie regole (es. usare OSPF o RIP).
3. **Punti chiave da memorizzare**
   1. Insieme di reti sotto **un'unica autorità**.
   2. Definisce **autonomamente le politiche di routing**.
   3. Identificato da un numero univoco (AS number).
4. **Esempio concreto** Un **Internet Service Provider (ISP)** come Telecom Italia gestisce il proprio Autonomous System e decide come le sue reti interne si instradano.
5. **Possibile domanda di approfondimento orale** Quali sono i vantaggi di suddividere Internet in Autonomous Systems?

**114. Differenza tra IGP ed EGP.**

1. **Confronto diretto**

|  |  |  |
| --- | --- | --- |
| Caratteristica | IGP (Interior Gateway Protocol) | EGP (Exterior Gateway Protocol) |
| Ambito | **Routing interno** (all'interno di un singolo AS). | **Routing esterno** (tra diversi AS). |
| Protocolli | **RIP, OSPF, IGRP**. | **BGP** (Border Gateway Protocol). |
| Messaggi | Contengono solo informazioni sulle reti **dell'AS medesimo**. | Contengono informazioni sulle **rotte conosciute** dai due AS. |

1. **Spiegazione semplificata** **IGP** è il protocollo che si usa per mandare i dati da un punto A a un punto B all'interno della stessa zona (AS). **EGP** (principalmente BGP) è il protocollo più complesso che i router di confine (Border Router) usano per decidere come inviare i dati da una zona (AS) a un'altra zona.
2. **Punti chiave da memorizzare**
   1. IGP è per l'**interno** dell'AS.
   2. EGP è per la comunicazione **tra** AS.
   3. Esempi: OSPF è IGP, BGP è EGP.
3. **Esempio concreto** Un pacchetto che viaggia da un ufficio all'altro della stessa azienda (stesso AS) usa un protocollo **IGP** (come OSPF). Se deve andare su un sito esterno (AS diverso) usa un protocollo **EGP** (BGP) per uscire.
4. **Possibile domanda di approfondimento orale** Perché i messaggi BGP (EGP) sono necessariamente più complessi dei messaggi OSPF (IGP)?

**115. Cos’è BGP?**

1. **Definizione formale** **BGP (Border Gateway Protocol)** è il protocollo EGP (Exterior Gateway Protocol) attualmente utilizzato per scambiare informazioni di routing tra diversi **Autonomous Systems (AS)**.
2. **Spiegazione semplificata** È il "linguaggio" usato dai router di confine (*Border Router*) che si collegano alla dorsale Internet. BGP non si preoccupa solo del percorso più breve, ma soprattutto delle **politiche** e degli accordi tra i diversi fornitori di servizi (AS).
3. **Punti chiave da memorizzare**
   1. È un **EGP** (Exterior Gateway Protocol).
   2. Utilizzato per il **routing tra AS**.
   3. Funziona sui **Border Router**.
4. **Esempio concreto** Quando un ISP (che gestisce un AS) si collega a un altro ISP, utilizza BGP per negoziare e pubblicizzare le reti che può raggiungere, stabilendo quali AS sono raggiungibili tramite il suo vicino.
5. **Possibile domanda di approfondimento orale** Qual è la funzione esatta di un **Border Router**?

**116. Funzione dei Border Router.**

1. **Definizione formale** I **Border Router** sono router specializzati situati ai confini di un **Autonomous System (AS)**. La loro funzione è **gestire il routing tra AS diversi** scambiando messaggi **EGP** (come BGP) con i router dei sistemi autonomi vicini.
2. **Spiegazione semplificata** Sono i "doganieri" di ogni zona di rete (AS). Decidono quali dati possono entrare e uscire e, soprattutto, usano protocolli complessi (BGP) per comunicare con il mondo esterno, mantenendo l'ordine all'interno dell'AS e gestendo le relazioni con l'esterno.
3. **Punti chiave da memorizzare**
   1. Router che si trovano ai **confini di un AS**.
   2. Utilizzano protocolli **EGP** (BGP).
   3. Servono per l'interconnessione tra **reti amministrative diverse**.
4. **Esempio concreto** Un Border Router, dopo aver ricevuto un pacchetto destinato a un AS esterno, lo indirizza a un altro Border Router attraverso la dorsale in fibra.
5. **Possibile domanda di approfondimento orale** Qual è la differenza tra un router interno e un Border Router in termini di tabelle di routing gestite?

## N. NAT e ARP

**117. Cos’è NAT?**

1. **Definizione formale** **NAT (Network Address Translation)** è un protocollo implementato nei **router** che traduce l'**indirizzo IP sorgente** di un pacchetto (e talvolta la porta) in un indirizzo IP diverso. È essenziale per permettere ai dispositivi con **indirizzi IP privati** di comunicare con reti esterne (come Internet) che richiedono **indirizzi IP pubblici**.
2. **Spiegazione semplificata** È il traduttore di indirizzi sul tuo router di casa. Quando il tuo PC (che ha un indirizzo privato, es. 192.168.1.10) vuole accedere a Google, il NAT sul router sostituisce quell'indirizzo privato con l'unico indirizzo pubblico della tua casa, permettendo al pacchetto di viaggiare su Internet.
3. **Punti chiave da memorizzare**
   1. Protocollo implementato sui **Router**.
   2. Traduce indirizzi **privati** in indirizzi **pubblici** e viceversa.
   3. Necessario per la comunicazione tra reti con **indirizzi diversi**.
   4. Esistono tre tipi principali: **Statico, Dinamico e Overload (PAT)**.
4. **Esempio concreto** Se l'interfaccia del router è configurata come ip nat inside, si intende che quella porta riceverà indirizzi privati che dovranno essere tradotti prima di uscire (*inside global*).
5. **Possibile domanda di approfondimento orale** Spiega in dettaglio il problema del **masquerading** (molti a uno) nel NAT e come viene risolto dal **PAT**.

**118. Perché si usa NAT?**

1. **Definizione formale** Il NAT viene utilizzato principalmente per due motivi:
   1. **Conservazione degli Indirizzi IP Pubblici:** Permette a più host interni (con IP privati, non instradabili su Internet) di condividere un numero limitato (spesso uno solo) di indirizzi IP pubblici validi.
   2. **Sicurezza:** Maschera l'architettura interna della rete, poiché gli host interni non sono direttamente raggiungibili dall'esterno.
2. **Spiegazione semplificata** Si usa perché non ci sono abbastanza indirizzi IP pubblici per tutti i dispositivi del mondo. Il NAT risolve questo problema permettendo a migliaia di dispositivi privati di utilizzare lo stesso IP pubblico (risparmio) e, in più, offre una prima forma di sicurezza.
3. **Punti chiave da memorizzare**
   1. **Utilizzo efficiente degli indirizzi IP**.
   2. Indispensabile per far uscire gli **IP privati** su Internet.
   3. Rimuove gli **errori di configurazione** degli host (se associato a DHCP).
4. **Esempio concreto** Senza NAT, ogni dispositivo (PC, telefono, tablet) nella tua rete domestica avrebbe bisogno di un indirizzo IP pubblico univoco per navigare.
5. **Possibile domanda di approfondimento orale** Qual è la differenza tra l'uso del NAT nel contesto di IPv4 e la sua necessità in un'architettura IPv6?

**119. Cos’è il NAT Overload / PAT?**

1. **Definizione formale** **NAT Overload**, noto anche come **PAT (Port Address Translation)**, è la forma più comune di NAT. Consente a **più host interni (con IP privati)** di condividere un **singolo indirizzo IP pubblico**. La distinzione tra i vari host privati viene mantenuta tramite l'uso di **diverse porte sorgenti**.
2. **Spiegazione semplificata** È il NAT "molti-a-uno". Quando tre PC escono su Internet usando lo stesso indirizzo IP pubblico del router, il router assegna a ciascuno una porta sorgente diversa (es. PC1 usa porta 1025, PC2 usa porta 1026). Quando il traffico torna indietro, il router guarda la porta di destinazione per sapere a quale PC interno reindirizzare il pacchetto.
3. **Punti chiave da memorizzare**
   1. Permette la condivisione di un **singolo IP pubblico**.
   2. La traduzione avviene basandosi sulla **Porta (PAT)**, oltre all'IP.
   3. Essenziale per la **scalabilità** delle reti domestiche/aziendali.
4. **Esempio concreto** Un client interno usa una porta dinamica (es. 49152). Quando esce, il PAT traduce l'IP privato e la porta dinamica in un unico IP pubblico e una nuova porta, ad esempio, 209.165.200.254:50000.
5. **Possibile domanda di approfondimento orale** Spiega la differenza tra inside local e inside global nel contesto della configurazione NAT.

**120. Differenza tra IP privato e IP pubblico.**

1. **Confronto diretto**

|  |  |  |
| --- | --- | --- |
| Caratteristica | IP Privato | IP Pubblico |
| Instradabilità | Non instradabile su **Internet**. | **Instradabile** (Raggiungibile) su Internet. |
| Unicità | Unico **all'interno della rete locale**; può ripetersi in altre reti private. | **Unico a livello mondiale**. |
| NAT | Indirizzo di **sorgente** all'interno della rete. | Indirizzo a cui viene tradotto l'IP privato in uscita. |

1. **Spiegazione semplificata** L'**IP privato** è l'indirizzo che usi solo a casa o in ufficio per identificare i dispositivi all'interno della tua LAN (es. 192.168.x.x). L'**IP pubblico** è l'indirizzo che ti viene assegnato dal tuo ISP e che identifica la tua rete a livello globale su Internet.
2. **Punti chiave da memorizzare**
   1. L'IP privato è usato per le comunicazioni **locali**.
   2. L'IP pubblico è necessario per uscire **su Internet**.
   3. La traduzione tra i due avviene tramite **NAT**.
3. **Esempio concreto** Se mandi un pacchetto a un server di Google, il tuo router trasformerà l'indirizzo sorgente da IP privato a IP pubblico. Quando Google risponde, invierà il pacchetto all'IP pubblico (di destinazione).
4. **Possibile domanda di approfondimento orale** Quali sono i *range* di indirizzi IP riservati per l'uso privato (classi A, B, e C)?

**121. Cos’è ARP?**

1. **Definizione formale** **ARP (Address Resolution Protocol)** è un protocollo utilizzato per risolvere un indirizzo di **Livello 3 (IP)** nel suo corrispondente indirizzo di **Livello 2 (MAC Address)** all'interno della stessa rete locale o dominio di *broadcast*.
2. **Spiegazione semplificata** È il protocollo che dice: "Conosco l'indirizzo IP di questo computer (Livello 3), ma per spedire il pacchetto qui sulla LAN, ho bisogno del suo indirizzo fisico (MAC Address, Livello 2)". Ogni host mantiene una **tabella ARP cache** con queste associazioni.
3. **Punti chiave da memorizzare**
   1. Risolve **IP in MAC Address**.
   2. Necessario per le comunicazioni a **Livello 2**.
   3. Avviene all'interno dello stesso **dominio di Broadcast** (LAN/VLAN).
4. **Esempio concreto** Quando un host vuole inviare un pacchetto a un altro host sulla stessa VLAN, prima di creare il *Frame Ethernet* (Livello 2), deve conoscere il MAC Address del destinatario. Se non lo trova in cache, usa ARP.
5. **Possibile domanda di approfondimento orale** Cosa succede se un host deve comunicare con un altro host su una rete diversa? A quale MAC Address indirizza il pacchetto?

**122. Funzionamento di ARP Request.**

1. **Definizione formale** L'**ARP Request** è un messaggio inviato in modalità **Broadcast** sulla rete locale. Contiene l'indirizzo IP del dispositivo di cui si cerca il MAC Address.
2. **Spiegazione semplificata** Il computer che cerca un MAC grida a tutti sulla rete: "Ciao a tutti, chi ha questo indirizzo IP X.X.X.X, per favore mi dica il suo MAC Address?". Poiché è in Broadcast, raggiunge tutti gli host sulla LAN.
3. **Punti chiave da memorizzare**
   1. Messaggio inviato in **Broadcast**.
   2. Contiene l'**IP desiderato**.
   3. Pesa sulla rete in quanto **crea traffico**.
4. **Esempio concreto** Il client manda un Frame con il MAC Address di destinazione settato a FFFF.FFFF.FFFF (MAC di broadcast) e il suo IP. Tutti gli host ricevono la richiesta.
5. **Possibile domanda di approfondimento orale** Spiega in che modo la creazione di **VLAN** riduce l'impatto del traffico ARP sulla rete.

**123. Funzionamento di ARP Reply.**

1. **Definizione formale** L'**ARP Reply** è la risposta inviata in modalità **Unicast** (direttamente all'host richiedente) dal dispositivo che possiede l'indirizzo IP desiderato. Contiene il **MAC Address** risolto, permettendo al mittente di aggiornare la sua tabella **ARP Cache**.
2. **Spiegazione semplificata** Solo il computer che riconosce l'IP richiesto risponde con un messaggio privato dicendo: "Sono io, il mio indirizzo fisico è Y.Y.Y.Y". Il computer richiedente salva immediatamente questa associazione nella sua cache.
3. **Punti chiave da memorizzare**
   1. Risposta inviata in **Unicast**.
   2. Contiene l'associazione **IP-MAC** Address.
   3. L'host mittente aggiorna l'**ARP Cache**.
4. **Esempio concreto** Il computer che ha lanciato l'ARP Request riceve l'ARP Reply e usa il MAC Address appreso per costruire il Frame Ethernet contenente il pacchetto IP, destinato al MAC del ricevente.
5. **Possibile domanda di approfondimento orale** Un attacco **Man-in-the-Middle** può sfruttare l'ARP Reply. In che modo?

**124. Differenza tra IP e MAC.**

1. **Confronto diretto**

|  |  |  |
| --- | --- | --- |
| Caratteristica | Indirizzo IP (Internet Protocol) | MAC Address (Media Access Control) |
| Livello | **Livello 3** (Rete). | **Livello 2** (Data-Link). |
| Valore | **Generale** (Globale); assegnato dal sistemista (statico) o da DHCP (dinamico). | **Locale** (all'interno della LAN); **fisso** (hardware). |
| Funzione | Identifica la **rete** e il dispositivo per il routing. | Identifica un host **all'interno di una rete locale**. |
| Utilizzo | Viene modificato solo dai **router** (NAT). | Viene **distrutto e riscritto** ad ogni salto di router. |

1. **Spiegazione semplificata** L'**IP** è come l'indirizzo postale: serve per far viaggiare il pacchetto da una città all'altra (qualsiasi rete). Il **MAC** è come il numero civico: serve al postino locale (lo switch) per capire a quale esatta porta consegnare il pacchetto una volta arrivato nel palazzo (la LAN).
2. **Punti chiave da memorizzare**
   1. Il MAC Address ha **valore locale**, l'IP ha **valore generale**.
   2. Il Router interviene sul MAC (Livello 2) per rimetterlo.
   3. **ARP** è il ponte tra i due.
3. **Esempio concreto** Se invii un pacchetto da un PC a un router (che non è sulla tua rete), l'IP di destinazione sarà quello del server remoto, ma il MAC di destinazione del frame di uscita sarà il **MAC del Default Gateway** (l'interfaccia del tuo router).
4. **Possibile domanda di approfondimento orale** Spiega in che modo i due indirizzi (IP e MAC) sono combinati per identificare un processo specifico (*Socket*).

## O. Sicurezza di rete avanzata

**125. Cos’è un attacco Man-in-the-Middle?**

1. **Definizione formale** Un attacco **Man-in-the-Middle (MITM)** è una forma di intercettazione in cui un attaccante si posiziona **logicamente tra due soggetti comunicanti** (A e B). L'attaccante si spaccia per A nei confronti di B, e per B nei confronti di A, intercettando, leggendo e potenzialmente modificando tutte le comunicazioni scambiate.
2. **Spiegazione semplificata** È come un truffatore telefonico che si mette in mezzo alla tua chiamata con la banca: la banca crede di parlare con te e tu credi di parlare con la banca, ma il truffatore controlla l'intera conversazione.
3. **Punti chiave da memorizzare**
   1. L'attaccante si frappone **tra i due soggetti**.
   2. Lo scopo è **intercettare e modificare** la comunicazione.
   3. Spesso si sfrutta la vulnerabilità dell'**ARP** (ARP Cache Poisoning).
   4. È mitigato dall'uso di protocolli con **crittografia e autenticazione** come **TLS**.
4. **Esempio concreto** In un attacco **ARP Poisoning**, l'attaccante manipola la **ARP Cache** di A e B, facendogli credere che il MAC Address del router sia il MAC dell'attaccante (e viceversa).
5. **Possibile domanda di approfondimento orale** Perché l'uso di **HTTPS (TLS)** rende inefficaci gli attacchi MITM per quanto riguarda la segretezza?

**126. Cos’è lo spoofing?**

1. **Definizione formale** Lo **Spoofing** (camuffamento) è un attacco informatico in cui un'entità (attaccante) **falsifica la propria identità** spacciandosi per un'altra entità legittima, spesso alterando campi nell'header dei pacchetti di rete, come l'indirizzo **IP sorgente** o il **MAC Address**.
2. **Spiegazione semplificata** È l'atto di "mentire" sulla propria identità digitale. Ad esempio, invio un pacchetto facendo credere che provenga dal computer del tuo capo (falsificando l'indirizzo IP) per farti fare qualcosa.
3. **Punti chiave da memorizzare**
   1. Consiste nel **falsificare l'identità**.
   2. Può avvenire a Livello 2 (**MAC Spoofing**) o Livello 3 (**IP Spoofing**).
   3. L'**autenticazione** (es. certificati digitali) è la difesa primaria.
4. **Esempio concreto** Un attacco **DNS Spoofing** reindirizza l'utente a un sito web falso (es. un sito di *phishing* di una banca) facendogli credere che l'IP risolto dal DNS sia quello vero.
5. **Possibile domanda di approfondimento orale** Qual è la differenza tra IP Spoofing e l'uso legittimo del **NAT** (che pure modifica l'IP sorgente)?

**127. Cos’è un replay attack?**

1. **Definizione formale** Un **Replay Attack** è un attacco in cui un attaccante intercetta e **registra una trasmissione dati valida** (spesso una sequenza di autenticazione) e successivamente la **ritrasmette** (ripete) fraudolentemente, spacciandosi per il mittente legittimo, al fine di ottenere un accesso non autorizzato o eseguire un'azione indesiderata.
2. **Spiegazione semplificata** Se registrassi la tua password mentre ti autentichi su un sistema insicuro, potrei riprodurre l'intera sequenza di autenticazione registrata per accedere al sistema senza conoscere la password vera e propria.
3. **Punti chiave da memorizzare**
   1. Consiste nell'**intercettare e riutilizzare** dati validi.
   2. Sfrutta l'assenza di **controlli di tempo** o sequenza.
4. **Esempio concreto** In una modalità di cifratura come **Electronic Codebook (ECB)**, i blocchi cifrati sono indipendenti: un attaccante potrebbe riordinare o ripetere un blocco cifrato valido, sapendo che il blocco cifrato è sempre lo stesso per lo stesso blocco in chiaro.
5. **Possibile domanda di approfondimento orale** Quali modalità operative del DES (es. CBC) sono state introdotte per mitigare i problemi di **statistica** e **replay**?

**128. Cos’è un attacco brute-force?**

1. **Definizione formale** Un attacco **Brute-Force** (a forza bruta) è un metodo di attacco che consiste nel **tentare sistematicamente ogni possibile combinazione** di caratteri (nello spazio delle chiavi) fino a trovare la chiave di cifratura o la password corretta.
2. **Spiegazione semplificata** È come provare tutte le serrature possibili. L'attaccante non usa intelligenza o analisi, ma usa la potenza di calcolo per testare ogni singola ipotesi, sperando di trovare la combinazione giusta.
3. **Punti chiave da memorizzare**
   1. Consiste nel provare **tutte le combinazioni possibili**.
   2. La **lunghezza della chiave** (es. 56 bit per DES) determina la complessità temporale dell'attacco.
   3. È il metodo di attacco base per cui è stata progettata la crittografia (resistenza).
4. **Esempio concreto** Per l'algoritmo **DES** (56 bit utili), l'attacco *brute force* richiede una complessità temporale dell'ordine di $2^{56}$ tentativi, riducibili a $2^{55}$ in media.
5. **Possibile domanda di approfondimento orale** Perché una chiave a 56 bit (come quella di DES) è oggi considerata troppo piccola e vulnerabile agli attacchi Brute-Force?

**129. Cos’è un attacco Rainbow Table?**

1. **Definizione formale** Un attacco **Rainbow Table** è un attacco in cui un hacker utilizza **enormi database di hash pre-calcolati** per parole comuni. L'attaccante confronta l'hash rubato (es. hash di una password da un database) con la *Rainbow Table* per risalire rapidamente alla password in chiaro, evitando così la necessità di eseguire un attacco *brute force*.
2. **Spiegazione semplificata** Se tutti usano la stessa password "123456", anche se memorizzi l'hash, il risultato dell'hash è sempre lo stesso. La *Rainbow Table* è un archivio di tutti questi hash comuni. Invece di provare tutte le password, l'hacker cerca l'hash rubato nella tabella per trovare subito la password di partenza.
3. **Punti chiave da memorizzare**
   1. Sfrutta **database di hash pre-calcolati**.
   2. Rende inutile la protezione data dal solo **hashing** per password comuni.
   3. La soluzione è l'uso del **Salt**.
4. **Esempio concreto** Se l'hash di password123 viene trovato nel database rubato, l'hacker consulta la sua *Rainbow Table* e scopre immediatamente che la password in chiaro è password123.
5. **Possibile domanda di approfondimento orale** In che modo il **Salt** (un valore casuale aggiunto prima dell'hashing) rende inutili le *Rainbow Tables*?

## P. Concetti trasversali

**130. Perché la crittografia moderna è ibrida?**

1. **Definizione formale** La crittografia moderna è **ibrida** perché combina i **vantaggi** della crittografia **simmetrica** (velocità ed efficienza nella cifratura di grandi volumi di dati) con i **vantaggi** della crittografia **asimmetrica** (gestione sicura della chiave e autenticazione).
2. **Spiegazione semplificata** L'asimmetrica (lenta) viene usata solo una volta all'inizio della comunicazione per scambiarsi in modo segreto la **chiave di sessione** (chiave unica). Una volta scambiata la chiave, tutta la comunicazione (i dati veri e propri) avviene tramite crittografia simmetrica (veloce).
3. **Punti chiave da memorizzare**
   1. **Simmetrica** (AES) garantisce la **segretezza dei dati** (velocità).
   2. **Asimmetrica** (RSA/DH) garantisce lo **scambio sicuro della chiave di sessione** (sicurezza).
   3. L'efficienza è la motivazione chiave.
4. **Esempio concreto** Il protocollo **TLS** (usato in HTTPS) è l'esempio standard di crittografia ibrida. La Cipher Suite definisce quali algoritmi simmetrici e asimmetrici vengono usati per le diverse fasi.
5. **Possibile domanda di approfondimento orale** Spiega la differenza, nel contesto ibrido, tra l'uso dell'RSA per lo scambio chiavi e l'uso di algoritmi come **Diffie-Hellman** (DH) o **ECDH**.

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
   1. La sicurezza introduce **overhead**.
   2. La crittografia **asimmetrica** è l'operazione più costosa in termini di tempo.
   3. Protocolli affidabili (**TCP**) sono più lenti di protocolli non affidabili (**UDP**).
4. **Esempio concreto** L'uso del protocollo **TLS** (sicurezza) è più lento del semplice **HTTP** (prestazioni) perché aggiunge le fasi di Handshake, calcolo MAC e cifratura/decifratura dei dati.
5. **Possibile domanda di approfondimento orale** Come la crittografia **ibrida** risolve il compromesso tra sicurezza e prestazioni?

**133. Perché la gestione delle chiavi è critica?**

1. **Definizione formale** La gestione delle chiavi è critica perché la **sicurezza di un sistema crittografico risiede nella segretezza della chiave, non nell'algoritmo**. Se una chiave viene compromessa (intercettata o rubata), l'attaccante può accedere a tutti i dati cifrati con quella chiave, annullando l'efficacia del sistema.
2. **Spiegazione semplificata** La chiave è il segreto assoluto. Se l'algoritmo (la serratura) è noto a tutti, la chiave (il codice segreto) deve essere custodita. Se la chiave viene rubata, è come se non avessi mai usato la crittografia, e tutti i messaggi sono esposti.
3. **Punti chiave da memorizzare**
   1. La sicurezza risiede nella **segretezza della chiave**.
   2. La crittografia **simmetrica** ha il problema primario dello scambio sicuro della chiave.
   3. La compromissione della chiave privata di un server può permettere la decrittazione dello **storico delle comunicazioni**.
   4. **PKI** e **Certificati Digitali** sono strutture create per gestire in modo sicuro l'associazione tra chiave pubblica e identità.
4. **Esempio concreto** Se la chiave privata di una **Certification Authority** viene rubata, essa può essere usata per firmare falsi certificati, compromettendo l'intera infrastruttura di fiducia (PKI).
5. **Possibile domanda di approfondimento orale** Spiega come il concetto di **chiave effimera** (usata in alcuni algoritmi di Key Exchange) cerca di limitare il danno in caso di compromissione di una chiave privata.

# Risposta alle domande della Verifica

**Protocolli di Posta Elettronica**

**73. Cos’è SMTP?**

1. **Definizione formale** **SMTP (Simple Mail Transfer Protocol)** è il protocollo di **Livello Applicativo** utilizzato per l'**invio di email** tra **server di posta elettronica** (MTA, Mail Transfer Agent). Utilizza la porta **25** (non crittografata) o la **465** (crittografata).
2. **Spiegazione semplificata** È il protocollo che trasferisce l'email dal tuo server di posta a quello del destinatario. È come l'ufficio postale digitale che instrada la posta.
3. **Punti chiave da memorizzare**
   1. Protocollo di **Livello Applicativo**.
   2. Utilizzato per l'**invio** e il **trasferimento** di email.
   3. Porta standard **25** (non sicura) o **465** (crittografata).
4. **Esempio concreto** Quando il tuo client di posta (MUA) invia un'email, la inoltra al proprio server in uscita (MTA) usando **SMTP**.
5. **Possibile domanda di approfondimento orale** Qual è il ruolo del protocollo **MIME** nell'ambito della posta elettronica?

**74. Cos’è POP3?**

1. **Definizione formale** **POP3 (Post Office Protocol v3)** è un protocollo di **Livello Applicativo** utilizzato da un **client di posta** (MUA) per **ricevere e scaricare i messaggi** dalla casella di posta sul server al proprio dispositivo. Tradizionalmente, il protocollo prevede che il messaggio venga **scaricato e rimosso** dal server.
2. **Spiegazione semplificata** È il protocollo che permette al tuo client di svuotare la casella sul server. Il comportamento predefinito è il download e la rimozione dal server, liberando spazio.
3. **Punti chiave da memorizzare**
   1. Protocollo di **Livello Applicativo** per la **ricezione** di email.
   2. Comportamento tradizionale: **scarica e libera il server**.
   3. Porta standard: **110** (non crittografata) o **995** (crittografata).
   4. La conversazione prevede le fasi di **Autorizzazione, Transazione e Update**.
4. **Esempio concreto** Il client di posta usa POP3 per accedere alla casella sul *mailserver* e prelevare i messaggi, archivandoli sul proprio **PC locale**.
5. **Possibile domanda di approfondimento orale** Spiega come la fase di **Update** di POP3 contribuisce a liberare la casella di posta.

**75. Cos’è IMAP?**

1. **Definizione formale** **IMAP (Internet Message Access Protocol)** è un protocollo di **Livello Applicativo** per l'**accesso remoto alle email** che permette al client di **sincronizzare e gestire** i messaggi direttamente sul server.
2. **Spiegazione semplificata** A differenza di POP3, IMAP mantiene i messaggi **sul server** e ne sincronizza lo stato (letto, non letto, in cartella, ecc.) con i client, permettendo l'accesso da più dispositivi.
3. **Punti chiave da memorizzare**
   1. Protocollo di **Livello Applicativo**.
   2. I messaggi sono **sincronizzati** e rimangono sul **server**.
   3. Ideale per l'uso da **dispositivi mobili** o remoti.
   4. Porta standard: **143** (non crittografata) o **993** (crittografata).
4. **Esempio concreto** I moderni servizi di webmail utilizzano IMAP, perché assicura che se si sposta un'email su una cartella dal telefono, questa modifica è immediatamente visibile sul computer.
5. **Possibile domanda di approfondimento orale** Quali protocolli di gestione di rete si utilizzano per il monitoraggio dei dispositivi (come i mailserver)?

**Certificato Digitale e Pilastri della Sicurezza**

**47. Cos’è un certificato digitale?**

1. **Definizione formale** Un **Certificato Digitale** è un documento elettronico standardizzato (solitamente **X.509**) emesso da una **Certification Authority (CA)**. Il suo scopo è stabilire una **relazione certa e indiscutibile** tra un soggetto (ad esempio un server) e la sua **Chiave Pubblica**.
2. **Spiegazione semplificata** È come un passaporto elettronico: contiene la chiave pubblica del server e la firma di un ente fidato (la CA). Questa firma serve a certificare che la chiave pubblica appartiene davvero a quel server, prevenendo furti d'identità (*spoofing*).
3. **Punti chiave da memorizzare**
   1. Rilasciato da una **Certification Authority (CA)**.
   2. Associa un soggetto alla sua **Chiave Pubblica**.
   3. Standard **X.509**.
   4. Include la **Firma Digitale del Certificato** della CA per verificarne l'autenticità.
4. **Esempio concreto** Il Certificato X.509 di un server web contiene il suo **Nome Distinto del Soggetto (Subject DN)** e il periodo di validità (**Not Before** e **Not After**).
5. **Possibile domanda di approfondimento orale** Spiega come la **PKI (Public Key Infrastructure)** si basa sui Certificati Digitali.

**Come il certificato digitale garantisce i tre pilastri della crittografia (Autenticazione, Integrità, Segretezza)**

1. **Definizione formale** Il certificato digitale è uno strumento di **autenticazione** che **abilita** i meccanismi crittografici per garantire segretezza e integrità.
   * **Autenticazione:** Il certificato garantisce l'identità del server (o del client, se richiesto). Il client verifica la **Firma Digitale del Certificato** usando la chiave pubblica della CA, assicurandosi che il server non sia un impostore.
   * **Integrità:** Il client ricalcola la funzione **Hash** sul contenuto del certificato e lo confronta con l'**Hash firmato** dalla CA, verificando che il certificato non sia stato alterato.
   * **Segretezza:** Il certificato fornisce la **Chiave Pubblica** del destinatario. Questa chiave pubblica viene usata (tipicamente nella fase di Handshake TLS) per cifrare la **chiave di sessione** (o *pre-master key*), rendendo sicuro lo scambio e garantendo la riservatezza della successiva comunicazione simmetrica.
2. **Spiegazione semplificata** Il certificato è la prova d'identità del server. Se l'identità è provata (**Autenticazione**), il client si fida e usa la chiave pubblica nel certificato per cifrare un codice segreto (**Segretezza**). Inoltre, poiché il certificato è firmato con un Hash, siamo sicuri che il documento non è stato manomesso (**Integrità**).
3. **Punti chiave da memorizzare**
   * **Certificato** = Strumento di **Autenticazione** e verifica **Integrità**.
   * Fornisce la **Chiave Pubblica** per abilitare la **Segretezza** (scambio chiave simmetrica).
   * L'integrità è verificata confrontando due **Digest**.
4. **Esempio concreto** In un Handshake TLS, se il browser verifica con successo il certificato del server, ha la certezza dell'**Autenticazione** e può procedere a inviare la chiave di sessione cifrata con la **Chiave Pubblica** del server per la **Segretezza**.
5. **Possibile domanda di approfondimento orale** Perché si dice che la sicurezza di una comunicazione crittografata risiede nella segretezza della chiave e non nell'algoritmo?

**Algoritmo RSA**

**19. Cos’è RSA?**

1. **Definizione formale** **RSA** (Rivest, Shamir, Adleman) è l'algoritmo di crittografia **asimmetrica** più noto, impiegato per garantire sia la **segretezza** (cifrando con la chiave pubblica del destinatario) sia l'**autenticazione** (firmando con la chiave privata del mittente).
2. **Spiegazione semplificata** È l'algoritmo che rende possibile la crittografia a chiave pubblica/privata. La sua sicurezza si basa sul fatto che è estremamente difficile, se non impossibile, **fattorizzare** numeri primi molto grandi.
3. **Punti chiave da memorizzare**
   1. Algoritmo di crittografia **Asimmetrica**.
   2. Usato per **Segretezza** (chiave pubblica) e **Autenticazione** (chiave privata).
   3. La sua forza sta nella difficoltà di **fattorizzare numeri primi**.
   4. È utilizzato per lo **scambio di chiavi** in una *Cipher Suite* TLS.
4. **Esempio concreto (Matematico)** Il processo di RSA richiede l'individuazione di due numeri primi segreti ($p$ e $q$). Il prodotto di questi numeri ($N=p \cdot q$) forma la prima parte della chiave pubblica.
5. **Possibile domanda di approfondimento orale** Quali sono gli algoritmi simmetrici (come AES) che l'RSA aiuta a implementare nello scambio sicuro di chiavi?

**Esempio di funzionamento RSA (con $p=7$ e $q=13$)**

1. **Generazione delle Chiavi (Segreta e Pubblica):**
   * Scegliere due numeri primi segreti: $p=7$ e $q=13$.
   * Calcolare $N = p \cdot q$. Questo è un componente della chiave pubblica: $N = 7 \cdot 13 = 91$.
   * Calcolare $\phi(N)$, un valore che resta segreto: $b = (p-1)(q-1)$. $b = (7-1)(13-1) = 6 \cdot 12 = 72$.
   * Scegliere il valore $e$ (seconda chiave pubblica) tale che $MCD(e, b) = 1$. Ad esempio, $e=5$.
   * Calcolare $d$ (la chiave privata/segreta) tale che $d \cdot e \bmod b = 1$. Nel nostro esempio, $d = 29$, poiché $29 \cdot 5 \bmod 72 = 145 \bmod 72 = 1$.
   * **Chiave Pubblica:** $(N=91, e=5)$; **Chiave Privata:** $(d=29, N=91)$.
2. **Cifratura (Segretezza):**
   * Se il mittente vuole cifrare il messaggio $m=11$ usando la chiave pubblica del destinatario $(N=91, e=5)$.
   * La formula è $C = m^e \bmod N$.
   * $C = 11^5 \bmod 91$. Risultato (nel processo completo) è $C=72$.
3. **Decifratura:**
   * Il destinatario decifra il messaggio cifrato $C=72$ usando la sua chiave privata $(d=29, N=91)$.
   * La formula è $m = C^d \bmod N$.
   * $m = 72^{29} \bmod 91$. Risultato $m=11$.

**Protocolli SSL/TLS**

**36. Cos’è TLS?**

1. **Definizione formale** **TLS (Transport Layer Security)** è lo standard più diffuso (successore di SSL) che consiste in una *suite* di protocolli operante sopra il Livello di Trasporto (TCP), che fornisce funzionalità di **cifratura** (Segretezza), **autenticazione** e **integrità** dei dati scambiati su Internet.
2. **Spiegazione semplificata** È l'infrastruttura di sicurezza che rende possibile HTTPS. Stabilisce un **canale sicuro** e crittografato tra client e server, usando un approccio ibrido (asimmetrica per lo scambio chiavi, simmetrica per i dati).
3. **Punti chiave da memorizzare**
   1. È una **suite di protocolli** (non solo uno).
   2. Garantisce **Segretezza, Autenticazione e Integrità**.
   3. Opera al Livello di **Sessione** (OSI) o **Applicazione** (TCP/IP).
   4. Composto da **Handshake Protocol** e **Record Protocol**.
4. **Esempio concreto** **HTTPS** combina HTTP con SSL/TLS, utilizzando la porta **443** e l'icona del lucchetto nel browser per indicare una connessione cifrata.
5. **Possibile domanda di approfondimento orale** Spiega in che modo TLS risolve il problema principale della crittografia simmetrica (scambio chiavi).

**40. Cos’è l’Handshake TLS?**

1. **Definizione formale** L’**Handshake Protocol** è il sottoprocesso del TLS responsabile della **negoziazione** iniziale tra client e server. Durante questa fase, le due parti si accordano sulla **Cipher Suite** da utilizzare, eseguono l'**autenticazione del server** tramite certificato digitale, e stabiliscono una **chiave segreta di sessione** condivisa.
2. **Spiegazione semplificata** È la fase di "accordo" che avviene prima di qualsiasi scambio di dati criptati. Il client dice al server quali algoritmi conosce, il server ne sceglie uno (la *Cipher Suite*) e invia il suo certificato per dimostrare la sua identità. Il risultato è una chiave segreta unica per quella sessione.
3. **Punti chiave da memorizzare**
   1. È la fase di **negoziazione** del TLS.
   2. La comunicazione iniziale avviene in **chiaro**.
   3. Definisce la **Cipher Suite** per la sessione.
   4. Utilizzato per l'**autenticazione** del server e lo **scambio sicuro della chiave di sessione**.
4. **Esempio concreto** Il client invia un Client Hello con l'elenco delle Cipher Suite supportate. Il server risponde con un Server Hello, scegliendo la suite e inviando il certificato digitale.
5. **Possibile domanda di approfondimento orale** Quali algoritmi, oltre a RSA, sono usati per lo **scambio di chiavi** nella Cipher Suite?

**42. Cos’è il TLS Record Protocol?**

1. **Definizione formale** Il **TLS Record Protocol** è il protocollo che gestisce la **trasmissione sicura dei dati applicativi** dopo che l'Handshake ha stabilito i parametri. Prende i dati applicativi, li suddivide in blocchi (**Record Protocol Units**), applica la compressione (se concordata), calcola il **MAC (Message Authentication Code)** per l'integrità, e infine **cifra** il risultato con l'algoritmo simmetrico di sessione.
2. **Spiegazione semplificata** È il protocollo che esegue il vero e proprio "lavoro sporco" della cifratura. Segmenta il messaggio HTML, aggiunge un'impronta (*MAC*) per l'integrità e lo cifra con la chiave veloce appena scambiata, trasformandolo nel "Pacchetto TCP" criptato da inviare.
3. **Punti chiave da memorizzare**
   1. Gestisce la **trasmissione dei dati** cifrati.
   2. Suddivide i dati in **Record Protocol Units**.
   3. Usa funzioni Hash (es. SHA) per calcolare il **MAC** (Integrità).
   4. Applica la **cifratura simmetrica** (Segretezza).
4. **Esempio concreto** I dati di sessione (testo cifrato e MAC) vengono poi incapsulati in un segmento TCP per essere inviati sulla rete.
5. **Possibile domanda di approfondimento orale** Qual è la funzione del MAC all'interno del Record Protocol e perché è necessario se i dati sono già cifrati?

# Sicurezza Informatica

## A. Def: Sicurezza Informatica

**1. Definizione tecnica formale**

La **Sicurezza Informatica** è l'insieme di hardware, software, policy, procedure e soluzioni architetturali volte a garantire la **Disponibilità** (*Availability*), l'**Autenticazione**, l'**Autorizzazione** e l'**Integrità** dei dati e dei sistemi. Essa mira a prevenire intrusioni, manomissioni e falsificazioni.

**2. Spiegazione concettuale**

La sicurezza informatica non è solo crittografia, ma un approccio olistico per garantire che l'infrastruttura, il software e l'accesso umano siano tutti protetti. La crittografia e l'hashing (sicurezza logica) lavorano insieme ai concetti architetturali (HA/FT/DR) per assicurare che i servizi critici siano **sempre accessibili** (*Disponibilità*) e che i dati siano **corretti** (*Integrità*) e **riservati** (*Confidenzialità*).

**3. Obiettivo del modello**

L'obiettivo principale è la **Business Continuity** e il mantenimento di un accordato livello di prestazione operativa (*uptime*), oltre alla protezione dai tre tipi di minacce: naturali, umane (volontarie/involontarie) e guasti infrastrutturali.

**4. Componenti architetturali**

L'architettura sicura si basa su:

* **Ridondanza:** Eliminazione dei *Single Point of Failure*.
* **Failover/Failback:** Meccanismi automatici di gestione dei guasti.
* **Isolamento/Segmentazione:** Uso di firewall o VLAN per separare le zone di rete (es. Green Zone, DMZ, Red Zone).
* **Controlli Crittografici:** Implementazione di TLS/IPsec per garantire l'autenticazione e la segretezza dei dati in transito.

**5. Flusso logico di funzionamento**

In condizioni normali, l'architettura sicura gestisce il traffico con il massimo delle prestazioni, applicando policy di **Access Control List (ACL)** o *Packet Filtering* sui router/firewall. In caso di attacco, i meccanismi attivi (crittografia, autenticazione) mantengono l'integrità e la riservatezza, mentre la ridondanza e il failover (HA/FT) mantengono la disponibilità.

**6. Vantaggi e limiti**

* **Vantaggi:** Garantisce **Disponibilità** del sistema, **Tolleranza ai Guasti** e protezione da minacce multiple.
* **Limiti:** Introduce **overhead** (per la crittografia e i meccanismi di ridondanza) e richiede una gestione complessa (es. VTP, Spanning Tree Protocol, ACL).

**7. Esempio astratto ma concreto**

Un *cluster attivo-passivo* di server applicativi con un *Load Balancer* in testa. Il *Load Balancer* (componente di HA) reindirizza le richieste al nodo attivo. Se il nodo attivo fallisce, i meccanismi di *failure detection* attivano il nodo passivo (*failover*), mantenendo la continuità del servizio con un *downtime* minimo (HA) o nullo (FT).

**8. Domanda di approfondimento tipica di un esame orale**

Come si collega il concetto di **Disponibilità** (pilastro della Sicurezza Informatica) all'uso di protocolli come **RIP** o **OSPF**?

## B. I Pilastri Infrastrutturali della Sicurezza (HA, FT, DR)

**I. High Availability (HA)**

1. **Definizione tecnica formale** L'**Alta Disponibilità (HA)** è una caratteristica di un sistema volta a garantire un livello concordato di prestazioni operative, solitamente misurato come *uptime* (tempo di attività), eliminando i *Single Point of Failure*. L'obiettivo standard è raggiungere il **99.999%** di *uptime*.
2. **Spiegazione concettuale** HA significa che i componenti critici sono ridondanti e che esistono meccanismi di *failover* automatici in grado di trasferire il carico di lavoro in caso di guasto. L'HA accetta una piccola quantità di *downtime* (fino a 5.26 minuti all'anno).
3. **Obiettivo del modello** Minimizzare il *downtime* e garantire la **continuità del servizio**.
4. **Componenti architetturali** **Ridondanza** dei componenti, meccanismi di **Failure Detection** (rilevamento dei guasti) e **Workload Redirection** (reindirizzamento del carico). Esempi includono l'uso di **Clustering Technologies** e *Load Balancer*.
5. **Flusso logico di funzionamento** In caso di guasto di un componente primario (es. un host), un componente ridondante (es. una VM su un altro host) subentra (*failover*) e gestisce il carico senza intervento umano.
6. **Vantaggi e limiti**
   * **Vantaggi:** Costo inferiore rispetto a FT; minimizzazione delle perdite finanziarie derivanti da interruzioni.
   * **Limiti:** Non garantisce *zero downtime*; c'è un breve periodo di indisponibilità (latenza) durante la fase di *failover*.
7. **Esempio astratto ma concreto** Un **cluster di server applicativi** con due nodi (N1 e N2). N1 è attivo e N2 è in *standby passivo*. Se N1 fallisce, il sistema rileva l'errore e trasferisce il servizio su N2 in pochi secondi, causando un *downtime* minimo.
8. **Domanda di approfondimento tipica di un esame orale** Come si utilizza il protocollo **OSPF** (Link State Protocol) per implementare l'Alta Disponibilità nel routing?

**II. Fault Tolerance (FT)**

1. **Definizione tecnica formale** La **Tolleranza ai Guasti (FT)** è la proprietà che consente a un sistema di **continuare a operare correttamente** anche in presenza di guasti di uno o più dei suoi componenti. FT è una versione più stringente di HA, focalizzata sull'erogazione di **zero downtime**.
2. **Spiegazione concettuale** FT significa che ogni applicazione critica gira contemporaneamente su **due componenti speculari e accoppiati** (mirroring). Se un componente fallisce, l'altro prende il controllo *istantaneamente*, senza alcun ritardo.
3. **Obiettivo del modello** Garantire **zero downtime**.
4. **Componenti architetturali** **Ridondanza stretta** ottenuta tramite l'esecuzione simultanea di un'applicazione su due componenti che si **rispecchiano** (*mirroring*). Tutte le modifiche e gli input sul componente primario sono duplicati sul secondario.
5. **Flusso logico di funzionamento** I carichi di lavoro sono eseguiti in parallelo su entrambi i componenti. In caso di corruzione o guasto del componente primario (es. una VM), il trasferimento del carico al componente secondario (la copia identica) avviene **immediatamente**.
6. **Vantaggi e limiti**
   * **Vantaggi:** **Massima continuità** del servizio (zero downtime), cruciale per applicazioni che non tollerano alcuna interruzione.
   * **Limiti:** Costo molto elevato; può operare a un **livello di prestazione ridotto** durante il guasto, poiché la priorità non è la performance, ma la funzionalità operativa.
7. **Esempio astratto ma concreto** Due server DB identici che eseguono simultaneamente la stessa istanza dell'applicazione (*tightly coupled components*). La memoria, lo stato e il disco vengono replicati in tempo reale (sincronizzazione). Se un disco primario fallisce, il sistema continua a scrivere sul disco secondario **senza che la transazione subisca interruzioni**.
8. **Domanda di approfondimento tipica di un esame orale** In che modo i meccanismi di FT sono legati al concetto di **Integrità** dei dati durante il *failover*?

**III. Disaster Recovery (DR)**

1. **Definizione tecnica formale** Il **Disaster Recovery (DR)** è una strategia complessa che include policy, *tool* e procedure volte al **recupero** o alla **continuazione** delle infrastrutture IT e dei sistemi vitali a seguito di un evento catastrofico (naturale, umano, o cyber-attacco) che rende **intere infrastrutture** indisponibili.
2. **Spiegazione concettuale** DR è un piano di emergenza per disastri su larga scala. Richiede una **sede secondaria (remota)** dove dati e carichi di lavoro possono essere ripristinati. L'obiettivo è riattivare l'operatività critica entro un RTO (*Recovery Time Objective*) concordato, focalizzandosi sul recupero dei dati.
3. **Obiettivo del modello** Recupero dei dati e **ripristino delle operazioni aziendali** dopo un evento distruttivo (catastrofico).
4. **Componenti architetturali** **Sito secondario remoto** (per il *failover* geografico), analisi delle dipendenze, configurazione di soluzioni di **replica dello storage** (*storage replication*) e procedure di **backup** (offline/online).
5. **Flusso logico di funzionamento** A seguito di un disastro che colpisce l'intera sede primaria, i dati critici e i carichi di lavoro vengono ripristinati (o trasferiti) nel sito secondario. Il processo utilizza soluzioni automatizzate di *failover* remoto per raggiungere gli obiettivi di tempo di recupero (RTO).
6. **Vantaggi e limiti**
   * **Vantaggi:** Fornisce resilienza contro **guasti infrastrutturali totali** e disastri che superano le capacità di HA/FT locali.
   * **Limiti:** Generalmente comporta un **RTO più lungo** rispetto a HA/FT, dato che il ripristino avviene su infrastrutture geograficamente distanti.
7. **Esempio astratto ma concreto** Una grande azienda mantiene una replica costante dei database (utilizzando un meccanismo di *storage replication*) in un **datacenter remoto**. Se la sede principale subisce un'interruzione di corrente prolungata, si esegue il *failover* sul sito remoto per riprendere il servizio in un'altra area geografica.
8. **Domanda di approfondimento tipica di un esame orale** In che modo la **Replica dei Dati** (tipica del DR) si differenzia dai meccanismi di **Redundancy** (tipici di HA/FT)?

## C. Confronto e Collegamento dei Concetti

**Confronto diretto (Architetture di Resilienza)**

|  |  |  |  |
| --- | --- | --- | --- |
| Caratteristica | High Availability (HA) | Fault Tolerance (FT) | Disaster Recovery (DR) |
| Obiettivo | Minimizzare il *downtime* (es. 5 minuti all'anno). | Garantire **Zero Downtime**. | Recupero e continuazione del business dopo **evento catastrofico**. |
| Tempo di ripristino | Veloce, con *downtime* minimo (necessita *failover*). | **Istantaneo** (nessun *downtime*). | Dipendente dal RTO (tempo di recupero concordato). |
| Continuità del servizio | Alta, ma con interruzione breve tollerata. | **Massima**, servizio ininterrotto. | Garanzia di ripresa delle operazioni critiche. |
| Tecniche tipiche | Cluster, Failover automatico, Load Balancing, Ridondanza. | Componenti *mirroring* strettamente accoppiati. | Siti remoti, Backup/Restore, Storage Replication. |
| Livello di protezione | Da guasti di singoli componenti/server. | Da guasti di componenti, garantendo la singola transazione. | Da guasti di intere infrastrutture/sedi. |

**Collegamento tra Sicurezza Logica e Infrastrutturale**

La sicurezza non è una sola fase, ma un *continuum* che lega la **protezione dei dati** (crittografia) alla **disponibilità del sistema** (HA/FT/DR).

|  |  |  |
| --- | --- | --- |
| Concetto Infrastrutturale | Ruolo nel Pilastro Logico | Protocolli di Supporto |
| HA/FT/DR | Garantisce la **Disponibilità**. | Routing dinamico (OSPF, RIP, EIGRP) per il *Failover*. |
| Autenticazione | Garantita prima di ogni connessione, anche tra nodi di un *cluster*. | **Certificati X.509** e crittografia asimmetrica. |
| Segretezza | I dati replicati (HA/FT/DR) devono essere cifrati sia *at rest* che *in transit*. | **TLS** (*Handshake*) per lo scambio chiavi. |
| Integrità | I dati sottoposti a *failover* o *restore* (DR) devono essere non alterati. | **Hashing/MAC** (es. TLS *Record Protocol*) per verificare l'assenza di manomissione. |

## D. Soluzioni Tecniche

**🟢 1. High Availability (HA) - Continuità Operativa**

L'obiettivo è minimizzare il *downtime* (punto di riferimento: **99.999%** di uptime) eliminando i **Single Point of Failure** (SPoF).

**Soluzioni Tecniche:**

* **Cluster Activo-Passivo (Failover):** Un nodo primario gestisce il carico, mentre un nodo secondario è in *standby* pronto a subentrare automaticamente in caso di guasto.
* **Load Balancing (Active-Active):** Un **Load Balancer** distribuisce le richieste tra più server attivi contemporaneamente. Se uno fallisce, il traffico viene reindirizzato agli altri senza interruzioni percepibili.
* **Ridondanza di Rete:** Utilizzo di protocolli di routing dinamico come **OSPF** o **EIGRP** per ricalcolare istantaneamente i percorsi in caso di interruzione di un link.
* **Virtualizzazione:** Utilizzo di funzionalità come *vSphere HA* per riavviare automaticamente le macchine virtuali su un altro host fisico se quello originale si guasta.

**🟡 2. Fault Tolerance (FT) - Tolleranza ai Guasti Estrema**

A differenza dell'HA, la FT punta a **zero downtime** e **zero perdita di dati**, anche durante il passaggio tra i nodi.

**Soluzioni Tecniche:**

* **Hardware Mirroring (Tightly Coupled):** Due sistemi identici eseguono le stesse istruzioni in parallelo.
* **Sincronizzazione della Memoria e dello Stato:** Ogni operazione di scrittura o modifica in RAM viene replicata istantaneamente sul nodo secondario.
* **RAID (Redundant Array of Independent Disks):** Implementazione di RAID 1 (Mirroring) o RAID 5/6 a livello di storage per evitare che il guasto di un disco blocchi il sistema.
* **Costi e Limiti:** È una soluzione molto costosa e complessa, riservata solo a transazioni critiche (es. sistemi bancari o medici).

**🔴 3. Disaster Recovery (DR) - Recupero Catastrofale**

Strategia per ripristinare i sistemi a seguito di un evento che rende indisponibile l'intera infrastruttura primaria (incendi, alluvioni, attacchi hacker massivi).

**Soluzioni Tecniche:**

* **Sito Secondario Remoto:** Una sede geograficamente distante dove replicare i dati.
* **Storage Replication:** Replica costante dei database e dei file system tra il sito primario e quello di DR (replica sincrona o asincrona).
* **Backup Strategici:**
  + **Backup Online:** Copie veloci su dischi o cloud.
  + **Backup Offline:** Copie su supporti fisici scollegati dalla rete per protezione contro i ransomware.
* **Metriche Fondamentali da citare nello scritto:**
  + **RTO (Recovery Time Objective):** Il tempo massimo necessario per tornare operativi.
  + **RPO (Recovery Point Objective):** La massima quantità di dati che l'azienda può permettersi di perdere (misurata in tempo, es. "perdiamo al massimo gli ultimi 15 minuti di dati").

**📑 Tabella di Sintesi per la Prova Scritta**

In una traccia d'esame, potresti dover confrontare queste architetture:

|  |  |  |  |
| --- | --- | --- | --- |
| Caratteristica | High Availability (HA) | Fault Tolerance (FT) | Disaster Recovery (DR) |
| Obiettivo | Ridurre il downtime | Zero downtime | Ripristino post-catastrofe |
| Downtime ammesso | Pochi minuti/anno | Nessuno | Dipende dal RTO concordato |
| Costo | Moderato | Molto Elevato | Variabile (alto per infrastruttura) |
| Tecnica Chiave | Cluster & Load Balancing | Mirroring sincrono | Replica geografica & Backup |

**Sicurezza di Rete – IPsec e VPN (Livello Rete)**

**Spiegazione Concettuale** **IPsec (IP Security)** non è un singolo protocollo, ma una *suite* di protocolli che opera a **Livello 3 (Rete)**. La sua funzione è trasformare il livello IP, che nasce non sicuro, in un canale logico protetto. A differenza di TLS (che opera a livello applicativo/sessione), IPsec protegge l'intero pacchetto IP, rendendo la sicurezza trasparente alle applicazioni sovrastanti.

**Protocolli Principali: AH vs ESP**

* **AH (Authentication Header):** Garantisce l'**Autenticazione** del mittente e l'**Integrità** dei dati (tramite Hash), ma **NON** la segretezza. I dati viaggiano in chiaro, ma firmati digitalmente. Protegge anche parti dell'header IP.
* **ESP (Encapsulating Security Payload):** È il protocollo più completo. Fornisce **Segretezza** (cifratura del payload), **Autenticazione**, **Integrità** e protezione anti-replay. È la scelta standard per le VPN che richiedono riservatezza.

**Modalità di Funzionamento**

* **Transport Mode:** Cifra solo il *payload* (i dati), lasciando l'header IP originale in chiaro. Si usa per comunicazioni **Host-to-Host** (es. gestione remota).
* **Tunnel Mode:** Cifra l'intero pacchetto IP originale (header + dati) e lo incapsula dentro un *nuovo* pacchetto IP. È la modalità obbligatoria per le **VPN Site-to-Site** (Gateway-to-Gateway), poiché nasconde la topologia interna delle reti.

**Il Protocollo IKE (Internet Key Exchange)** IPsec richiede la gestione automatica delle chiavi e delle associazioni di sicurezza (SA). Questo avviene tramite **IKE**, in due fasi:

1. **Phase 1:** I due dispositivi si autenticano e stabiliscono un canale sicuro iniziale.
2. **Phase 2:** All'interno del canale sicuro, negoziano i parametri specifici per il tunnel IPsec (algoritmi di cifratura/hash) e creano le SA per il traffico dati.

👉 **Collegamento alla Sicurezza:** IPsec in *Tunnel Mode* è la tecnologia fondante per le **VPN Site-to-Site**, permettendo di collegare due sedi aziendali attraverso una rete pubblica (Internet) garantendo riservatezza, integrità e autenticazione.

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

**Sicurezza Infrastrutturale e Fault Tolerance Hardware**

**Spiegazione Concettuale** La sicurezza include la **Disponibilità** (Availability). Esistono diversi livelli di protezione contro i guasti hardware.

* **HA (High Availability):** Minimizza il downtime. Se un nodo cade, il servizio viene riavviato su un altro nodo. C'è una breve interruzione.
* **FT (Fault Tolerance):** Garantisce **Zero Downtime**. Il sistema continua a operare senza interruzioni anche in caso di guasto.

**Il Concetto di Lockstep e FT Hardware** La vera Fault Tolerance si basa sul principio di **Lockstep** (o funzionamento in sincrono).

* **Sincronizzazione Continua:** Due componenti hardware (o VM) eseguono le *stesse istruzioni* nello *stesso momento*.
* **Ridondanza Hardware:** Piattaforme come *ftServer* utilizzano hardware completamente ridondato (CPU, memoria, I/O) impacchettato come un sistema unico. Se un componente si rompe, il gemello continua l'elaborazione senza perdere nemmeno un ciclo di clock o una transazione in memoria.

👉 **Collegamento alla Sicurezza:** La FT Hardware protegge l'**Integrità** dei dati "in-flight" (in memoria/processo) e garantisce la **Business Continuity** per applicazioni critiche dove il riavvio (HA) non è accettabile.

1. **Analisi delle Minacce e Resilienza**

**Spiegazione Concettuale** La sicurezza non parte dalla tecnologia, ma dall'analisi del rischio. Le minacce si classificano in base all'origine:

1. **Naturali:** Eventi fuori dal controllo umano (terremoti, alluvioni, incendi). Richiedono strategie di *Disaster Recovery* (siti remoti).
2. **Umane Volontarie:** Attacchi mirati dall'esterno (Hacker, Malware) o dall'interno (dipendenti infedeli, sabotaggio).
3. **Umane Involontarie:** Errori, imperizia, inesperienza o distrazione degli utenti o degli amministratori (es. cancellazione accidentale dati).
4. **Infrastrutturali:** Guasti Hardware, Bug Software, o architetture mal progettate (Single Point of Failure).

**Dal Rischio alla Continuità** L'analisi di queste minacce definisce le metriche **RTO** (tempo massimo offline) e **RPO** (massima perdita dati).

* Se il rischio è il guasto hardware $\rightarrow$ Soluzione: **HA/FT** (Cluster).
* Se il rischio è la catastrofe naturale $\rightarrow$ Soluzione: **Disaster Recovery** (Replica geografica).
* Se il rischio è l'errore umano/ransomware $\rightarrow$ Soluzione: **Backup** (Offline/Immutable).

👉 **Collegamento alla Sicurezza:** Un sistema sicuro deve prevedere il fallimento. La **Resilienza** è la capacità dell'architettura di assorbire questi eventi (minacce) e mantenere il servizio attivo (Business Continuity).


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

**INTEGRAZIONE 1: Approfondimento Tecnico IPsec**

**IPsec (Internet Protocol Security)** non è un semplice protocollo, ma una *suite* complessa di protocolli che opera a **Livello 3 (Rete)** per garantire sicurezza alle comunicazioni IP. La sua architettura si basa su tre pilastri: protocolli di sicurezza (AH/ESP), modalità di funzionamento e gestione delle chiavi (IKE).

**1. I Protocolli di Sicurezza: AH vs ESP**

Ogni pacchetto IPsec utilizza uno di questi due header per proteggere i dati.

* **AH (Authentication Header - RFC 2402):**
  + **Funzione:** Garantisce l'**autenticazione** dell'origine e l'**integrità** dei dati (tramite Hashing), assicurando che il pacchetto non sia stato alterato.
  + **Limite:** **NON fornisce confidenzialità** (cifratura). Il payload rimane leggibile in chiaro.
  + **Dettaglio Tecnico:** Protegge anche parti dell'intestazione IP originale (quelle immutabili). Nel pacchetto IP, è identificato dal protocollo numero **51**.
* **ESP (Encapsulating Security Payload - RFC 2406):**
  + **Funzione:** È il protocollo completo. Fornisce **Segretezza** (cifratura del payload), **Autenticazione**, **Integrità** e protezione anti-replay.
  + **Funzionamento:** Incapsula il payload originale (o l'intero pacchetto) in una nuova struttura cifrata. Nel pacchetto IP, è identificato dal protocollo numero **50**.

**2. Modalità di Funzionamento: Tunnel vs Transport**

* **Transport Mode (Modalità Trasporto):**
  + **Cosa protegge:** Cifra solo il **payload** del pacchetto IP (es. il segmento TCP/UDP), lasciando l'intestazione IP originale in chiaro.
  + **Utilizzo:** Tipico delle comunicazioni **End-to-End** (Host-to-Host), ad esempio per una sessione di amministrazione remota tra due PC nella stessa rete.
* **Tunnel Mode (Modalità Tunnel):**
  + **Cosa protegge:** Cifra l'**intero pacchetto IP originale** (Header + Payload). Il pacchetto cifrato viene "imbustato" dentro un **nuovo pacchetto IP** con nuove intestazioni (gli indirizzi dei Gateway VPN).
  + **Utilizzo:** È lo standard per le **VPN Site-to-Site** (Gateway-to-Gateway). È necessario quando il traffico deve attraversare una rete pubblica (Internet) nascondendo la topologia degli indirizzi privati interni.

**3. Il Protocollo IKE (Internet Key Exchange)**

La gestione manuale delle chiavi è impossibile su larga scala. IPsec usa **IKE** per automatizzare la negoziazione. Il processo avviene in due fasi:

* **Fase 1 (IKE Phase 1):** I due dispositivi (peer) si autenticano (tramite Pre-Shared Key o Certificati) e stabiliscono un canale sicuro iniziale crittografato.
* **Fase 2 (IKE Phase 2):** All'interno del canale sicuro della Fase 1, vengono negoziati i parametri specifici per il tunnel IPsec (quali algoritmi di cifratura/hash usare per i dati, es. AES e SHA) e vengono create le **SA** per il traffico dati.

**4. Security Association (SA)**

La **SA** è il concetto fondamentale di IPsec. È una connessione logica **unidirezionale** (Simplex).

* Se due host vogliono comunicare bidirezionalmente, devono stabilire **due SA** (una per l'andata, una per il ritorno).
* Una SA è identificata univocamente da una tripla: **<Indirizzo IP Destinazione, Protocollo (AH o ESP), SPI (Security Parameter Index)>**.
* Il database **SAD (Security Association Database)** nel router contiene i parametri attivi (chiavi, contatori) per ogni SA.

**INTEGRAZIONE 2: Proxy e Sicurezza Applicativa**

I Proxy operano a **Livello 7 (Applicazione)** agendo come intermediari totali: interrompono la connessione diretta tra sorgente e destinazione.

**1. Forward Proxy (Protezione Client)**

* **Funzione:** Si posiziona davanti ai **client** interni. Quando un utente vuole accedere a Internet, la richiesta va al Proxy, che la esegue per conto dell'utente.
* **Scopi di sicurezza:**
  + **Anonimato:** Nasconde l'IP del client interno al server esterno.
  + **Filtering:** Blocca l'accesso a siti non autorizzati (URL Filtering).
  + **Caching:** Memorizza le risorse scaricate per velocizzare gli accessi successivi.

**2. Reverse Proxy (Protezione Server)**

* **Funzione:** Si posiziona davanti ai **server** interni (es. Web Server aziendali). Accetta le richieste da Internet e le smista ai server backend.
* **Scopi di sicurezza:**
  + **Protezione:** Nasconde l'identità e l'IP reale dei server interni (pubblicando solo l'IP del Proxy).
  + **Offloading SSL:** Si occupa di gestire la crittografia HTTPS, alleggerendo il carico di lavoro dei server interni.
  + **Load Balancing:** Distribuisce il traffico in entrata su più server per evitare sovraccarichi (DDoS mitigation).

**INTEGRAZIONE 3: Firewall Avanzati**

L'evoluzione dei firewall ha superato il semplice controllo di porte e indirizzi IP.

**1. Deep Packet Inspection (DPI)**

A differenza dei firewall *Packet Filtering* (che guardano solo l'header), la **DPI** analizza il **Payload** (il contenuto dati) del pacchetto fino al livello 7.

* **Obiettivo:** Riconoscere e bloccare dati appartenenti a virus, worm, o protocolli applicativi specifici nascosti (es. traffico P2P su porta 80).
* **Contesto:** Permette di applicare regole basate sul contenuto reale, non solo sulla porta dichiarata.

**2. Next Generation Firewall (NGFW)**

Il NGFW è la fusione in un'unica piattaforma (appliance) di diverse tecnologie di sicurezza che tradizionalmente erano separate:

* **Application Awareness:** Riconosce l'applicazione che sta generando traffico (es. distinguere Facebook Chat da Facebook Games) indipendentemente dalla porta usata.
* **IPS (Intrusion Prevention System):** Rileva e blocca attacchi attivi in tempo reale.
* **Integrazione con Threat Intelligence:** Si aggiorna costantemente sulle nuove minacce globali.
* **Identità Utente:** Le regole non si basano solo su IP, ma sull'utente autenticato (es. Active Directory).

**INTEGRAZIONE 4: Casi Studio (Hardware vs Software)**

**1. Cisco ASA (Adaptive Security Appliance)**

* **Ruolo:** È lo standard industriale per i **Firewall Hardware** di tipo Enterprise.
* **Caratteristiche:**
  + È un dispositivo fisico dedicato con processori ottimizzati per gestire traffico ad alta velocità.
  + Funge da Gateway di sicurezza perimetrale, gestendo Firewall Stateful, VPN (IPsec e SSL) e prevenzione intrusioni.
  + Garantisce alte prestazioni e stabilità per reti aziendali complesse.

**2. IPFire**

* **Ruolo:** È un esempio eccellente di **Firewall Software** open source (basato su Linux).
* **Caratteristiche:**
  + Può essere installato su un comune PC/Server dotato di due schede di rete (RED interface per Internet, GREEN interface per la LAN).
  + Integra funzionalità avanzate come **Proxy Server**, VPN gateway, e IDS/IPS in un'unica distribuzione gratuita.
  + Ideale per PMI o scuole che necessitano di sicurezza robusta senza i costi di hardware proprietario.

**INTEGRAZIONE 5: Tabella di Mappatura Sicurezza (Modello OSI)**

Ecco come i protocolli di sicurezza studiati si posizionano sulla pila ISO/OSI e TCP/IP.

|  |  |  |  |
| --- | --- | --- | --- |
| Livello OSI | Livello TCP/IP | Protocollo di Sicurezza | Funzione Principale |
| 7. Applicazione | **Applicazione** | **PGP / GPG** | Crittografia delle email e dei file (dati a riposo/transito). |
| 7. Applicazione | **Applicazione** | **SSH / HTTPS** | Canali sicuri per amministrazione remota e web. |
| 5. Sessione | **Applicazione** | **SSL / TLS** | Crittografia ibrida, autenticazione server/client. |
| 3. Rete | **Internet** | **IPsec (Tunnel/Transport)** | Cifratura pacchetti IP, VPN Site-to-Site. |
| 2. Data Link | **Accesso alla Rete** | **L2TP / PPTP** | Tunneling (spesso usati con IPsec). |
| 2. Data Link | **Accesso alla Rete** | **WPA2 / WPA3 / 802.1Q** | Cifratura Wi-Fi e segmentazione VLAN. |

Ecco l'analisi e l'integrazione richieste, strutturate come materiale didattico avanzato per la preparazione all'Esame di Stato.

**1) GAP ANALYSIS DETTAGLIATA**

1. **Lacune Infrastrutturali Critiche (IPsec & VPN):**
   * **Mancanza:** Dettaglio tecnico sugli header **AH** e **ESP**. Il documento cita IPsec ma non spiega *come* garantisce integrità vs confidenzialità a livello di pacchetto.
   * **Superficialità:** La distinzione tra **Tunnel Mode** e **Transport Mode** è spesso confusa.
   * **Mancanza:** Il ruolo del protocollo **IKE** (Fase 1 e 2) nella negoziazione delle chiavi è assente.
2. **Architetture di Difesa (Firewall & DMZ):**
   * **Superficialità:** La distinzione tra *Packet Filtering* (Stateless) e *Stateful Inspection* è presente ma necessita di maggiore rigore tecnico.
   * **Mancanza:** Concetto di **Deep Packet Inspection (DPI)** e **Next Generation Firewall (NGFW)**, fondamentali nel programma moderno.
   * **Mancanza:** Configurazione pratica delle zone (Green, Red, Orange/DMZ) e il concetto di **Bastion Host**.
3. **Proxy e Application Layer:**
   * **Mancanza:** La distinzione netta tra **Forward Proxy** (lato client) e **Reverse Proxy** (lato server). Questo è un concetto chiave per capire la protezione dei Web Server.
4. **Casi Reali (Laboratorio/Pratica):**
   * **Mancanza:** Riferimenti a **Cisco ASA** e **IPFire**, esplicitamente citati nel programma ministeriale fornito.

**2) INTEGRAZIONE CONCETTUALE (TESTO DA INSERIRE)**

Di seguito le sezioni scritte con taglio accademico/tecnico per colmare le lacune.

**A. IPsec e VPN: Approfondimento Tecnico (Livello 3 ISO/OSI)**

**IPsec (Internet Protocol Security)** non è un singolo protocollo, ma una suite standardizzata (IETF) che estende il protocollo IP introducendo sicurezza a Livello 3. A differenza di TLS (che opera sopra il livello 4), IPsec protegge l'intero pacchetto IP, rendendo la sicurezza trasparente alle applicazioni.

**1. Protocolli di Sicurezza: AH vs ESP**

* **AH (Authentication Header - RFC 2402):**
  + **Funzione:** Garantisce l'**autenticazione** del mittente e l'**integrità** dei dati, ma **NON la confidenzialità**.
  + **Meccanismo:** Calcola un Hash (HMAC) sull'intero pacchetto (header IP + payload). Protegge contro attacchi di *Replay* e *Spoofing*.
  + **Limite:** Non cifra il payload (i dati sono leggibili se intercettati).
* **ESP (Encapsulating Security Payload - RFC 2406):**
  + **Funzione:** Fornisce **confidenzialità** (cifratura), **autenticazione**, **integrità** e anti-replay.
  + **Meccanismo:** Cifra il payload (e opzionalmente l'header originale) e lo incapsula in un nuovo contenitore ESP. È lo standard per le VPN sicure.

**2. Modalità di Trasmissione**

* **Transport Mode:** Cifra solo il *payload* (es. il segmento TCP). L'header IP originale rimane in chiaro. Usato per comunicazioni end-to-end tra due host (es. amministrazione remota server).
* **Tunnel Mode:** Cifra l'**intero pacchetto IP** originale (Header + Payload) e lo incapsula in un nuovo pacchetto IP con nuove intestazioni (i gateway VPN). Usato per **VPN Site-to-Site**, nasconde la topologia interna delle reti private.

**3. Gestione Chiavi: IKE (Internet Key Exchange)** IPsec utilizza IKE (basato su Diffie-Hellman) per negoziare le chiavi e stabilire le **SA (Security Associations)**:

* **Fase 1:** Autenticazione dei peer (Gateway) e creazione di un canale sicuro iniziale.
* **Fase 2:** Negoziazione dei parametri specifici per il tunnel dati (algoritmi di cifratura/hash per le SA IPsec).

**Confronto: IPsec vs SSL/TLS VPN (es. OpenVPN)**

* **IPsec:** Standard per collegare sedi (Site-to-Site). Richiede configurazione lato kernel/OS. Difficile da far passare attraverso NAT/Firewall stretti.
* **OpenVPN (SSL):** Opera in *User Space* su TCP/UDP. Più facile da configurare per utenti mobili (Remote Access), attraversa facilmente i NAT (sembra traffico HTTPS).

**B. Firewall Avanzati e Architettura Perimetrale**

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

**E. Sicurezza per Livelli OSI (Tabella di Sintesi)**

Questa tabella è cruciale per rispondere a domande trasversali ("Come proteggiamo la rete a tutti i livelli?").

|                     |                                                 |                                                                                                           |
| ------------------- | ----------------------------------------------- | --------------------------------------------------------------------------------------------------------- |
| **Livello OSI**     | **Minaccia Principale**                         | **Tecnologia/Contromisura**                                                                               |
| **1. Fisico**       | Accesso fisico, taglio cavi, sniffing hardware. | Controllo accessi locali, cavi in fibra (più difficili da sniffare), ridondanza fisica.                   |
| **2. Data Link**    | MAC Spoofing, ARP Poisoning, VLAN Hopping.      | **Port Security** (mac-address sticky), **VLAN** (segmentazione), **802.1X** (autenticazione port-based). |
| **3. Rete**         | IP Spoofing, Sniffing, Accesso non autorizzato. | **IPsec** (confidenzialità), **Firewall** (Packet Filter), ACL sui router.                                |
| **4. Trasporto**    | Port Scanning, SYN Flood, Session Hijacking.    | **Firewall Stateful**, TLS (confine L4/L5), TCP Wrapper.                                                  |
| **7. Applicazione** | SQL Injection, XSS, Malware, Phishing.          | **WAF** (Web Application Firewall), **NGFW** (DPI), **Proxy**, Antivirus, Input Validation.               |

**F. Concetti Avanzati per l'Orale (Pillole da 10/10)**

* **Defense in Depth (Difesa in Profondità):** Non affidarsi a un singolo perimetro (es. solo firewall). La sicurezza deve essere a strati: sicurezza fisica + sicurezza perimetrale + sicurezza host + sicurezza applicativa + sicurezza dati. Se un livello fallisce, l'altro protegge (modello "a cipolla").
* **Principio del Privilegio Minimo (Least Privilege):** Ogni utente o processo deve avere *solo* i diritti strettamente necessari per svolgere il proprio compito. Questo limita il danno in caso di compromissione (es. un malware su un account guest fa meno danni che su un account admin).
* **Zero Trust Architecture:** "Non fidarti mai, verifica sempre". Non esiste più una zona "sicura" (LAN). Ogni richiesta, anche se proviene dall'interno, deve essere autenticata, autorizzata e cifrata.
* **Risk Analysis & Business Continuity:** La sicurezza non è assoluta ma basata sul rischio.
  + **RPO (Recovery Point Objective):** Quanto dati posso perdere? (Definisce la frequenza dei backup).
  + **RTO (Recovery Time Objective):** Quanto tempo posso stare fermo? (Definisce le tecnologie di HA/Cluster).

**3) SUGGERIMENTI PER DOMANDE D'ESAME TRASVERSALI**

Utilizza queste domande per testare la preparazione integrata:

1. *"Candidato, mi parli della differenza tra sicurezza del canale (IPsec/TLS) e sicurezza del perimetro (Firewall). Perché servono entrambe?"*
2. *"Come mitigherebbe un attacco Man-in-the-Middle a livello 2 (ARP) e come lo mitigherebbe a livello 3/4 (IP/TCP)?"*
3. *"Mi progetti un'architettura sicura per un Web Server aziendale, includendo DMZ, Firewall e Reverse Proxy. Quali regole metterebbe sul firewall?"*
4. *"Perché un Packet Filter non è sufficiente a bloccare un attacco SQL Injection? Quale dispositivo dovrei usare?"* (Risposta attesa: Perché opera a L3/L4, mentre l'SQLi è un payload L7; serve un WAF/NGFW).