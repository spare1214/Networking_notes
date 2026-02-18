
**Protocolli di Posta Elettronica**

**73. Cos’è SMTP?**

1. **Definizione formale** **SMTP (Simple Mail Transfer Protocol)** è il protocollo di **Livello Applicativo** utilizzato per l'**invio di email** tra **server di posta elettronica** (MTA, Mail Transfer Agent). Utilizza la porta **25** (non crittografata) o la **465** (crittografata).
2. **Spiegazione semplificata** È il protocollo che trasferisce l'email dal tuo server di posta a quello del destinatario. È come l'ufficio postale digitale che instrada la posta.
3. **Punti chiave da memorizzare**
   4. Protocollo di **Livello Applicativo**.
   5. Utilizzato per l'**invio** e il **trasferimento** di email.
   6. Porta standard **25** (non sicura) o **465** (crittografata).
7. **Esempio concreto** Quando il tuo client di posta (MUA) invia un'email, la inoltra al proprio server in uscita (MTA) usando **SMTP**.
8. **Possibile domanda di approfondimento orale** Qual è il ruolo del protocollo **MIME** nell'ambito della posta elettronica?

**74. Cos’è POP3?**

1. **Definizione formale** **POP3 (Post Office Protocol v3)** è un protocollo di **Livello Applicativo** utilizzato da un **client di posta** (MUA) per **ricevere e scaricare i messaggi** dalla casella di posta sul server al proprio dispositivo. Tradizionalmente, il protocollo prevede che il messaggio venga **scaricato e rimosso** dal server.
2. **Spiegazione semplificata** È il protocollo che permette al tuo client di svuotare la casella sul server. Il comportamento predefinito è il download e la rimozione dal server, liberando spazio.
3. **Punti chiave da memorizzare**
   4. Protocollo di **Livello Applicativo** per la **ricezione** di email.
   5. Comportamento tradizionale: **scarica e libera il server**.
   6. Porta standard: **110** (non crittografata) o **995** (crittografata).
   7. La conversazione prevede le fasi di **Autorizzazione, Transazione e Update**.
8. **Esempio concreto** Il client di posta usa POP3 per accedere alla casella sul *mailserver* e prelevare i messaggi, archivandoli sul proprio **PC locale**.
9. **Possibile domanda di approfondimento orale** Spiega come la fase di **Update** di POP3 contribuisce a liberare la casella di posta.

**75. Cos’è IMAP?**

1. **Definizione formale** **IMAP (Internet Message Access Protocol)** è un protocollo di **Livello Applicativo** per l'**accesso remoto alle email** che permette al client di **sincronizzare e gestire** i messaggi direttamente sul server.
2. **Spiegazione semplificata** A differenza di POP3, IMAP mantiene i messaggi **sul server** e ne sincronizza lo stato (letto, non letto, in cartella, ecc.) con i client, permettendo l'accesso da più dispositivi.
3. **Punti chiave da memorizzare**
   4. Protocollo di **Livello Applicativo**.
   5. I messaggi sono **sincronizzati** e rimangono sul **server**.
   6. Ideale per l'uso da **dispositivi mobili** o remoti.
   7. Porta standard: **143** (non crittografata) o **993** (crittografata).
8. **Esempio concreto** I moderni servizi di webmail utilizzano IMAP, perché assicura che se si sposta un'email su una cartella dal telefono, questa modifica è immediatamente visibile sul computer.
9. **Possibile domanda di approfondimento orale** Quali protocolli di gestione di rete si utilizzano per il monitoraggio dei dispositivi (come i mailserver)?

**Certificato Digitale e Pilastri della Sicurezza**

**47. Cos’è un certificato digitale?**

1. **Definizione formale** Un **Certificato Digitale** è un documento elettronico standardizzato (solitamente **X.509**) emesso da una **Certification Authority (CA)**. Il suo scopo è stabilire una **relazione certa e indiscutibile** tra un soggetto (ad esempio un server) e la sua **Chiave Pubblica**.
2. **Spiegazione semplificata** È come un passaporto elettronico: contiene la chiave pubblica del server e la firma di un ente fidato (la CA). Questa firma serve a certificare che la chiave pubblica appartiene davvero a quel server, prevenendo furti d'identità (*spoofing*).
3. **Punti chiave da memorizzare**
   4. Rilasciato da una **Certification Authority (CA)**.
   5. Associa un soggetto alla sua **Chiave Pubblica**.
   6. Standard **X.509**.
   7. Include la **Firma Digitale del Certificato** della CA per verificarne l'autenticità.
