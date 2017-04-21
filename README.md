# Tesi
Repo per il versioning della mia tesi di laurea


# Mail prof
> Alllllllllllora, la struttura della tesi deve essere "a imbuto", ovvero - lasciando da parte la necessità di dovere scrivere il prologo, un'invenzione dei tempi moderni...
> deve evolvere dal generale al particolare, conducendo il lettore via via a contenuti di maggior dettaglio.
> Quindi, direi debba esserci una introduzione che illustra il contesto IoT così come si sta sviluppando, all'interno di questo le varie classi di applicazioni e tra queste quelle che
> coinvolgono l'elaborazione di immagine, per arrivare al caso del PCN e a descrivere che obiettivi si è prefissato il tuo lavoro.
> Dopo di questo, nella sezione successiva, passi in rassegna il contesto tecnologico di dettaglio (l'obiettivo del PCN, la sua versione attuale, il vantaggio delle telecamere ToF,
> Java, OSGi ecc.). Poi passi a descrivere cosa hai fatto e come lo hai fatto. Infine le conclusioni in cui riassumi il tutto.

TODO: Seguire le istruzioni dettate dal prof e aggiungere quello che pensi sia giusto mettere nella tesi.

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
