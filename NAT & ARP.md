

**117. Cos’è NAT?**

1. **Definizione formale** **NAT (Network Address Translation)** è un protocollo implementato nei **router** che traduce l'**indirizzo IP sorgente** di un pacchetto (e talvolta la porta) in un indirizzo IP diverso. È essenziale per permettere ai dispositivi con **indirizzi IP privati** di comunicare con reti esterne (come Internet) che richiedono **indirizzi IP pubblici**.
2. **Spiegazione semplificata** È il traduttore di indirizzi sul tuo router di casa. Quando il tuo PC (che ha un indirizzo privato, es. 192.168.1.10) vuole accedere a Google, il NAT sul router sostituisce quell'indirizzo privato con l'unico indirizzo pubblico della tua casa, permettendo al pacchetto di viaggiare su Internet.
3. **Punti chiave da memorizzare**
   4. Protocollo implementato sui **Router**.
   5. Traduce indirizzi **privati** in indirizzi **pubblici** e viceversa.
   6. Necessario per la comunicazione tra reti con **indirizzi diversi**.
   7. Esistono tre tipi principali: **Statico, Dinamico e Overload (PAT)**.
8. **Esempio concreto** Se l'interfaccia del router è configurata come ip nat inside, si intende che quella porta riceverà indirizzi privati che dovranno essere tradotti prima di uscire (*inside global*).
9. **Possibile domanda di approfondimento orale** Spiega in dettaglio il problema del **masquerading** (molti a uno) nel NAT e come viene risolto dal **PAT**.

**118. Perché si usa NAT?**

1. **Definizione formale** Il NAT viene utilizzato principalmente per due motivi:
   2. **Conservazione degli Indirizzi IP Pubblici:** Permette a più host interni (con IP privati, non instradabili su Internet) di condividere un numero limitato (spesso uno solo) di indirizzi IP pubblici validi.
   3. **Sicurezza:** Maschera l'architettura interna della rete, poiché gli host interni non sono direttamente raggiungibili dall'esterno.
4. **Spiegazione semplificata** Si usa perché non ci sono abbastanza indirizzi IP pubblici per tutti i dispositivi del mondo. Il NAT risolve questo problema permettendo a migliaia di dispositivi privati di utilizzare lo stesso IP pubblico (risparmio) e, in più, offre una prima forma di sicurezza.
5. **Punti chiave da memorizzare**
   6. **Utilizzo efficiente degli indirizzi IP**.
   7. Indispensabile per far uscire gli **IP privati** su Internet.
   8. Rimuove gli **errori di configurazione** degli host (se associato a DHCP).
9. **Esempio concreto** Senza NAT, ogni dispositivo (PC, telefono, tablet) nella tua rete domestica avrebbe bisogno di un indirizzo IP pubblico univoco per navigare.
10. **Possibile domanda di approfondimento orale** Qual è la differenza tra l'uso del NAT nel contesto di IPv4 e la sua necessità in un'architettura IPv6?

**119. Cos’è il NAT Overload / PAT?**

1. **Definizione formale** **NAT Overload**, noto anche come **PAT (Port Address Translation)**, è la forma più comune di NAT. Consente a **più host interni (con IP privati)** di condividere un **singolo indirizzo IP pubblico**. La distinzione tra i vari host privati viene mantenuta tramite l'uso di **diverse porte sorgenti**.
2. **Spiegazione semplificata** È il NAT "molti-a-uno". Quando tre PC escono su Internet usando lo stesso indirizzo IP pubblico del router, il router assegna a ciascuno una porta sorgente diversa (es. PC1 usa porta 1025, PC2 usa porta 1026). Quando il traffico torna indietro, il router guarda la porta di destinazione per sapere a quale PC interno reindirizzare il pacchetto.
3. **Punti chiave da memorizzare**
   4. Permette la condivisione di un **singolo IP pubblico**.
   5. La traduzione avviene basandosi sulla **Porta (PAT)**, oltre all'IP.
   6. Essenziale per la **scalabilità** delle reti domestiche/aziendali.
7. **Esempio concreto** Un client interno usa una porta dinamica (es. 49152). Quando esce, il PAT traduce l'IP privato e la porta dinamica in un unico IP pubblico e una nuova porta, ad esempio, 209.165.200.254:50000.
8. **Possibile domanda di approfondimento orale** Spiega la differenza tra inside local e inside global nel contesto della configurazione NAT.

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
   3. L'IP privato è usato per le comunicazioni **locali**.
   4. L'IP pubblico è necessario per uscire **su Internet**.
   5. La traduzione tra i due avviene tramite **NAT**.