8. **Esempio concreto** Il Certificato X.509 di un server web contiene il suo **Nome Distinto del Soggetto (Subject DN)** e il periodo di validità (**Not Before** e **Not After**).
9. **Possibile domanda di approfondimento orale** Spiega come la **PKI (Public Key Infrastructure)** si basa sui Certificati Digitali.

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
   4. Algoritmo di crittografia **Asimmetrica**.
   5. Usato per **Segretezza** (chiave pubblica) e **Autenticazione** (chiave privata).
   6. La sua forza sta nella difficoltà di **fattorizzare numeri primi**.
   7. È utilizzato per lo **scambio di chiavi** in una *Cipher Suite* TLS.
8. **Esempio concreto (Matematico)** Il processo di RSA richiede l'individuazione di due numeri primi segreti ($p$ e $q$). Il prodotto di questi numeri ($N=p \cdot q$) forma la prima parte della chiave pubblica.
9. **Possibile domanda di approfondimento orale** Quali sono gli algoritmi simmetrici (come AES) che l'RSA aiuta a implementare nello scambio sicuro di chiavi?

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
   4. È una **suite di protocolli** (non solo uno).
   5. Garantisce **Segretezza, Autenticazione e Integrità**.
   6. Opera al Livello di **Sessione** (OSI) o **Applicazione** (TCP/IP).
   7. Composto da **Handshake Protocol** e **Record Protocol**.
8. **Esempio concreto** **HTTPS** combina HTTP con SSL/TLS, utilizzando la porta **443** e l'icona del lucchetto nel browser per indicare una connessione cifrata.
9. **Possibile domanda di approfondimento orale** Spiega in che modo TLS risolve il problema principale della crittografia simmetrica (scambio chiavi).

**40. Cos’è l’Handshake TLS?**

1. **Definizione formale** L’**Handshake Protocol** è il sottoprocesso del TLS responsabile della **negoziazione** iniziale tra client e server. Durante questa fase, le due parti si accordano sulla **Cipher Suite** da utilizzare, eseguono l'**autenticazione del server** tramite certificato digitale, e stabiliscono una **chiave segreta di sessione** condivisa.
2. **Spiegazione semplificata** È la fase di "accordo" che avviene prima di qualsiasi scambio di dati criptati. Il client dice al server quali algoritmi conosce, il server ne sceglie uno (la *Cipher Suite*) e invia il suo certificato per dimostrare la sua identità. Il risultato è una chiave segreta unica per quella sessione.
3. **Punti chiave da memorizzare**
   4. È la fase di **negoziazione** del TLS.
   5. La comunicazione iniziale avviene in **chiaro**.
   6. Definisce la **Cipher Suite** per la sessione.
   7. Utilizzato per l'**autenticazione** del server e lo **scambio sicuro della chiave di sessione**.
8. **Esempio concreto** Il client invia un Client Hello con l'elenco delle Cipher Suite supportate. Il server risponde con un Server Hello, scegliendo la suite e inviando il certificato digitale.
9. **Possibile domanda di approfondimento orale** Quali algoritmi, oltre a RSA, sono usati per lo **scambio di chiavi** nella Cipher Suite?

**42. Cos’è il TLS Record Protocol?**

1. **Definizione formale** Il **TLS Record Protocol** è il protocollo che gestisce la **trasmissione sicura dei dati applicativi** dopo che l'Handshake ha stabilito i parametri. Prende i dati applicativi, li suddivide in blocchi (**Record Protocol Units**), applica la compressione (se concordata), calcola il **MAC (Message Authentication Code)** per l'integrità, e infine **cifra** il risultato con l'algoritmo simmetrico di sessione.
2. **Spiegazione semplificata** È il protocollo che esegue il vero e proprio "lavoro sporco" della cifratura. Segmenta il messaggio HTML, aggiunge un'impronta (*MAC*) per l'integrità e lo cifra con la chiave veloce appena scambiata, trasformandolo nel "Pacchetto TCP" criptato da inviare.
3. **Punti chiave da memorizzare**
   4. Gestisce la **trasmissione dei dati** cifrati.
   5. Suddivide i dati in **Record Protocol Units**.
   6. Usa funzioni Hash (es. SHA) per calcolare il **MAC** (Integrità).
   7. Applica la **cifratura simmetrica** (Segretezza).
8. **Esempio concreto** I dati di sessione (testo cifrato e MAC) vengono poi incapsulati in un segmento TCP per essere inviati sulla rete.
9. **Possibile domanda di approfondimento orale** Qual è la funzione del MAC all'interno del Record Protocol e perché è necessario se i dati sono già cifrati?
