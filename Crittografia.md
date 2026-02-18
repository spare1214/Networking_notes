
## B. Crittografia simmetrica

**5. Cos’è la crittografia simmetrica?**

1. **Definizione formale** La crittografia simmetrica, definita anche **crittografia a chiave privata**, è un sistema di cifratura che impiega una **chiave unica** e segreta per eseguire sia l'operazione di cifratura del testo in chiaro da parte del mittente, sia la successiva decifratura da parte del ricevente.
2. **Spiegazione semplificata** È un metodo crittografico in cui si usa la stessa chiave per "chiudere" e "aprire" il messaggio. È il metodo più **veloce** per cifrare i dati perché le operazioni matematiche sono meno complesse rispetto all'asimmetrica.
3. **Punti chiave da memorizzare**
   4. Usa una **chiave unica** per cifrare e decifrare.
   5. È **veloce e sicura**.
   6. Il problema critico è la **condivisione sicura** della chiave.
   7. Algoritmi noti: **DES**, **3-DES**, **IDEA**, **AES**.
8. **Esempio concreto** L'algoritmo **AES** (Advanced Encryption Standard) è un cifrario simmetrico largamente utilizzato e preferito oggi, spesso impiegato all'interno di protocolli di sicurezza ibrida come TLS.
9. **Possibile domanda di approfondimento orale** Spiega in dettaglio la struttura di funzionamento di un cifrario a blocchi come il DES.

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
   4. Si basa su una **coppia di chiavi** (pubblica e privata).
   5. È usata per garantire **segretezza** e **autenticazione**.
   6. L'algoritmo più noto è l'**RSA**.
   7. È computazionalmente **più lenta** della simmetrica.
8. **Esempio concreto** Il funzionamento dell'algoritmo **RSA** si basa sulla difficoltà matematica di **fattorizzare numeri primi molto grandi**.
9. **Possibile domanda di approfondimento orale** In termini di sicurezza dei dati, quale delle due chiavi (pubblica o privata) deve essere custodita con assoluta segretezza e perché?.

**17. Come si garantisce la segretezza con chiavi asimmetriche?**

1. **Definizione formale** La segretezza si ottiene quando il mittente cifra il testo in chiaro utilizzando la **chiave pubblica del destinatario**. Dato che solo il destinatario possiede la corrispondente **chiave privata**, solo lui sarà in grado di decifrare il messaggio e ripristinare il testo in chiaro.
2. **Spiegazione semplificata** Se vuoi che solo il ricevente legga il messaggio, usi la sua chiave pubblica per nasconderlo. È come usare un lucchetto che tutti possono chiudere, ma solo il destinatario ha la chiave unica per aprirlo.
3. **Punti chiave da memorizzare**
   4. Mittente usa **Chiave Pubblica del Destinatario**.
   5. Destinatario usa **Chiave Privata propria**.
   6. Garantisce la **riservatezza** del contenuto.
7. **Esempio concreto** Durante l'Handshake TLS, il client cifra la **chiave di sessione** (o *pre master key*) utilizzando la **chiave pubblica del server** (ottenuta dal certificato). Questa chiave cifrata viene inviata al server, che la decifra con la sua chiave privata, garantendo la segretezza della chiave di sessione.
8. **Possibile domanda di approfondimento orale** Perché la segretezza non è l'unica proprietà necessaria? Se il messaggio è segreto, non potrebbe comunque essere stato alterato?.

**18. Come si garantisce l’autenticazione con chiavi asimmetriche?**

1. **Definizione formale** L'autenticazione è garantita quando il mittente usa la **propria chiave privata** per **firmare digitalmente** un messaggio (o, più comunemente, il suo *digest*). Qualsiasi utente può quindi verificare l'identità del mittente utilizzando la corrispondente **chiave pubblica** del mittente stesso.
2. **Spiegazione semplificata** Il mittente usa la sua chiave segreta per applicare un timbro unico al messaggio. Tutti possono vedere il timbro e, usando la chiave pubblica del mittente, possono confermare che quel timbro è autentico e che solo il possessore della chiave privata ha potuto crearlo.
3. **Punti chiave da memorizzare**
   4. Mittente usa la **Chiave Privata propria**.
   5. Si ottiene una **firma elettronica/digitale**.
   6. La verifica avviene con la **Chiave Pubblica del Mittente**.
   7. Garantisce la prova di **origine** del messaggio.
8. **Esempio concreto** Una **Certification Authority (CA)** autentica un **certificato digitale** apponendo la sua **Firma Digitale del Certificato** (generata con la sua chiave privata) sul contenuto del certificato (che include la chiave pubblica del server). Il browser verifica la CA usando la chiave pubblica della CA stessa.
9. **Possibile domanda di approfondimento orale** Spiega la relazione tra la **firma digitale** e la **funzione di Hash** nel processo di autenticazione asimmetrica.