6. **Esempio concreto** Se mandi un pacchetto a un server di Google, il tuo router trasformerà l'indirizzo sorgente da IP privato a IP pubblico. Quando Google risponde, invierà il pacchetto all'IP pubblico (di destinazione).
7. **Possibile domanda di approfondimento orale** Quali sono i *range* di indirizzi IP riservati per l'uso privato (classi A, B, e C)?

**121. Cos’è ARP?**

1. **Definizione formale** **ARP (Address Resolution Protocol)** è un protocollo utilizzato per risolvere un indirizzo di **Livello 3 (IP)** nel suo corrispondente indirizzo di **Livello 2 (MAC Address)** all'interno della stessa rete locale o dominio di *broadcast*.
2. **Spiegazione semplificata** È il protocollo che dice: "Conosco l'indirizzo IP di questo computer (Livello 3), ma per spedire il pacchetto qui sulla LAN, ho bisogno del suo indirizzo fisico (MAC Address, Livello 2)". Ogni host mantiene una **tabella ARP cache** con queste associazioni.
3. **Punti chiave da memorizzare**
   4. Risolve **IP in MAC Address**.
   5. Necessario per le comunicazioni a **Livello 2**.
   6. Avviene all'interno dello stesso **dominio di Broadcast** (LAN/VLAN).
7. **Esempio concreto** Quando un host vuole inviare un pacchetto a un altro host sulla stessa VLAN, prima di creare il *Frame Ethernet* (Livello 2), deve conoscere il MAC Address del destinatario. Se non lo trova in cache, usa ARP.
8. **Possibile domanda di approfondimento orale** Cosa succede se un host deve comunicare con un altro host su una rete diversa? A quale MAC Address indirizza il pacchetto?

**122. Funzionamento di ARP Request.**

1. **Definizione formale** L'**ARP Request** è un messaggio inviato in modalità **Broadcast** sulla rete locale. Contiene l'indirizzo IP del dispositivo di cui si cerca il MAC Address.
2. **Spiegazione semplificata** Il computer che cerca un MAC grida a tutti sulla rete: "Ciao a tutti, chi ha questo indirizzo IP X.X.X.X, per favore mi dica il suo MAC Address?". Poiché è in Broadcast, raggiunge tutti gli host sulla LAN.
3. **Punti chiave da memorizzare**
   4. Messaggio inviato in **Broadcast**.
   5. Contiene l'**IP desiderato**.
   6. Pesa sulla rete in quanto **crea traffico**.
7. **Esempio concreto** Il client manda un Frame con il MAC Address di destinazione settato a FFFF.FFFF.FFFF (MAC di broadcast) e il suo IP. Tutti gli host ricevono la richiesta.
8. **Possibile domanda di approfondimento orale** Spiega in che modo la creazione di **VLAN** riduce l'impatto del traffico ARP sulla rete.

**123. Funzionamento di ARP Reply.**

1. **Definizione formale** L'**ARP Reply** è la risposta inviata in modalità **Unicast** (direttamente all'host richiedente) dal dispositivo che possiede l'indirizzo IP desiderato. Contiene il **MAC Address** risolto, permettendo al mittente di aggiornare la sua tabella **ARP Cache**.
2. **Spiegazione semplificata** Solo il computer che riconosce l'IP richiesto risponde con un messaggio privato dicendo: "Sono io, il mio indirizzo fisico è Y.Y.Y.Y". Il computer richiedente salva immediatamente questa associazione nella sua cache.
3. **Punti chiave da memorizzare**
   4. Risposta inviata in **Unicast**.
   5. Contiene l'associazione **IP-MAC** Address.
   6. L'host mittente aggiorna l'**ARP Cache**.
7. **Esempio concreto** Il computer che ha lanciato l'ARP Request riceve l'ARP Reply e usa il MAC Address appreso per costruire il Frame Ethernet contenente il pacchetto IP, destinato al MAC del ricevente.
8. **Possibile domanda di approfondimento orale** Un attacco **Man-in-the-Middle** può sfruttare l'ARP Reply. In che modo?

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
   3. Il MAC Address ha **valore locale**, l'IP ha **valore generale**.
   4. Il Router interviene sul MAC (Livello 2) per rimetterlo.
   5. **ARP** è il ponte tra i due.
6. **Esempio concreto** Se invii un pacchetto da un PC a un router (che non è sulla tua rete), l'IP di destinazione sarà quello del server remoto, ma il MAC di destinazione del frame di uscita sarà il **MAC del Default Gateway** (l'interfaccia del tuo router).
7. **Possibile domanda di approfondimento orale** Spiega in che modo i due indirizzi (IP e MAC) sono combinati per identificare un processo specifico (*Socket*).
