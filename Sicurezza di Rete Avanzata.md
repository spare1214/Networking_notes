
## O. Sicurezza di rete avanzata

**125. Cos’è un attacco Man-in-the-Middle?**

1. **Definizione formale** Un attacco **Man-in-the-Middle (MITM)** è una forma di intercettazione in cui un attaccante si posiziona **logicamente tra due soggetti comunicanti** (A e B). L'attaccante si spaccia per A nei confronti di B, e per B nei confronti di A, intercettando, leggendo e potenzialmente modificando tutte le comunicazioni scambiate.
2. **Spiegazione semplificata** È come un truffatore telefonico che si mette in mezzo alla tua chiamata con la banca: la banca crede di parlare con te e tu credi di parlare con la banca, ma il truffatore controlla l'intera conversazione.
3. **Punti chiave da memorizzare**
   4. L'attaccante si frappone **tra i due soggetti**.
   5. Lo scopo è **intercettare e modificare** la comunicazione.
   6. Spesso si sfrutta la vulnerabilità dell'**ARP** (ARP Cache Poisoning).
   7. È mitigato dall'uso di protocolli con **crittografia e autenticazione** come **TLS**.
8. **Esempio concreto** In un attacco **ARP Poisoning**, l'attaccante manipola la **ARP Cache** di A e B, facendogli credere che il MAC Address del router sia il MAC dell'attaccante (e viceversa).
9. **Possibile domanda di approfondimento orale** Perché l'uso di **HTTPS (TLS)** rende inefficaci gli attacchi MITM per quanto riguarda la segretezza?

**126. Cos’è lo spoofing?**

1. **Definizione formale** Lo **Spoofing** (camuffamento) è un attacco informatico in cui un'entità (attaccante) **falsifica la propria identità** spacciandosi per un'altra entità legittima, spesso alterando campi nell'header dei pacchetti di rete, come l'indirizzo **IP sorgente** o il **MAC Address**.
2. **Spiegazione semplificata** È l'atto di "mentire" sulla propria identità digitale. Ad esempio, invio un pacchetto facendo credere che provenga dal computer del tuo capo (falsificando l'indirizzo IP) per farti fare qualcosa.
3. **Punti chiave da memorizzare**
   4. Consiste nel **falsificare l'identità**.
   5. Può avvenire a Livello 2 (**MAC Spoofing**) o Livello 3 (**IP Spoofing**).
   6. L'**autenticazione** (es. certificati digitali) è la difesa primaria.
7. **Esempio concreto** Un attacco **DNS Spoofing** reindirizza l'utente a un sito web falso (es. un sito di *phishing* di una banca) facendogli credere che l'IP risolto dal DNS sia quello vero.
8. **Possibile domanda di approfondimento orale** Qual è la differenza tra IP Spoofing e l'uso legittimo del **NAT** (che pure modifica l'IP sorgente)?

**127. Cos’è un replay attack?**

1. **Definizione formale** Un **Replay Attack** è un attacco in cui un attaccante intercetta e **registra una trasmissione dati valida** (spesso una sequenza di autenticazione) e successivamente la **ritrasmette** (ripete) fraudolentemente, spacciandosi per il mittente legittimo, al fine di ottenere un accesso non autorizzato o eseguire un'azione indesiderata.
2. **Spiegazione semplificata** Se registrassi la tua password mentre ti autentichi su un sistema insicuro, potrei riprodurre l'intera sequenza di autenticazione registrata per accedere al sistema senza conoscere la password vera e propria.
3. **Punti chiave da memorizzare**
   4. Consiste nell'**intercettare e riutilizzare** dati validi.
   5. Sfrutta l'assenza di **controlli di tempo** o sequenza.
6. **Esempio concreto** In una modalità di cifratura come **Electronic Codebook (ECB)**, i blocchi cifrati sono indipendenti: un attaccante potrebbe riordinare o ripetere un blocco cifrato valido, sapendo che il blocco cifrato è sempre lo stesso per lo stesso blocco in chiaro.
7. **Possibile domanda di approfondimento orale** Quali modalità operative del DES (es. CBC) sono state introdotte per mitigare i problemi di **statistica** e **replay**?

**128. Cos’è un attacco brute-force?**

1. **Definizione formale** Un attacco **Brute-Force** (a forza bruta) è un metodo di attacco che consiste nel **tentare sistematicamente ogni possibile combinazione** di caratteri (nello spazio delle chiavi) fino a trovare la chiave di cifratura o la password corretta.
2. **Spiegazione semplificata** È come provare tutte le serrature possibili. L'attaccante non usa intelligenza o analisi, ma usa la potenza di calcolo per testare ogni singola ipotesi, sperando di trovare la combinazione giusta.
3. **Punti chiave da memorizzare**
   4. Consiste nel provare **tutte le combinazioni possibili**.
   5. La **lunghezza della chiave** (es. 56 bit per DES) determina la complessità temporale dell'attacco.
   6. È il metodo di attacco base per cui è stata progettata la crittografia (resistenza).
7. **Esempio concreto** Per l'algoritmo **DES** (56 bit utili), l'attacco *brute force* richiede una complessità temporale dell'ordine di $2^{56}$ tentativi, riducibili a $2^{55}$ in media.
8. **Possibile domanda di approfondimento orale** Perché una chiave a 56 bit (come quella di DES) è oggi considerata troppo piccola e vulnerabile agli attacchi Brute-Force?

**129. Cos’è un attacco Rainbow Table?**

1. **Definizione formale** Un attacco **Rainbow Table** è un attacco in cui un hacker utilizza **enormi database di hash pre-calcolati** per parole comuni. L'attaccante confronta l'hash rubato (es. hash di una password da un database) con la *Rainbow Table* per risalire rapidamente alla password in chiaro, evitando così la necessità di eseguire un attacco *brute force*.
2. **Spiegazione semplificata** Se tutti usano la stessa password "123456", anche se memorizzi l'hash, il risultato dell'hash è sempre lo stesso. La *Rainbow Table* è un archivio di tutti questi hash comuni. Invece di provare tutte le password, l'hacker cerca l'hash rubato nella tabella per trovare subito la password di partenza.
3. **Punti chiave da memorizzare**
   4. Sfrutta **database di hash pre-calcolati**.
   5. Rende inutile la protezione data dal solo **hashing** per password comuni.
   6. La soluzione è l'uso del **Salt**.
7. **Esempio concreto** Se l'hash di password123 viene trovato nel database rubato, l'hacker consulta la sua *Rainbow Table* e scopre immediatamente che la password in chiaro è password123.
8. **Possibile domanda di approfondimento orale** In che modo il **Salt** (un valore casuale aggiunto prima dell'hashing) rende inutili le *Rainbow Tables*?
