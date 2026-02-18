
## B. I Pilastri Infrastrutturali della Sicurezza (HA, FT, DR)

**I. High Availability (HA)**

1. **Definizione tecnica formale** L'**Alta Disponibilità (HA)** è una caratteristica di un sistema volta a garantire un livello concordato di prestazioni operative, solitamente misurato come *uptime* (tempo di attività), eliminando i *Single Point of Failure*. L'obiettivo standard è raggiungere il **99.999%** di *uptime*.
2. **Spiegazione concettuale** HA significa che i componenti critici sono ridondanti e che esistono meccanismi di *failover* automatici in grado di trasferire il carico di lavoro in caso di guasto. L'HA accetta una piccola quantità di *downtime* (fino a 5.26 minuti all'anno).
3. **Obiettivo del modello** Minimizzare il *downtime* e garantire la **continuità del servizio**.
4. **Componenti architetturali** **Ridondanza** dei componenti, meccanismi di **Failure Detection** (rilevamento dei guasti) e **Workload Redirection** (reindirizzamento del carico). Esempi includono l'uso di **Clustering Technologies** e *Load Balancer*.
5. **Flusso logico di funzionamento** In caso di guasto di un componente primario (es. un host), un componente ridondante (es. una VM su un altro host) subentra (*failover*) e gestisce il carico senza intervento umano.
6. **Vantaggi e limiti**
   * **Vantaggi:** Costo inferiore rispetto a FT; minimizzazione delle perdite finanziarie derivanti da interruzioni.
   * **Limiti:** Non garantisce *zero downtime*; c'è un breve periodo di indisponibilità (latenza) durante la fase di *failover*.
7. **Esempio astratto ma concreto** Un **cluster di server applicativi** con due nodi (N1 e N2). N1 è attivo e N2 è in *standby passivo*. Se N1 fallisce, il sistema rileva l'errore e trasferisce il servizio su N2 in pochi secondi, causando un *downtime* minimo.
8. **Domanda di approfondimento tipica di un esame orale** Come si utilizza il protocollo **OSPF** (Link State Protocol) per implementare l'Alta Disponibilità nel routing?

**II. Fault Tolerance (FT)**

1. **Definizione tecnica formale** La **Tolleranza ai Guasti (FT)** è la proprietà che consente a un sistema di **continuare a operare correttamente** anche in presenza di guasti di uno o più dei suoi componenti. FT è una versione più stringente di HA, focalizzata sull'erogazione di **zero downtime**.
2. **Spiegazione concettuale** FT significa che ogni applicazione critica gira contemporaneamente su **due componenti speculari e accoppiati** (mirroring). Se un componente fallisce, l'altro prende il controllo *istantaneamente*, senza alcun ritardo.
3. **Obiettivo del modello** Garantire **zero downtime**.
4. **Componenti architetturali** **Ridondanza stretta** ottenuta tramite l'esecuzione simultanea di un'applicazione su due componenti che si **rispecchiano** (*mirroring*). Tutte le modifiche e gli input sul componente primario sono duplicati sul secondario.
5. **Flusso logico di funzionamento** I carichi di lavoro sono eseguiti in parallelo su entrambi i componenti. In caso di corruzione o guasto del componente primario (es. una VM), il trasferimento del carico al componente secondario (la copia identica) avviene **immediatamente**.
6. **Vantaggi e limiti**
   * **Vantaggi:** **Massima continuità** del servizio (zero downtime), cruciale per applicazioni che non tollerano alcuna interruzione.
   * **Limiti:** Costo molto elevato; può operare a un **livello di prestazione ridotto** durante il guasto, poiché la priorità non è la performance, ma la funzionalità operativa.
7. **Esempio astratto ma concreto** Due server DB identici che eseguono simultaneamente la stessa istanza dell'applicazione (*tightly coupled components*). La memoria, lo stato e il disco vengono replicati in tempo reale (sincronizzazione). Se un disco primario fallisce, il sistema continua a scrivere sul disco secondario **senza che la transazione subisca interruzioni**.
8. **Domanda di approfondimento tipica di un esame orale** In che modo i meccanismi di FT sono legati al concetto di **Integrità** dei dati durante il *failover*?

**III. Disaster Recovery (DR)**

1. **Definizione tecnica formale** Il **Disaster Recovery (DR)** è una strategia complessa che include policy, *tool* e procedure volte al **recupero** o alla **continuazione** delle infrastrutture IT e dei sistemi vitali a seguito di un evento catastrofico (naturale, umano, o cyber-attacco) che rende **intere infrastrutture** indisponibili.
2. **Spiegazione concettuale** DR è un piano di emergenza per disastri su larga scala. Richiede una **sede secondaria (remota)** dove dati e carichi di lavoro possono essere ripristinati. L'obiettivo è riattivare l'operatività critica entro un RTO (*Recovery Time Objective*) concordato, focalizzandosi sul recupero dei dati.
3. **Obiettivo del modello** Recupero dei dati e **ripristino delle operazioni aziendali** dopo un evento distruttivo (catastrofico).
4. **Componenti architetturali** **Sito secondario remoto** (per il *failover* geografico), analisi delle dipendenze, configurazione di soluzioni di **replica dello storage** (*storage replication*) e procedure di **backup** (offline/online).
5. **Flusso logico di funzionamento** A seguito di un disastro che colpisce l'intera sede primaria, i dati critici e i carichi di lavoro vengono ripristinati (o trasferiti) nel sito secondario. Il processo utilizza soluzioni automatizzate di *failover* remoto per raggiungere gli obiettivi di tempo di recupero (RTO).
6. **Vantaggi e limiti**
   * **Vantaggi:** Fornisce resilienza contro **guasti infrastrutturali totali** e disastri che superano le capacità di HA/FT locali.
   * **Limiti:** Generalmente comporta un **RTO più lungo** rispetto a HA/FT, dato che il ripristino avviene su infrastrutture geograficamente distanti.
