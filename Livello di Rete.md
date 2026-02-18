## K. Routing e inoltro

**96. Cos’è un router?**

1. **Definizione formale** Un **Router** è un dispositivo di **Livello 3 (Rete)** il cui scopo principale è **instradare (routing)** i pacchetti (PDU di Livello 3) tra reti diverse. Il Router opera leggendo l'**header di Livello 3** (l'indirizzo IP di destinazione).
2. **Spiegazione semplificata** È il dispositivo che decide il percorso migliore per far viaggiare i dati attraverso Internet, che è un insieme di reti. Ogni pacchetto deve sapere dove uscire per raggiungere il *next hop* (passaggio successivo) verso la destinazione finale.
3. **Punti chiave da memorizzare**
   4. Dispositivo di **Livello 3**.
   5. Funzione primaria: **Instradamento (Routing)**.
   6. Prende decisioni basate sull'**indirizzo IP** di destinazione.
   7. Utilizza la **Routing Table** (Tabella di Routing).
8. **Esempio concreto** Il Router, per inoltrare un pacchetto su una rete diversa, distrugge l'header del *Frame* (Livello 2) e ne crea uno nuovo (nuovo MAC di sorgente e destinazione).
9. **Possibile domanda di approfondimento orale** Spiega il ruolo della **NVRAM** e della **RAM** in un router, e cosa contengono in termini di configurazione.

**97. Funzione della routing table.**

1. **Definizione formale** La **Routing Table** è una struttura dati, che risiede nella **RAM** del router, contenente l'elenco delle **reti conosciute** e le istruzioni necessarie per inoltrare i pacchetti verso tali reti, specificando l'**interfaccia di uscita** e l'indirizzo IP del **next hop** (passaggio successivo).
2. **Spiegazione semplificata** È la "mappa" del router. Quando arriva un pacchetto, il router cerca l'indirizzo di rete di destinazione nella tabella. La tabella gli dice, per quella specifica rete, dove deve inviare il pacchetto per il prossimo salto, non necessariamente la destinazione finale.
3. **Punti chiave da memorizzare**
   4. Si trova in **RAM**.
   5. Contiene le reti conosciute (connesse, statiche, dinamiche).
   6. Indica l'indirizzo del **Next Hop**.
7. **Esempio concreto** Se la tabella ha una voce ip route 0.0.0.0 0.0.0.0 <Next Hop/>, questa è una **rotta di default** (*Last Resort*) che viene utilizzata se il router non ha trovato una rotta più specifica per la destinazione.
8. **Possibile domanda di approfondimento orale** Qual è il vantaggio per la **Tolleranza ai Guasti (Fault Tolerance)** di avere più route verso la stessa destinazione all'interno della Tabella di Routing?

**98. Cos’è una route?**

1. **Definizione formale** Una **Route** è una singola voce all'interno della Tabella di Routing che definisce il percorso da seguire per raggiungere una specifica **rete di destinazione** o un host. Essa include l'indirizzo IP della rete, la *Subnet Mask* e l'indirizzo del *Next Hop*.
2. **Spiegazione semplificata** È un'istruzione specifica: "Per arrivare a questa rete (Destinazione), devi passare da questo router (Next Hop)".
3. **Punti chiave da memorizzare**
   4. Voce elementare della **Tabella di Routing**.
   5. Definisce il **percorso** (Next Hop) verso una rete specifica.
   6. Può essere **Statica** o **Dinamica**.
7. **Esempio concreto** Quando un amministratore definisce una rotta statica con il comando ip route 192.168.2.0 255.255.255.0 10.0.0.2, la voce *10.0.0.2* rappresenta il **Next Hop**.
8. **Possibile domanda di approfondimento orale** A cosa serve la **Subnet Mask** nell'identificazione di una route in una rete?

**99. Differenza tra next-hop e destinazione finale.**

