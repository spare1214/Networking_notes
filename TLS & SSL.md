
## F. SSL / TLS

**38. A cosa serve TLS?**

1. **Definizione formale** **TLS (Transport Layer Security)** è una *suite* di protocolli (evoluzione di SSL) standardizzata che opera tipicamente al di sopra del livello di trasporto (Livello 5 OSI - Sessione). Il suo scopo è offrire funzionalità crittografiche (segretezza, autenticazione, integrità) ai protocolli applicativi sovrastanti, stabilendo un **canale sicuro** di comunicazione tra client e server.
2. **Spiegazione semplificata** TLS è la "tutela" che rende sicure le comunicazioni internet. Permette al tuo browser e a un sito web di mettersi d'accordo su quale algoritmo usare, scambiarsi chiavi in modo segreto e poi cifrare tutti i dati scambiati, in modo che nessuno possa spiarli o modificarli.
3. **Punti chiave da memorizzare**
   4. È una **suite di protocolli**.
   5. Fornisce **Segretezza, Autenticazione e Integrità**.
   6. Composto da **Handshake Protocol** (negoziazione) e **Record Protocol** (trasmissione dati).
   7. Rende sicuri protocolli come **HTTP** (diventando HTTPS).
   8. Si usa la **crittografia ibrida**.
9. **Esempio concreto** Ogni volta che si effettua un acquisto online, l'uso di **HTTPS** garantisce che i dati della carta di credito siano cifrati e che il sito sia autentico, grazie all'impiego del protocollo TLS.
10. **Possibile domanda di approfondimento orale** Descrivi il ruolo di una **Cipher Suite** nel funzionamento del TLS Handshake.

**39. In quale livello OSI opera TLS?**

1. **Definizione formale** Il protocollo **TLS (Transport Layer Security)** è una suite di protocolli che, nel modello a strati TCP/IP, si posiziona al **Livello di Applicazione**. Nel modello OSI, opera tipicamente al **Livello di Sessione (Livello 5)** o immediatamente al di sopra del Livello di Trasporto, fornendo servizi crittografici ai protocolli applicativi sovrastanti.
2. **Spiegazione semplificata** Nonostante il suo nome (*Transport Layer Security*), il TLS lavora nella parte alta dello *stack*. Si trova tra il livello applicativo (dove operano HTTP o FTP) e il livello di trasporto (TCP). Funge da "strato intermedio" che rende sicura la comunicazione tra i due processi sul client e sul server.
3. **Punti chiave da memorizzare**
   4. Opera al **Livello di Sessione (OSI)** o immediatamente sopra il Trasporto.
   5. Nel modello **TCP/IP** è considerato al **Livello Applicativo**.
   6. Fornisce servizi crittografici (Segretezza, Autenticazione, Integrità) ai protocolli superiori.
7. **Esempio concreto** Quando si usa **HTTPS**, il browser (Applicazione) non parla direttamente con il TCP, ma con il **TLS** (Livello Sessione/Applicazione), che si occupa di cifrare i dati prima di passarli al TCP per l'invio.
8. **Possibile domanda di approfondimento orale** Perché TLS è descritto come un protocollo *ibrido*?

**40. Cos’è l’Handshake TLS?**

