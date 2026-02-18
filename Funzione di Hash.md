
## E. Funzioni di Hash

**26. Cos’è una funzione hash?**

1. **Definizione formale** Una funzione hash crittografica è una funzione **unidirezionale** e **irreversibile** che trasforma un input di **lunghezza arbitraria** in un output di **lunghezza fissa**. Questo output viene chiamato **hash** o **digest**.
2. **Spiegazione semplificata** È un meccanismo per creare un'**impronta digitale** unica e compatta di un qualsiasi dato. Non importa quanto sia grande il dato originale, il risultato (il digest) sarà sempre della stessa dimensione. La caratteristica cruciale è che non si può tornare indietro dal digest al dato originale.
3. **Punti chiave da memorizzare**
   4. È **Unidirezionale** e **Irreversibile**.
   5. L'output (Digest) ha **lunghezza fissa**.
   6. Fondamentale per garantire l'**integrità** dei dati.
   7. Esempi: **MD5**, famiglia **SHA**.
8. **Esempio concreto** Durante l'installazione di un software, il file scaricato è spesso accompagnato da un valore **SHA-256**. L'utente può calcolare l'hash del file scaricato e confrontarlo con quello fornito: se i due digest coincidono, il file è integro e non è stato modificato durante il download.
9. **Possibile domanda di approfondimento orale** Qual è il rischio critico legato all'uso di vecchie funzioni come MD5, che ha portato alla loro obsolescenza?.

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