1. **Definizione formale** La **Destinazione Finale** è l'indirizzo IP completo della rete o dell'host che il pacchetto deve raggiungere. Il **Next Hop** è l'indirizzo IP dell'**interfaccia del router adiacente** (il salto logico successivo) a cui il pacchetto deve essere inoltrato per proseguire il suo cammino verso la destinazione finale.
2. **Spiegazione semplificata** Il router non deve conoscere tutta la strada (Destinazione Finale), deve solo sapere chi è il **prossimo router** (Next Hop) a cui passare il pacchetto. È come dare un pacco al corriere: non serve sapere tutte le tappe, solo l'indirizzo del prossimo centro di smistamento.
3. **Punti chiave da memorizzare**
   4. Il router conosce solo il **Next Hop**.
   5. Il Next Hop è un **router adiacente**.
   6. La Destinazione Finale è l'obiettivo del pacchetto.
7. **Esempio concreto** Per un pacchetto destinato a Roma (Destinazione Finale), un router a Firenze avrà come Next Hop il router che si trova a Bologna, non direttamente Roma.
8. **Possibile domanda di approfondimento orale** Perché l'uso del **Time To Live (TTL)** è essenziale nei pacchetti IP per evitare che errori di routing (loop) rendano il pacchetto infinito?

**100. Cos’è il routing statico?**

1. **Definizione formale** Il **Routing Statico** è un metodo di instradamento in cui le rotte all'interno della Tabella di Routing sono **inserite manualmente** dall'amministratore di sistema e rimangono fisse, a meno di un intervento manuale.
2. **Spiegazione semplificata** L'amministratore definisce "a mano" ogni percorso. Funziona bene finché la rete non cambia, perché ogni modifica richiede un aggiornamento manuale su ogni router coinvolto.
3. **Punti chiave da memorizzare**
   4. Rotte **definite manualmente** (dal sistemista).
   5. La rotta è **sempre la stessa**.
   6. Ideale per **reti piccole** o per rotte di **default**.
7. **Esempio concreto** Il comando ip route 0.0.0.0 0.0.0.0 1.1.1.1 (Rotta di default) è un esempio di routing statico utilizzato come *Last Resort* (ultima risorsa) quando non c'è una rotta specifica.
8. **Possibile domanda di approfondimento orale** In termini di Distanza Amministrativa, qual è il valore assegnato al routing statico e perché è un valore basso?

**101. Vantaggi e limiti del routing statico.**

1. **Confronto diretto**

|                |                                                                   |                                                                                                                                           |
| -------------- | ----------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------- |
| Caratteristica | Vantaggi (Punti di forza)                                         | Limiti (Debolezze)                                                                                                                        |
| Complessità    | **Facile da configurare** e non genera traffico di aggiornamento. | Non si adatta automaticamente ai **guasti** o ai cambiamenti di topologia.                                                                |
| Sicurezza      | Non richiede lo scambio di informazioni di routing (più sicuro).  | **Assenza di Fault Tolerance**: se l'interfaccia si stacca, la rotta sparisce e il sistema non la rimuove o la rimpiazza automaticamente. |
| Scalabilità    | Minore overhead.                                                  | **Non scalabile**; richiede molto tempo per l'amministrazione in reti grandi.                                                             |

1. **Spiegazione semplificata** Il vantaggio è la semplicità e il minor carico sulla CPU del router. Il limite è l'elasticità: se qualcosa si rompe o cambia, il router continua a credere nella rotta manuale, bloccando il traffico.
2. **Punti chiave da memorizzare**
   3. Vantaggio: Efficienza e **leggerezza** (non genera traffico di routing).
   4. Limite: **Zero dinamicità** o adattabilità ai guasti.
5. **Esempio concreto** In un'azienda con un solo router per l'accesso a Internet, l'unica rotta statica (la rotta di default) è efficiente, ma in una rete con 50 router e più percorsi, diventerebbe ingestibile.
6. **Possibile domanda di approfondimento orale** Perché si usa il routing statico in combinazione con il routing dinamico?

**102. Cos’è il routing dinamico?**

1. **Definizione formale** Il **Routing Dinamico** è un metodo di instradamento in cui i router utilizzano **protocolli dinamici** (**Link State** o **Distance Vector**) e **algoritmi** (Dijkstra o Bellman-Ford) per **scambiarsi informazioni** sulla topologia di rete, decidendo autonomamente la **rotta ottimale** in base a una metrica o un *costo*.
2. **Spiegazione semplificata** I router "parlano" tra loro usando protocolli specifici (come OSPF o RIP) e si scambiano continuamente aggiornamenti sulla mappa della rete. Se una strada si rompe o ne appare una più veloce, i router lo sanno e aggiornano le loro tabelle automaticamente.
3. **Punti chiave da memorizzare**
   4. Si basa su **protocolli** e **algoritmi** (es. RIP, OSPF).
   5. Decide la rotta migliore in base a un **costo/metrica**.
   6. Garantisce la **Tolleranza ai guasti (Fault Tolerance)**.
   7. Crea **traffico di rete** (overhead per gli aggiornamenti).
