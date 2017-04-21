# Tesi
Repo per il versioning della mia tesi di laurea

# Mail prof
> Alllllllllllora, la struttura della tesi deve essere "a imbuto", ovvero - lasciando da parte la necessità di dovere scrivere il prologo, un'invenzione dei tempi moderni...
> deve evolvere dal generale al particolare, conducendo il lettore via via a contenuti di maggior dettaglio.
> Quindi, direi debba esserci una introduzione che illustra il contesto IoT così come si sta sviluppando, all'interno di questo le varie classi di applicazioni e tra queste quelle che
> coinvolgono l'elaborazione di immagine, per arrivare al caso del PCN e a descrivere che obiettivi si è prefissato il tuo lavoro.
> Dopo di questo, nella sezione successiva, passi in rassegna il contesto tecnologico di dettaglio (l'obiettivo del PCN, la sua versione attuale, il vantaggio delle telecamere ToF,
> Java, OSGi ecc.). Poi passi a descrivere cosa hai fatto e come lo hai fatto. Infine le conclusioni in cui riassumi il tutto.

### Prototipo indice

- Sezione 1: Introduzione
  - Illustrazione del contesto IoT e come si sta sviluppando
  - Classi di applicazioni IoT
  - Applicazioni di Elaborazione di immagini in ambito IoT
  - Caso del PCN 
  - Obiettivi del mio lavoro (migliorare(?) PCN + realizzazione distro custom con Yocto)
- Sezione 2: Contesto tecnologico di dettaglio
  - L'obiettivo del PCN (cosa fa)
  - La sua versione attuale (PCN Eurotech)
  - Tecnologie/tool utilizzati
    - Descrizione funzionamento e vantaggi delle telecamere ToF
    - OpenCV
    - Yocto
    - Java (?)
    - OSGi (?)
- Sezione 3: Cosa ho fatto e come l'ho fatto
  - Blocco 1: analisi ambienti disponibili per image processing embedded
    - Ambiente SDSoC + FPGA + OpenCV + AuvizCV
    - Ambiente Yocto + Eurotech ReliGate 20-25 + OpenCV
    - Motivazioni per cui è stato infine scelta la seconda opzione
  - Blocco 2: PCNs: implementazioni e confronti
    - PCN Eurotech (in breve)
    - PCN a sottrazione del background
    - PCN con telecamere RealSense
    - Confronto prestazioni delle varie versioni
    - Versioni realizzate (c++, java, java wrap, osgi(?))
  - Blocco 3: Piattaforma Yocto realizzata
    - Risultato finale (immagine stack software)
    - Procedimento realizzazione
    - Problemi riscontrati nella realizzazione dell'immagine 
- Sezione 4: Conclusioni
  - Riassunto
  - Risultati ottenuti
  - Miglioramenti

### TODOs
1. [ ] Scrivere al prof per l'approvazione del prototipo dell'indice
2. [ ] Nel caso di approvazione espandere le sezioni e sottosezioni riassumendo per sommi capi il loro contenuto come fatto qui di seguito
3. [ ] Cominciare a scrivere la tesi

**Nota:** da qui in poi segue l'espansione dell'indice. La versione seguente non è aggiornata rispetto alle ultime direttive dettate dal prof.

# Sommario

Breve riassunto della tesi. Esporre:
* Problema considerato
  * PCN
  * Piattaforma per lo sviluppo
* Come il problema è stato risolto
* Principali risultati

### Indice
...

### Lista delle tabelle
...
### Lista delle figure
...


# Introduzione
Spiegare il fatto che sono stati affrontati due problemi contemporaneamente PCN + sviluppo piattaforma software 
sulla quale far girare il PCN (tramite Yocto)

PCN:
* Spiegazione dei problemi del PCN eurotech che si volevano sistemare
  * Difficoltà nel reperimento delle lenti (telecamera obsoleta)
  * Costo elevato dovuto alla FPGA
  * Costo elevato dovuto al fatto che ci deve essere una unità di elaborazione per telecamera
* Spiegazione di come sono stati sistemati

Piattaforma:
* Spiegazione di cosa la eurotech voleva dalla piattaforma di sviluppo
  * Aumentare appetibilità della piattaforma venduta dalla Eurotech aggiungendo tecnologie
* Spiegare cosa si è riusciti ad ottenere
  * OpenCV con interfacce C++(Nativa) Java e Python
  * Accesso alla libreria RealSense e telecamere
  * JRE e JDK

* Elenco schematico del contenuto dei vari capitoli


# Corpo della tesi

### Blocco 1: analisi ambienti disponibili per image processing embedded

##### 1) Ambiente SDSoC + FPGA + OpenCV + AuvizCV

##### 2) Ambiente Yocto + Eurotech ReliGate 20-25 + OpenCV

##### 3) Motivazioni per cui è stato infine scelta la seconda opzione 
* Ambiente più completo
* Ambiente più flessibile

### Blocco 2: Passenger counters: implementazioni e confronti

##### 1) PCN Eurotech (in breve)
* Tecnologia usata dalla eurotech (algoritmo usato)
  * Telecamere a infrarossi
  * Ricostruzione tramite FPGA
  * Tracciamento dei massimi locali nell'immagine 3D
* Problemi principali(quelli già spiegati prima ma più nel dettaglio dal punto di vista tecnico)
* Soluzioni che si volevano ottenere

##### 2) Breve overview di OpenCV (?)

##### 3) PCN (versione con sottrazione del background)
* Tecnologie impiegate
  * Webcam
* Spiegazione algoritmo
* Problemi principali
  * Costo computazionale
  * Imprecisione
 
##### 4) RSPCN (versione con telecamere RealSense)
* Tecnologie impiegate
  * Telecamere RealSense
    * SR300
    * R200
* Spiegazione algoritmo
* Miglioramenti rispetto alle versioni precedenti

##### 5) Confronto prestazioni PCN vs RSPCN
* Costo computazionale
* Precisione nella rilevazione (metrica?)

##### 6) Versioni realizzate
* cpp
* java(?)
  * wrap java realizzato con SWIG
  * versione java con JavaCV e librealsense interfacciate a JavaCPP
* osgi(?)

### Blocco 3: Piattaforma Yocto realizzazione e features

##### 1) Overview Yocto project
Cos'è cosa fa ecc...

##### 2) Realizzazione della piattaforma
* Risultato finale (immagine stack software)
* Realizzazione
  * Procedimento
  * Ricetta realizzata per inserire tutto (TODO)
* Problemi riscontrati nella realizzazione dell'immagine che volevamo
  * Incompatiblità versioni precedenti con librealsense
  * Modifica della ricetta OpenCV

# Conclusioni

### PCN
* Risultati ottenuti con RSPCN
* Possibili miglioramenti 
  * Implementazione algoritmi di machine learning per il tracciamento più preciso delle persone
  * Scaricare il carico computazionale più intenso sulla GPU
  * Test più approfonditi (i mezzi che ho a disposizione sono limitati)

### Yocto
* Risultati ottenuti con Yocto
* Possibili miglioramenti

### Bibliografia

### Appendici
