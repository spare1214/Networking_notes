
**1. Cosa si intende per sicurezza nelle comunicazioni di rete?**

1. **Definizione formale** La sicurezza nelle comunicazioni di rete si riferisce all'insieme delle tecniche e delle discipline, come la **crittografia**, volte a garantire i tre pilastri fondamentali: la **segretezza** (confidenzialità), l'**autenticazione** e l'**integrità** dei dati scambiati tra i soggetti comunicanti.
2. **Spiegazione semplificata** Si tratta di assicurare che quando le informazioni viaggiano su una rete, non possano essere lette da terzi, che siamo certi dell'identità di chi invia e riceve, e che il messaggio non sia stato modificato durante il tragitto.
3. **Punti chiave da memorizzare**
   4. Obiettivo primario: proteggere lo scambio di informazioni.
   5. Si basa su tre principi fondamentali: **Segretezza, Integrità, Autenticazione**.
   6. La disciplina portante è la **Crittografia**.
7. **Esempio concreto** L'utilizzo di protocolli come **SSL/TLS** (Secure Socket Layer/Transport Layer Security) in una connessione **HTTPS** incarna la sicurezza di rete, fornendo queste tre funzionalità crittografiche ai protocolli applicativi.
8. **Possibile domanda di approfondimento orale** Quali meccanismi architetturali si utilizzano per garantire l'alta disponibilità (*High Availability*) e la tolleranza ai guasti (*Fault Tolerance*) di un sistema informatico?.

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