8. **Esempio concreto** Quando un'interfaccia di rete si disattiva (guasto), i protocolli dinamici come OSPF inviano un **Link State Packet** per informare subito gli altri router, permettendo un ricalcolo rapido del percorso (Fault Tolerance).
9. **Possibile domanda di approfondimento orale** Qual è il nome dato alla metrica utilizzata da **RIP** e come viene calcolata?

## L. Protocolli di routing

**103. Cos’è RIP?**

1. **Definizione formale** **RIP (Routing Information Protocol)** è un protocollo di routing dinamico che appartiene alla categoria **Distance Vector Protocol**. La sua metrica è il **numero di router (Hop Count)** che il pacchetto deve attraversare per raggiungere la destinazione.
2. **Spiegazione semplificata** RIP cerca la strada con il minor numero di salti (router). Ogni router che deve attraversare vale "1". È facile e non tiene conto della qualità della linea (ampiezza di banda o traffico). Ha una **visione locale** della rete.
3. **Punti chiave da memorizzare**
   4. **Distance Vector Protocol**.
   5. Metrica: **Hop Count** (numero di router).
   6. Limite massimo: **15 salti** (adatto solo per reti piccole).
   7. Utilizza l'algoritmo di **Bellman-Ford**.
8. **Esempio concreto** Se ci sono due strade per una destinazione, una con 2 router e l'altra con 5, RIP sceglierà quella con 2 router, anche se la strada con 5 router ha una banda di trasmissione enormemente superiore.
9. **Possibile domanda di approfondimento orale** Perché RIP è considerato obsoleto per le reti moderne?

**104. Cos’è OSPF?**

1. **Definizione formale** **OSPF (Open Shortest Path First)** è un protocollo di routing dinamico che appartiene alla categoria **Link State Protocol**. Sceglie la rotta migliore calcolando un **costo (metrica)** che è inversamente proporzionale all'ampiezza di banda del collegamento.
2. **Spiegazione semplificata** OSPF è il protocollo dinamico moderno. Invia pacchetti informativi (Link State Packet) a tutti gli altri router della sua area (*flooding*), costruendo una **visione globale** della topologia. Usa la banda per determinare la qualità: più banda = costo minore.
3. **Punti chiave da memorizzare**
   4. **Link State Protocol**.
   5. Metrica: **Costo** (calcolato su base **ampiezza di banda**).
   6. Utilizza l'algoritmo di **Dijkstra**.
   7. Ha una **visione globale** della topologia di rete.
8. **Esempio concreto** Il Costo OSPF si calcola con la formula $Costo = \frac{Banda\ di\ riferimento}{Ampiezza\ di\ banda}$. Questo permette di dare un valore basso (migliore) a un collegamento veloce (es. fibra).
9. **Possibile domanda di approfondimento orale** Qual è l'importanza di configurare un'**Interfaccia di Loopback** in OSPF?

**105. Cos’è EIGRP?**

1. **Definizione formale** **EIGRP (Enhanced Interior Gateway Routing Protocol)** è un protocollo di routing dinamico **proprietario di Cisco** e un'evoluzione di IGRP. È considerato un protocollo ibrido avanzato che, oltre all'ampiezza di banda, tiene conto anche del **traffico di rete** e dei **ritardi** (*delays*) per calcolare la metrica.
2. **Spiegazione semplificata** È un protocollo molto sofisticato che non si basa solo sulla velocità teorica della linea (come OSPF), ma anche su quanto è congestionata in quel momento. Il router invia dei pacchetti per misurare i ritardi effettivi (*round-trip time*) e prende la decisione di routing più informata.
3. **Punti chiave da memorizzare**
   4. Protocollo **proprietario Cisco**.
   5. Evoluzione di **IGRP**.
   6. Calcola la metrica tenendo conto di **traffico e ritardi**.
   7. È più complesso da configurare ma è migliore di OSPF in termini di scelta del percorso.