7. **Esempio astratto ma concreto** Una grande azienda mantiene una replica costante dei database (utilizzando un meccanismo di *storage replication*) in un **datacenter remoto**. Se la sede principale subisce un'interruzione di corrente prolungata, si esegue il *failover* sul sito remoto per riprendere il servizio in un'altra area geografica.
8. **Domanda di approfondimento tipica di un esame orale** In che modo la **Replica dei Dati** (tipica del DR) si differenzia dai meccanismi di **Redundancy** (tipici di HA/FT)?

## C. Confronto e Collegamento dei Concetti

**Confronto diretto (Architetture di Resilienza)**

|  |  |  |  |
| --- | --- | --- | --- |
| Caratteristica | High Availability (HA) | Fault Tolerance (FT) | Disaster Recovery (DR) |
| Obiettivo | Minimizzare il *downtime* (es. 5 minuti all'anno). | Garantire **Zero Downtime**. | Recupero e continuazione del business dopo **evento catastrofico**. |
| Tempo di ripristino | Veloce, con *downtime* minimo (necessita *failover*). | **Istantaneo** (nessun *downtime*). | Dipendente dal RTO (tempo di recupero concordato). |
| Continuità del servizio | Alta, ma con interruzione breve tollerata. | **Massima**, servizio ininterrotto. | Garanzia di ripresa delle operazioni critiche. |
| Tecniche tipiche | Cluster, Failover automatico, Load Balancing, Ridondanza. | Componenti *mirroring* strettamente accoppiati. | Siti remoti, Backup/Restore, Storage Replication. |
| Livello di protezione | Da guasti di singoli componenti/server. | Da guasti di componenti, garantendo la singola transazione. | Da guasti di intere infrastrutture/sedi. |

**Collegamento tra Sicurezza Logica e Infrastrutturale**

La sicurezza non è una sola fase, ma un *continuum* che lega la **protezione dei dati** (crittografia) alla **disponibilità del sistema** (HA/FT/DR).

|  |  |  |
| --- | --- | --- |
| Concetto Infrastrutturale | Ruolo nel Pilastro Logico | Protocolli di Supporto |
| HA/FT/DR | Garantisce la **Disponibilità**. | Routing dinamico (OSPF, RIP, EIGRP) per il *Failover*. |
| Autenticazione | Garantita prima di ogni connessione, anche tra nodi di un *cluster*. | **Certificati X.509** e crittografia asimmetrica. |
| Segretezza | I dati replicati (HA/FT/DR) devono essere cifrati sia *at rest* che *in transit*. | **TLS** (*Handshake*) per lo scambio chiavi. |
| Integrità | I dati sottoposti a *failover* o *restore* (DR) devono essere non alterati. | **Hashing/MAC** (es. TLS *Record Protocol*) per verificare l'assenza di manomissione. |

## D. Soluzioni Tecniche

**🟢 1. High Availability (HA) - Continuità Operativa**

L'obiettivo è minimizzare il *downtime* (punto di riferimento: **99.999%** di uptime) eliminando i **Single Point of Failure** (SPoF).

**Soluzioni Tecniche:**

* **Cluster Activo-Passivo (Failover):** Un nodo primario gestisce il carico, mentre un nodo secondario è in *standby* pronto a subentrare automaticamente in caso di guasto.
* **Load Balancing (Active-Active):** Un **Load Balancer** distribuisce le richieste tra più server attivi contemporaneamente. Se uno fallisce, il traffico viene reindirizzato agli altri senza interruzioni percepibili.
* **Ridondanza di Rete:** Utilizzo di protocolli di routing dinamico come **OSPF** o **EIGRP** per ricalcolare istantaneamente i percorsi in caso di interruzione di un link.
* **Virtualizzazione:** Utilizzo di funzionalità come *vSphere HA* per riavviare automaticamente le macchine virtuali su un altro host fisico se quello originale si guasta.

**🟡 2. Fault Tolerance (FT) - Tolleranza ai Guasti Estrema**

A differenza dell'HA, la FT punta a **zero downtime** e **zero perdita di dati**, anche durante il passaggio tra i nodi.

**Soluzioni Tecniche:**

* **Hardware Mirroring (Tightly Coupled):** Due sistemi identici eseguono le stesse istruzioni in parallelo.
* **Sincronizzazione della Memoria e dello Stato:** Ogni operazione di scrittura o modifica in RAM viene replicata istantaneamente sul nodo secondario.
* **RAID (Redundant Array of Independent Disks):** Implementazione di RAID 1 (Mirroring) o RAID 5/6 a livello di storage per evitare che il guasto di un disco blocchi il sistema.
* **Costi e Limiti:** È una soluzione molto costosa e complessa, riservata solo a transazioni critiche (es. sistemi bancari o medici).

**🔴 3. Disaster Recovery (DR) - Recupero Catastrofale**

Strategia per ripristinare i sistemi a seguito di un evento che rende indisponibile l'intera infrastruttura primaria (incendi, alluvioni, attacchi hacker massivi).

**Soluzioni Tecniche:**

* **Sito Secondario Remoto:** Una sede geograficamente distante dove replicare i dati.
* **Storage Replication:** Replica costante dei database e dei file system tra il sito primario e quello di DR (replica sincrona o asincrona).
* **Backup Strategici:**
  + **Backup Online:** Copie veloci su dischi o cloud.
  + **Backup Offline:** Copie su supporti fisici scollegati dalla rete per protezione contro i ransomware.
* **Metriche Fondamentali da citare nello scritto:**
  + **RTO (Recovery Time Objective):** Il tempo massimo necessario per tornare operativi.
  + **RPO (Recovery Point Objective):** La massima quantità di dati che l'azienda può permettersi di perdere (misurata in tempo, es. "perdiamo al massimo gli ultimi 15 minuti di dati").

**📑 Tabella di Sintesi per la Prova Scritta**

In una traccia d'esame, potresti dover confrontare queste architetture:

|  |  |  |  |
| --- | --- | --- | --- |
| Caratteristica | High Availability (HA) | Fault Tolerance (FT) | Disaster Recovery (DR) |
| Obiettivo | Ridurre il downtime | Zero downtime | Ripristino post-catastrofe |
| Downtime ammesso | Pochi minuti/anno | Nessuno | Dipende dal RTO concordato |
| Costo | Moderato | Molto Elevato | Variabile (alto per infrastruttura) |
| Tecnica Chiave | Cluster & Load Balancing | Mirroring sincrono | Replica geografica & Backup |

---
**Sicurezza Infrastrutturale e Fault Tolerance Hardware**

**Spiegazione Concettuale** La sicurezza include la **Disponibilità** (Availability). Esistono diversi livelli di protezione contro i guasti hardware.

* **HA (High Availability):** Minimizza il downtime. Se un nodo cade, il servizio viene riavviato su un altro nodo. C'è una breve interruzione.
* **FT (Fault Tolerance):** Garantisce **Zero Downtime**. Il sistema continua a operare senza interruzioni anche in caso di guasto.

**Il Concetto di Lockstep e FT Hardware** La vera Fault Tolerance si basa sul principio di **Lockstep** (o funzionamento in sincrono).

* **Sincronizzazione Continua:** Due componenti hardware (o VM) eseguono le *stesse istruzioni* nello *stesso momento*.
* **Ridondanza Hardware:** Piattaforme come *ftServer* utilizzano hardware completamente ridondato (CPU, memoria, I/O) impacchettato come un sistema unico. Se un componente si rompe, il gemello continua l'elaborazione senza perdere nemmeno un ciclo di clock o una transazione in memoria.

👉 **Collegamento alla Sicurezza:** La FT Hardware protegge l'**Integrità** dei dati "in-flight" (in memoria/processo) e garantisce la **Business Continuity** per applicazioni critiche dove il riavvio (HA) non è accettabile.

1. **Analisi delle Minacce e Resilienza**

**Spiegazione Concettuale** La sicurezza non parte dalla tecnologia, ma dall'analisi del rischio. Le minacce si classificano in base all'origine:

1. **Naturali:** Eventi fuori dal controllo umano (terremoti, alluvioni, incendi). Richiedono strategie di *Disaster Recovery* (siti remoti).
2. **Umane Volontarie:** Attacchi mirati dall'esterno (Hacker, Malware) o dall'interno (dipendenti infedeli, sabotaggio).
3. **Umane Involontarie:** Errori, imperizia, inesperienza o distrazione degli utenti o degli amministratori (es. cancellazione accidentale dati).
4. **Infrastrutturali:** Guasti Hardware, Bug Software, o architetture mal progettate (Single Point of Failure).

**Dal Rischio alla Continuità** L'analisi di queste minacce definisce le metriche **RTO** (tempo massimo offline) e **RPO** (massima perdita dati).

* Se il rischio è il guasto hardware $\rightarrow$ Soluzione: **HA/FT** (Cluster).
* Se il rischio è la catastrofe naturale $\rightarrow$ Soluzione: **Disaster Recovery** (Replica geografica).
* Se il rischio è l'errore umano/ransomware $\rightarrow$ Soluzione: **Backup** (Offline/Immutable).

👉 **Collegamento alla Sicurezza:** Un sistema sicuro deve prevedere il fallimento. La **Resilienza** è la capacità dell'architettura di assorbire questi eventi (minacce) e mantenere il servizio attivo (Business Continuity).