1. **Definizione formale** L’**Handshake Protocol** è una delle due componenti principali della *suite* TLS, responsabile della **negoziazione** e dell'accordo sui parametri di sicurezza tra il client e il server prima che inizi lo scambio di dati dell'applicazione.
2. **Spiegazione semplificata** È la "stretta di mano" iniziale. Il client e il server si scambiano informazioni, concordano su quale **Cipher Suite** (l'insieme di algoritmi crittografici) utilizzare per la sessione, verificano l'autenticità del server tramite il **Certificato Digitale**, e si scambiano la **chiave di sessione** in modo sicuro.
3. **Punti chiave da memorizzare**
   4. È la fase di **negoziazione** del TLS.
   5. Stabilisce i parametri di sicurezza per la sessione.
   6. Include l'autenticazione del server (tramite certificato).
   7. Il risultato finale è la definizione di una **chiave segreta condivisa** (chiave di sessione) per la cifratura simmetrica.
8. **Esempio concreto** Quando un browser stabilisce una connessione HTTPS, invia un Client Hello contenente un elenco di *Cipher Suite* supportate. Il server risponde con un Server Hello, scegliendo la *Cipher Suite* definitiva e inviando il suo certificato.
9. **Possibile domanda di approfondimento orale** Descrivi il meccanismo con cui la chiave di sessione viene scambiata in modo sicuro durante l'Handshake.

**42. Cos’è il TLS Record Protocol?**

1. **Definizione formale** Il **TLS Record Protocol** è il protocollo della *suite* TLS che gestisce la **trasmissione sicura dei dati applicativi** dopo che l'Handshake ha stabilito i parametri di sicurezza. Prende i dati dall'alto (Applicazione), li suddivide in blocchi (**Record Protocol Units**), calcola il **MAC** (Message Authentication Code), li cifra e li trasmette.
2. **Spiegazione semplificata** È la parte del TLS che lavora durante la sessione vera e propria, gestendo il flusso dei dati. Il suo compito è prendere i dati, assicurarsi che non siano stati alterati (calcolando il MAC/Hash), cifrarli usando l'algoritmo simmetrico concordato (es. AES) e aggiungere l'header TLS per l'invio.
3. **Punti chiave da memorizzare**
   4. Gestisce la **trasmissione dei dati applicativi**.
   5. Segmenta i dati in **Record Protocol Units**.
   6. Aggiunge integrità tramite il calcolo del **MAC** (con funzioni Hash).
   7. Garantisce la segretezza tramite la **cifratura simmetrica** (es. AES).
8. **Esempio concreto** Dopo l'Handshake, una pagina HTML (dato applicativo) viene suddivisa dal Record Protocol. Per ogni blocco, viene calcolato un MAC (per l'integrità), e poi il blocco viene cifrato con la chiave di sessione.
9. **Possibile domanda di approfondimento orale** Spiega la funzione del MAC all'interno del Record Protocol e perché è necessario se si usa già la cifratura.

**43. Cos’è una Cipher Suite?**

1. **Definizione formale** Una **Cipher Suite** (letteralmente "suite di cifratura") è una combinazione predefinita di algoritmi crittografici che specificano l'insieme esatto di metodi da utilizzare in una sessione TLS per garantire le quattro funzioni fondamentali: **scambio di chiavi**, **autenticazione**, **cifratura simmetrica** (segretezza), e **calcolo del MAC** (integrità).
2. **Spiegazione semplificata** È un "pacchetto di istruzioni" che definisce tutte le scelte crittografiche per una data connessione, come un menu fisso. Ad esempio, una *Cipher Suite* può indicare: usa RSA per lo scambio di chiavi, ECDSA per l'autenticazione, AES-256 per cifrare i dati e SHA-384 per il controllo di integrità.
3. **Punti chiave da memorizzare**
   4. Definisce gli algoritmi per **scambio chiavi, autenticazione, cifratura e MAC**.
   5. Viene negoziata durante l'**Handshake TLS**.
   6. È un esempio di implementazione della **crittografia ibrida**.
7. **Esempio concreto** Un esempio di *Cipher Suite* è TLS\_ECDH\_ECDSA\_WITH\_AES\_256\_CBC\_SHA384, dove ogni parte indica un algoritmo specifico per una funzione (es. ECDH per lo scambio, AES\_256\_CBC per la cifratura).
8. **Possibile domanda di approfondimento orale** Quali algoritmi asimmetrici conosci che sono utilizzati per lo *scambio di chiavi* in una Cipher Suite?

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
   3. HTTPS = **HTTP + SSL/TLS** (crittografia).
   4. HTTP usa la porta **80**, HTTPS usa la porta **443**.
   5. HTTPS garantisce **segretezza** e **autenticazione** (tramite certificati).
6. **Esempio concreto** Quando digiti l'URL del tuo conto bancario, il prefisso https:// indica che tutti i dati scambiati, come le tue credenziali di accesso, vengono cifrati e protetti da TLS, rendendo sicura la trasmissione.
7. **Possibile domanda di approfondimento orale** Qual è il ruolo del Certificato Digitale X.509 in una connessione HTTPS?