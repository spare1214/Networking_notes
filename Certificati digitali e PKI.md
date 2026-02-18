
**47. Cos’è un certificato digitale?**

1. **Definizione formale** Un certificato digitale (spesso basato sullo standard **X.509**) è un documento elettronico emesso da una **Certification Authority (CA)**. Il suo scopo è stabilire una **relazione certa e indiscutibile** tra un soggetto (come un server o una persona) e la sua **chiave pubblica**.
2. **Spiegazione semplificata** È come un "passaporto" elettronico per un sito web o un utente. Contiene l'identità del proprietario e la sua chiave pubblica, ed è timbrato (firmato) da un ente fidato (la CA). Questo timbro certifica che la chiave pubblica appartiene davvero al soggetto dichiarato, prevenendo i furti d'identità (*spoofing*).
3. **Punti chiave da memorizzare**
   4. Rilasciato da una **Certification Authority (CA)**.
   5. Associa in modo indiscutibile un soggetto alla sua **chiave pubblica**.
   6. Standard più comune è **X.509**.
   7. Fondamentale per l'**autenticazione** in protocolli come HTTPS.
8. **Esempio concreto** Il certificato di un server web come *www.google.com* contiene la chiave pubblica di Google. La **Firma Digitale del Certificato** (apposta dalla CA) garantisce che quella chiave pubblica sia effettivamente di Google.
9. **Possibile domanda di approfondimento orale** Qual è il campo all'interno del certificato X.509 che definisce per quanto tempo il certificato è considerato valido?

**48. Cos’è un certificato X.509?**

1. **Definizione formale** X.509 è lo **standard internazionale** che definisce il formato e le specifiche che un certificato digitale deve rispettare. Un certificato X.509 contiene campi obbligatori come la **versione** dello standard, il **numero di serie**, l'**algoritmo di firma** usato dalla CA, il **periodo di validità**, il **nome distinto dell'emittente (CA)**, il **nome del soggetto** e le informazioni sulla **chiave pubblica del soggetto**.
2. **Spiegazione semplificata** È semplicemente la "carta d'identità" digitale con un formato standard riconosciuto a livello globale. Garantisce che tutti i programmi (come i browser) sappiano esattamente dove trovare le informazioni chiave, come la chiave pubblica e la firma della CA, perché sono sempre nello stesso formato.
3. **Punti chiave da memorizzare**
   4. È lo **standard** di formato per i certificati digitali.
   5. Contiene informazioni sul **soggetto**, la sua **chiave pubblica** e la **CA**.
   6. Include la **Firma Digitale del Certificato** creata dalla CA.
7. **Esempio concreto** Il campo **Periodo di Validità** del certificato X.509 stabilisce la data di inizio ("Not Before") e la data di fine ("Not After") in cui il certificato è ritenuto attendibile.
8. **Possibile domanda di approfondimento orale** Qual è la differenza tra il Nome Distinto del Soggetto (*Subject DN*) e l'Identificatore Univoco Soggetto (*Subject Unique Identifier*) in un certificato X.509?

**50. Cos’è una CA (Certification Authority)?**

1. **Definizione formale** Una **Certification Authority (CA)** è un ente terzo, fidato e riconosciuto (spesso a livello statale), che ha il compito di **emettere e firmare digitalmente** i certificati X.509, garantendo così l'associazione tra l'identità del soggetto (server/utente) e la sua chiave pubblica. Le CA sono il pilastro della Public Key Infrastructure (PKI).
2. **Spiegazione semplificata** È l'ente che agisce come un "notaio" sul web. Quando vuoi un certificato, la CA verifica la tua identità e poi appone la sua firma digitale sul tuo certificato. Poiché tutti i browser si fidano delle CA più importanti (le cui chiavi pubbliche sono preinstallate), quando vedono la loro firma sul certificato, sanno che il certificato è valido e non falsificato.
3. **Punti chiave da memorizzare**
   4. Ente di **terza parte fidata** e riconosciuta.
   5. Emette e **firma i certificati digitali**.
   6. Custodisce la propria **chiave privata** in modo estremamente sicuro.
   7. È il componente centrale della **PKI**.
8. **Esempio concreto** Quando si visita un sito, il browser controlla la validità del certificato. Per farlo, usa la **chiave pubblica della CA** (che ha firmato il certificato) per decifrare la **Firma Digitale del Certificato** e verificare che non sia stata alterata.
9. **Possibile domanda di approfondimento orale** Cosa succede se la chiave privata di una Certification Authority viene compromessa?

**53. Come il browser verifica un certificato?**

1. **Definizione formale** Il browser (client) verifica un certificato X.509 ricevuto dal server in due modi principali:ò
   2. **Integrità/Autenticità:** Utilizza la **chiave pubblica della Certification Authority (CA)**, che ha emesso il certificato, per decifrare la **Firma Digitale del Certificato** contenuta nel documento. Se la decifratura è coerente, il certificato è autentico.
   3. **Integrità del Contenuto:** Ricalcola la funzione **Hash** sul certificato e confronta il **digest** ottenuto con quello contenuto all'interno della firma appena decifrata. Se i *digest* coincidono, il certificato non è stato alterato.
4. **Spiegazione semplificata** Il browser ha in memoria una lista di chiavi pubbliche di CA fidate. Quando riceve il certificato del server, usa la chiave pubblica della CA per sbloccare la "firma" presente sul certificato. Poi verifica che le informazioni sul certificato non siano state modificate. Se la firma della CA è valida e i dati sono integri, il browser si fida del server.
5. **Punti chiave da memorizzare**
   6. Applica la **chiave pubblica della CA** per la verifica.
   7. Verifica l'**autenticità** della firma della CA.
   8. Confronta il **digest ricalcolato** con quello firmato per l'**integrità**.
   9. Controlla anche il **periodo di validità**.
10. **Esempio concreto** Il client calcola l'hash di tutto il certificato. Poi decifra il *Digest firmato* (Firma Digitale del Certificato) usando la chiave pubblica della CA e confronta i due hash. Se sono uguali, la comunicazione è considerata sicura.
11. **Possibile domanda di approfondimento orale** Qual è il vantaggio, dal punto di vista dell'integrità, di firmare solo l'Hash del certificato e non l'intero certificato?

La **PKI** (*Public Key Infrastructure*) è un'infrastruttura che comprende hardware, software, persone, politiche e procedure necessarie per creare, gestire, distribuire, utilizzare, archiviare e revocare i certificati digitali.

Il suo obiettivo principale è stabilire una **relazione certa e indiscutibile** tra un'identità (un soggetto, come un server web o una persona) e la sua **Chiave Pubblica**.

I componenti fondamentali della PKI sono:

* **Certification Authority (CA):** È l'ente terzo fidato che emette e firma digitalmente i certificati. La sua firma garantisce che la chiave pubblica contenuta nel certificato appartenga davvero al soggetto indicato.
* **Certificato Digitale (standard X.509):** È il documento elettronico che funge da "carta d'identità", associando la chiave pubblica all'identità del proprietario.

In pratica, la PKI è il sistema di fiducia che impedisce a un attaccante di spacciarsi per la tua banca fornendoti una chiave pubblica falsa (attacco *Man-in-the-Middle* o *Spoofing*).