8. **Esempio concreto** EIGRP può preferire un percorso con banda leggermente inferiore rispetto a OSPF, se sa che il percorso più veloce è cronicamente congestionato dal traffico (gestendo il bilanciamento di carico in modo intelligente).
9. **Possibile domanda di approfondimento orale** Nonostante EIGRP sia proprietario, a quale categoria (Distance Vector o Link State) è più vicino dal punto di vista concettuale?

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
   3. **RIP** (Distance Vector) usa **Hop Count** come metrica.
   4. **OSPF** (Link State) usa **Costo/Banda** come metrica.
   5. **Flooding** in Link State garantisce una **convergenza rapida**.
6. **Esempio concreto** Se un collegamento si interrompe, un protocollo Link State lo saprà quasi immediatamente grazie al *flooding* di un LSP, mentre un protocollo Distance Vector potrebbe impiegare molto più tempo (rischio di loop temporanei o ritardi).
7. **Possibile domanda di approfondimento orale** Qual è il vantaggio del *flooding* di un LSP nonostante crei più traffico sulla rete rispetto all'aggiornamento parziale delle tabelle di routing?

**107. Cos’è l’algoritmo di Bellman-Ford?**

1. **Definizione formale** L'algoritmo di **Bellman-Ford** è l'algoritmo matematico utilizzato dai protocolli **Distance Vector** (come RIP) per calcolare i percorsi nella rete. Si basa su una **formula ricorsiva** che calcola la distanza (*distance*) fino a una destinazione aggregando i dati ricevuti dai router vicini.
2. **Spiegazione semplificata** È la logica che permette al router di dire: "Se il mio vicino C mi dice che può raggiungere la rete X in 3 salti, io la raggiungerò in $3+1=4$ salti." La conoscenza si propaga passo dopo passo, in modo ricorsivo.
3. **Punti chiave da memorizzare**
   4. Algoritmo fondamentale per i **Distance Vector** (RIP).
   5. **Ricorsivo** nel calcolo della distanza.
   6. La sua lentezza è la causa del lento **tempo di convergenza** di RIP.
7. **Esempio concreto** Se un router riceve una tabella di routing da un vicino con un percorso a una rete che non conosceva, aggiorna la sua tabella sommando il costo del vicino più uno (o il costo del segmento di connessione).
8. **Possibile domanda di approfondimento orale** Come risolve l'algoritmo di Bellman-Ford il problema dei loop di routing?

**108. Cos’è l’algoritmo di Dijkstra?**

1. **Definizione formale** L'algoritmo di **Dijkstra** è l'algoritmo matematico utilizzato dai protocolli **Link State** (come OSPF). Dopo aver ricevuto i **Link State Packet** (LSP) da tutti i router, questo algoritmo calcola il **percorso più breve (shortest path)** verso tutte le destinazioni, creando un albero di percorso ottimale.
2. **Spiegazione semplificata** È l'algoritmo che, avendo la mappa completa della rete (visione globale), può calcolare con precisione il percorso totale con il costo minimo verso ogni punto.
3. **Punti chiave da memorizzare**
   4. Algoritmo fondamentale per i **Link State** (OSPF).
   5. Richiede una **visione globale** della rete.
   6. Calcola il **percorso ottimale** basandosi sul **costo**.
7. **Esempio concreto** Quando un router OSPF ha finito la fase di *flooding* e ha costruito il database della topologia, lancia l'algoritmo di Dijkstra per generare la sua Tabella di Routing ottimale (utilizzando etichette con costo e nome).
8. **Possibile domanda di approfondimento orale** Perché l'algoritmo di Dijkstra è più veloce in termini di convergenza rispetto a Bellman-Ford?

**109. Cos’è il Hop Count?**

1. **Definizione formale** L'**Hop Count** (Conteggio dei Salti) è la metrica utilizzata dal protocollo **RIP**. Misura il **costo** di una rotta semplicemente contando il **numero di router** che un pacchetto deve attraversare per raggiungere la destinazione.
2. **Spiegazione semplificata** È la misura di distanza più semplice in una rete. Ogni router che si incontra vale 1. Se devo fare un salto, l'Hop Count è 1; se devo fare due salti (passare per due router), l'Hop Count è 2.
3. **Punti chiave da memorizzare**
   4. Metrica specifica del protocollo **RIP**.
   5. Misura il **numero di router** attraversati.
   6. Non tiene conto della **qualità della linea** (banda).
