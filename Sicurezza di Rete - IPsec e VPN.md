
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

---
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

