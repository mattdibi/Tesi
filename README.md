# Tesi PCN
Repo per il versioning della mia tesi di laurea

Nel seguito ho riportato l'espansione dell'indice dove in ogni sezione ho descritto per sommi capi cosa intendo scrivere.

## Sommario

Breve riassunto della tesi. Esporre:
* Problema considerato
  * PCN
  * Piattaforma per lo sviluppo
* Come il problema è stato risolto
* Principali risultati

### Indice
- Sezione 1: Introduzione
  - Illustrazione del contesto IoT e come si sta sviluppando
  - Classi di applicazioni IoT
  - Applicazioni di Elaborazione di immagini in ambito IoT
  - Applicazione/i PCN 
  - Obiettivi del mio lavoro (migliorare(?) PCN + realizzazione distro custom con Yocto)
  - Struttura della tesi
- Sezione 2: Contesto tecnologico di dettaglio
  - L'obiettivo del PCN
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
    - Ambiente Yocto + Eurotech ReliGate 2025 + OpenCV
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

### Lista delle tabelle
...

### Lista delle figure
...

## Sezione 1: Introduzione
Sezione "imbuto". Andiamo dal generale al particolare. Breve ricerchina sullo stato attuale dell'IoT, storia e sviluppi futuri. Quindi si passa ad analizzare sempre più nel dettaglio l'ambito nel quale si è sviluppata la mia tesi.

##### 1) Contesto IoT
* Spiegazione concetto IoT
  * Definizione Internet of Things
  * Storia dell'IoT
  * Sviluppi futuri dell'IoT

##### 2) Classi di applicazioni IoT
* Spiegazione generale quindi passiamo al dettaglio
  * Domotica
  * Automotive
  * Sistemi Embedded
  * Monitoraggio in ambito industriale
  * Telemetria
  * Elaborazione di immagini
* Applicazioni di Elaborazione di immagini in ambito IoT
  * ...?

##### 3) Passenger Counter
* Applicazione PCN
  * Qual'è la sua funzione
  * ...?
* Obiettivi del mio lavoro
  * Miglioramento del PCN la cui metrica per valutare il miglioramento sarebbe stata: costi, prestazioni ...
  * Realizzazione di una infrastruttura che possa supportare la nuova versione del PCN (immagine Yocto)

##### 4) Struttura della tesi
Qui riporto l'organizzazione del testo della tesi come consigliato dalla guida dell'Università

## Sezione 2: Contesto tencologico di dettaglio
Sezione nella quale passo a descrivere nel dettaglio le tecnologie che ho utilizzato nello svolgimento del mio lavoro.

##### 1) PCN Eurotech
* Obiettivo del PCN
* PCN Eurotech: Descrizione versione corrente del PCN
  * Telecamere a infrarossi
  * Ricostruzione 3D luce strutturata
  * FPGA per ricavare le informazioni di profondità
  * Algoritmo di tracciamento su CPU (Tracciamento dei massimi locali nell'immagine 3D)
TODO: Farsi passare qualche informazione in più dalla Eurotech?

##### 2) Tecnologie usate nella mia versione del PCN
* Telecamere ToF
  * Funzionamento (SR300 e R200) TODO: Rubacchiare immagini dal repo di librealsense
  * Librearia librealsense
  * Vantaggi
* OpenCV
* Yocto
* OSGi(?)

## Sezione 3: Corpo della tesi
Sezione nella quale descrivo cosa ho fatto e come l'ho fatto.
**Nota**: Necessario raccogliere dati sulle performance delle varie versioni per effettuare i vari confronti.

### Blocco 1: Analisi ambienti disponibili per image processing embedded
Qui passo a descrivere l'analisi effettuata per capire quale ambiente di sviluppo fosse il più promettente. Non penso di scrivere molto in questa sezione.

##### 1) Ambiente SDSoC + FPGA + OpenCV + AuvizCV
* Piattaforma Xilinx: Zedboard & Zybo
  * Descrizione dell'hardware
  * Difficoltà riscontrate nel reperire il modulo per l'interfacciamento alla porta HDMI
* SDSoC
  * Descrizione: tool che raggruppa vari tool Xilinx per automatizzare la sintesi di tencologie per FPGA partendo da un alto livello di astrazione
  * Breve descrizione del funzionamento: in pratica è uno script che chiama in sequenza tutti i tool della Xilinx. 
* AuvizCV
  * Cos'è (libreria di codice pre ottimizzato per l'esecuzione su FPGA)
  * Vantaggi (prestazioni)
  * Svantaggi (poche funzioni, poca flessibilità, scarso supporto)