7. **Esempio concreto** In un percorso RIP, un collegamento a 100 Mbps ha lo stesso costo (1 Hop) di un collegamento a 10 Gbps, assumendo che in entrambi i casi ci sia un solo router intermedio.
8. **Possibile domanda di approfondimento orale** Perché l'Hop Count non è una metrica sufficiente per le reti moderne ad alta velocità?

**110. Limite dei 15 hop in RIP.**

1. **Definizione formale** Il protocollo **RIP** impone un limite massimo di **15 Hop Count** per una rotta. Se una destinazione richiede 16 o più salti, viene considerata **irraggiungibile** (*infinity*).
2. **Spiegazione semplificata** È un meccanismo di sicurezza e un limite intrinseco del protocollo. Superare 15 salti significa che la rete è troppo grande per RIP. Questo limite serve anche per prevenire i *loop* (pacchetti che girano all'infinito), limitando il raggio d'azione di RIP.
3. **Punti chiave da memorizzare**
   4. Limite massimo di **15 router**.
   5. Una destinazione a 16 hop è considerata **irraggiungibile**.
   6. Indica che RIP è adatto solo per **reti di piccole dimensioni**.
7. **Esempio concreto** Se una rete aziendale ha 16 router in linea, RIP non sarà in grado di instradare i pacchetti dal primo all'ultimo router; in questo caso si deve usare OSPF o EIGRP.
8. **Possibile domanda di approfondimento orale** Perché i protocolli *Distance Vector* sono più inclini a problemi di loop rispetto ai *Link State Protocol*?

**111. Concetto di cost in OSPF.**

1. **Definizione formale** Il **Costo** in OSPF (detto anche metrica) è il valore numerico assegnato a ciascun collegamento di rete. Esso viene calcolato automaticamente ed è determinato dal rapporto tra una **Banda di Riferimento** (di default 10⁸ Hz) e l'**ampiezza di banda** del collegamento.
2. **Spiegazione semplificata** È la misura di "quanto è faticoso" attraversare una linea. Se la linea è molto veloce (ha alta banda), il costo sarà basso, e OSPF preferirà quel percorso. Se la linea è lenta, il costo sarà alto.
3. **Punti chiave da memorizzare**
   4. Metrica specifica di **OSPF**.
   5. Basato sull'**ampiezza di banda**.
   6. Formula: $Costo = \frac{Banda\ di\ riferimento}{Ampiezza\ di\ banda}$.
   7. Il percorso migliore è quello con il **costo minore**.
8. **Esempio concreto** Un collegamento Ethernet a 100 Mbps avrà un costo inferiore rispetto a un vecchio collegamento a 10 Mbps, e l'algoritmo di Dijkstra sceglierà automaticamente il percorso cumulativo meno costoso.
9. **Possibile domanda di approfondimento orale** L'amministratore può modificare il Costo in OSPF? In che modo e perché dovrebbe farlo?

**112. Cos’è il flooding.**

1. **Definizione formale** Il **Flooding** è la tecnica di diffusione utilizzata dai protocolli **Link State** (come OSPF) per scambiare i **Link State Packet (LSP)**. Consiste nell'**inondare** un'area di rete (tutti i router di una specifica area) con il pacchetto di aggiornamento, in modo che ogni router riceva le informazioni sullo stato dei collegamenti.
2. **Spiegazione semplificata** È una tecnica di propagazione veloce: quando un router rileva una modifica, grida l'informazione a tutti gli altri router della sua zona in modo che tutti aggiornino la mappa in tempo reale.
3. **Punti chiave da memorizzare**
   4. Tecnica di diffusione di **OSPF** (Link State).
   5. Scopo: **inondare** la rete con i **LSP**.
   6. Garantisce una **convergenza rapida**.
   7. Avviene in modalità **Multicast**.
8. **Esempio concreto** Quando un router si accende in un'area OSPF, manda un pacchetto di Link State a un indirizzo **Multicast (Classe D)**, e tutti i router di quell'area lo ricevono e lo inoltrano ai loro vicini che non l'hanno ancora visto.
9. **Possibile domanda di approfondimento orale** Quali informazioni essenziali sono contenute in un **Link State Packet**?

## M. Autonomous Systems e Internet

**113. Cos’è un Autonomous System (AS)?**

1. **Definizione formale** Un **Autonomous System (AS)** è una **collezione di reti amministrate da un'unica autorità** o entità (come un ISP, una grande azienda o un'università), che determina in autonomia le proprie **politiche di instradamento**. Ogni AS è identificato da un numero univoco (un numero di 16 bit).
2. **Spiegazione semplificata** Internet è troppo grande per essere gestita da un unico protocollo. Per questo è divisa in grandi "blocchi" di rete, e ogni blocco (AS) è gestito internamente da un'unica autorità che decide le proprie regole (es. usare OSPF o RIP).
3. **Punti chiave da memorizzare**
   4. Insieme di reti sotto **un'unica autorità**.
   5. Definisce **autonomamente le politiche di routing**.
   6. Identificato da un numero univoco (AS number).
7. **Esempio concreto** Un **Internet Service Provider (ISP)** come Telecom Italia gestisce il proprio Autonomous System e decide come le sue reti interne si instradano.
8. **Possibile domanda di approfondimento orale** Quali sono i vantaggi di suddividere Internet in Autonomous Systems?

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
   3. IGP è per l'**interno** dell'AS.
   4. EGP è per la comunicazione **tra** AS.
   5. Esempi: OSPF è IGP, BGP è EGP.
6. **Esempio concreto** Un pacchetto che viaggia da un ufficio all'altro della stessa azienda (stesso AS) usa un protocollo **IGP** (come OSPF). Se deve andare su un sito esterno (AS diverso) usa un protocollo **EGP** (BGP) per uscire.
7. **Possibile domanda di approfondimento orale** Perché i messaggi BGP (EGP) sono necessariamente più complessi dei messaggi OSPF (IGP)?

**115. Cos’è BGP?**

1. **Definizione formale** **BGP (Border Gateway Protocol)** è il protocollo EGP (Exterior Gateway Protocol) attualmente utilizzato per scambiare informazioni di routing tra diversi **Autonomous Systems (AS)**.
2. **Spiegazione semplificata** È il "linguaggio" usato dai router di confine (*Border Router*) che si collegano alla dorsale Internet. BGP non si preoccupa solo del percorso più breve, ma soprattutto delle **politiche** e degli accordi tra i diversi fornitori di servizi (AS).
3. **Punti chiave da memorizzare**
   4. È un **EGP** (Exterior Gateway Protocol).
   5. Utilizzato per il **routing tra AS**.
   6. Funziona sui **Border Router**.
7. **Esempio concreto** Quando un ISP (che gestisce un AS) si collega a un altro ISP, utilizza BGP per negoziare e pubblicizzare le reti che può raggiungere, stabilendo quali AS sono raggiungibili tramite il suo vicino.
8. **Possibile domanda di approfondimento orale** Qual è la funzione esatta di un **Border Router**?

**116. Funzione dei Border Router.**

1. **Definizione formale** I **Border Router** sono router specializzati situati ai confini di un **Autonomous System (AS)**. La loro funzione è **gestire il routing tra AS diversi** scambiando messaggi **EGP** (come BGP) con i router dei sistemi autonomi vicini.
2. **Spiegazione semplificata** Sono i "doganieri" di ogni zona di rete (AS). Decidono quali dati possono entrare e uscire e, soprattutto, usano protocolli complessi (BGP) per comunicare con il mondo esterno, mantenendo l'ordine all'interno dell'AS e gestendo le relazioni con l'esterno.
3. **Punti chiave da memorizzare**
   4. Router che si trovano ai **confini di un AS**.
   5. Utilizzano protocolli **EGP** (BGP).
   6. Servono per l'interconnessione tra **reti amministrative diverse**.
7. **Esempio concreto** Un Border Router, dopo aver ricevuto un pacchetto destinato a un AS esterno, lo indirizza a un altro Border Router attraverso la dorsale in fibra.
8. **Possibile domanda di approfondimento orale** Qual è la differenza tra un router interno e un Border Router in termini di tabelle di routing gestite?