##### 2) Ambiente Yocto + Eurotech ReliGate 20-25 + OpenCV
* Eurotech ReliGate 20-25
  * Descrizione dell'hardware architettura x86 64bit intel 
  * Vantaggi(flessibilità: è una arch x86 facilità di utilizzo) 
  * Svantaggi: prevalentemente le prestazioni
* Yocto
  * Vantaggi (installo le cose che mi servono)
* OpenCV
  * Vantaggi (flessibilità, supporto)

##### 3) Motivazioni per cui è stato infine scelta la seconda opzione 
* Ambiente più completo
* Ambiente più flessibile
* Performance più basse

### Blocco 2: Passenger counters: implementazioni e confronti
Qui passo a descrivere l'effettiva implementazione delle varie versioni dei PCN, confrontandone vantaggi e svantaggi. Inoltre vorrei poter fare dei confronti sulle prestazioni di ogni versione. 

**Nota**: Nel caso della precisione del conteggio è necessario capire se posso definire una metrica e confrontare effettivamente le varie versioni.

##### 1) PCN Eurotech (in breve)
* Problemi principali(quelli già spiegati prima ma più nel dettaglio dal punto di vista tecnico)
  * Difficoltà reperibilità telecamere infrarossi
  * Costi elevati dovuti alla presenza di una FPGA
  * Costi elevati dovuti al fatto che ci dovesse essere una unità di elaborazion per telecamera e quindi per porta
* Soluzioni che si volevano ottenere

##### 2) PCN (versione con sottrazione del background)
* Tecnologie impiegate
  * Webcam
* Spiegazione algoritmo
* Problemi principali
  * Costo computazionale
  * Imprecisione
 
##### 3) RSPCN (versione con telecamere RealSense)
* Tecnologie impiegate
  * Breve spiegazione della struttura del RSPCN
* Spiegazione algoritmo
* Miglioramenti rispetto alle versioni precedenti
  * Precisione
  * Costo computazionale
  * Possibilità di usare più di una telecamera

##### 5) Confronto prestazioni PCN a sottrazione del background vs RSPCN
* Costo computazionale
* Precisione nella rilevazione (metrica?)
* Maggior robustezza rispetto alle condizioni di illuminazione
* Nessun problema di ombre
* Mezzo pubblico in movimento probabilmente potrebbe creare problemi nell'individuazione del background

##### 6) Versioni realizzate
* c++
  * Vantaggi/svantaggi
* java wrap: java realizzato con SWIG
  * Breve excursus sul tool utilizzato (SWIG)
  * Vantaggi/svantaggi rispetto alle altre versioni
  * Difficoltà riscontrate nella realizzazione
* java : versione java con JavaCV e librealsense interfacciate a JavaCPP
  * Breve excursus sul tool utilizzato (Progetto JavaCPP)
  * Difficoltà riscontrate nella realizzazione
  * Vantaggi/svantaggi rispetto alle altre versioni
* osgi(?)

### Blocco 3: Piattaforma Yocto realizzazione e features
Qui passo a descrivere cosa ho fatto per riuscire a realizzare una distro custom Poky che avesse al suo interno tutti i tool che mi servivano per implementare il PCN.

##### 1) Realizzazione della piattaforma
* Risultato finale (immagine stack software)
* Realizzazione
  * Procedimento
* Problemi riscontrati nella realizzazione dell'immagine che volevamo
  * Incompatiblità versioni precedenti con librealsense
  * Necessità di usare il branch Morty quando la ricetta per installare il JDK si trovava molto più avanti nelle versioni.
  * Modifica della ricetta OpenCV

##### 2) Deplyment dell'applicazione all'interno della piattaforma software
* ...?

## Sezione 4: Conclusioni

##### 1) Riassunto di quanto fatto

##### 2) Risultati PCN
* Risultati ottenuti con RSPCN
* Possibili miglioramenti 
  * Implementazione algoritmi di machine learning per il tracciamento più preciso delle persone
  * Scaricare il carico computazionale più intenso sulla GPU
  * Test più approfonditi (i mezzi che ho a disposizione sono limitati)

##### 3) Risultati distro custom Poky
* Risultati ottenuti con Yocto
* Possibili miglioramenti

### Bibliografia

### Appendici
