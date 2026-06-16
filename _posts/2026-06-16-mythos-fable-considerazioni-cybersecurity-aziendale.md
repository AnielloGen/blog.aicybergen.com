---
layout: post
title: "Alcune considerazioni dopo la vicenda Claude Mythos e Claude Fable: cosa cambia per la cybersecurity aziendale"
date: 2026-06-16
description: "Dopo la sospensione di Fable 5 e Mythos 5, una riflessione su come le aziende possono introdurre la scoperta e la remediation di vulnerabilità assistite dall'AI nei propri processi, tra vincoli normativi e nuovi modelli organizzativi."
---

*Dalla scoperta automatizzata di vulnerabilità alla governance della remediation, nel quadro dell'AI Act europeo*

Ad aprile 2026 Anthropic ha annunciato Claude Mythos, un modello frontier le cui capacità di cybersecurity si sono rivelate sostanzialmente superiori a quelle di qualsiasi modello precedentemente addestrato dall'azienda. A inizio giugno è arrivata la versione di quinta generazione, distribuita secondo un nuovo schema a due livelli: Claude Mythos 5, riservato a un numero ristretto di partner verificati attraverso Project Glasswing, e Claude Fable 5, la versione generalmente disponibile dello stesso modello, dotata di protezioni che limitano l'accesso alle capacità più sensibili. Per le imprese che si occupano di sicurezza informatica questa distinzione non è solo terminologica: definisce due percorsi di adozione molto diversi, con implicazioni dirette su processi, governance e conformità normativa.

Due caratteristiche tecniche, condivise da entrambi i modelli, sono utili per inquadrare quanto segue. La finestra di contesto è la quantità di testo (misurata in token, unità approssimativamente corrispondenti a porzioni di parole) che il modello può "tenere a mente" in una singola conversazione: 1 milione di token, per i modelli Mythos-class, equivale a poter analizzare contemporaneamente un'intera codebase di medie dimensioni — file, dipendenze e relativi riferimenti incrociati — senza perdere il quadro d'insieme. L'adaptive thinking è invece il meccanismo con cui il modello dedica più o meno "ragionamento interno" a un task in base alla sua complessità, in modo automatico e sempre attivo (non può essere disattivato, solo regolato nel livello di sforzo computazionale): per attività come l'analisi di vulnerabilità multi-file, questo significa che il modello impiega più passaggi di ragionamento prima di produrre una risposta, a fronte di un costo computazionale — e quindi economico — maggiore.

## Cosa è successo

Il 12 giugno 2026, tre giorni dopo il lancio, il governo statunitense ha emesso una direttiva di export control che ha portato Anthropic a sospendere a livello globale l'accesso a Fable 5 e Mythos 5 per tutti i clienti, senza una timeline di ripristino.

A monte della direttiva, un ricercatore indipendente aveva rivendicato di aver aggirato i classificatori di sicurezza di Fable 5 tramite una combinazione di tecniche — decomposizione multi-agente, sostituzioni Unicode/omoglifi per evadere i filtri basati su parole chiave, framing narrativo per mascherare richieste sensibili come contenuti creativi — riuscendo anche a estrarre il system prompt del modello. Il governo statunitense ha citato questo presunto jailbreak come motivazione per la direttiva.

In attesa di chiarimenti, Anthropic contesta la motivazione, descrivendo il jailbreak alla base della direttiva come ristretto e non universale; raccomanda nel frattempo il fallback su Opus 4.8 o Sonnet 4.6.

In ogni caso, la vicenda Mythos/Fable, tuttora in corso al momento della stesura di queste note, impone di riflettere su quali debbano essere le evoluzioni della cybersecurity aziendale per utilizzare al meglio le grandi potenzialità dei sistemi di intelligenza artificiale. In questo articolo proviamo a ragionare su quali siano le verifiche preliminari che un'azienda dovrà effettuare, quale possa essere un processo di graduale introduzione, quali adeguamenti andranno apportati ai processi esistenti e quale potrebbe essere una possibile architettura per fare fronte alla crescita dei volumi delle segnalazioni di vulnerabilità.

Va infine sottolineato che l'episodio del blocco dell'accesso a Fable 5 impone che, nella analisi dei rischi, un'azienda che pianifichi l'accesso a modelli con capacità cyber avanzate debba considerare che la disponibilità stessa del modello sottostante può essere soggetta a sospensioni improvvise per ragioni che esulano dal controllo del singolo cliente e dovrebbe quindi progettare l'architettura in modo che sia portabile su modelli alternativi (es. Opus 4.8) senza modifiche sostanziali alla logica applicativa.

## Claude Mythos e Claude Fable: due facce dello stesso modello

Claude Fable 5 e Claude Mythos 5 condividono lo stesso modello sottostante, quello che Anthropic definisce "Mythos-class", con le stesse specifiche tecniche di base: una finestra di contesto di 1 milione di token, fino a 128.000 token di output per richiesta, e un meccanismo di "adaptive thinking" sempre attivo. La differenza non risiede quindi nelle capacità grezze del modello, ma nel livello di protezioni applicate e nel canale di accesso.

**Claude Mythos 5** è la versione con le protezioni rimosse in alcune aree, riservata a partner verificati attraverso Project Glasswing — un'iniziativa che riunisce organizzazioni come AWS, Apple, Google, Microsoft, CrowdStrike, JPMorgan Chase, Linux Foundation e Palo Alto Networks per proteggere il software più critico al mondo. L'accesso è subordinato a un programma di accesso fiduciario, pensato per organizzazioni che si occupano di difesa di infrastrutture critiche o di ricerca biomedica.

**Claude Fable 5** è invece accessibile pubblicamente tramite Claude API, claude.ai e i principali cloud provider. È lo stesso modello, ma avvolto in un sistema di classificatori di sicurezza che, quando rilevano una richiesta relativa a cybersecurity, biologia/chimica o tentativi di distillazione del modello, deviano automaticamente la risposta verso Claude Opus 4.8 — un meccanismo che riguarda meno del 5% delle sessioni.

Per la grande maggioranza delle aziende, la domanda non è "Mythos o Fable", ma se e come integrare Fable 5 (eventualmente affiancato da Claude Security) nei propri processi. I principali driver di scelta riguardano il profilo dell'organizzazione, la finalità d'uso (difesa generale o ricerca avanzata su vulnerabilità), la tolleranza ai falsi positivi dei classificatori, i requisiti di data retention e privacy, e il costo. Un ultimo driver, probabilmente il più importante nella pratica, riguarda la capacità interna di gestire l'output di questi strumenti — un tema su cui torniamo più avanti.

## Capacità di scoperta e impatto delle protezioni

Le capacità cyber dei modelli Mythos-class sono di tutt'altra scala rispetto a quanto visto finora. Nei test pre-rilascio, Mythos Preview ha identificato migliaia di vulnerabilità zero-day precedentemente sconosciute su tutti i principali sistemi operativi e browser, sviluppando exploit funzionanti al primo tentativo in oltre l'83% dei casi. Sul fronte coding, Stripe — tra i primi tester di Fable 5 — ha riportato che il modello ha completato in un giorno una migrazione su una codebase Ruby di 50 milioni di righe, un lavoro che con un team umano avrebbe richiesto oltre due mesi.

Secondo i dati pubblicati da Anthropic, l'impatto delle protezioni sull'utilità pratica del modello è molto limitato per l'uso quotidiano, ma può diventare significativo per i casi d'uso al limite: i classificatori instradano verso Opus 4.8 in media meno del 5% delle sessioni, e un partner esterno ha verificato che le protezioni di Fable 5 contro le query cyber dannose sono le più robuste tra tutti i modelli testati. Per attività difensive realistiche, quindi, le protezioni incidono marginalmente; la vera differenza di capacità tra Fable 5 e Mythos 5 si manifesta sui task più estremi, esattamente quelli per cui Mythos 5 resta riservato a un programma di accesso controllato.

## Dal finding al fix: la remediation come nuovo collo di bottiglia

Anthropic ha reso disponibile Claude Security, uno strumento che scansiona le codebase per individuare vulnerabilità e propone fix per la revisione umana: nelle prime tre settimane dal lancio, è stato utilizzato per correggere oltre 2.100 vulnerabilità. Il dato più rilevante riguarda però l'adozione: meno dell'1% delle vulnerabilità individuate da Mythos nell'ambito di Project Glasswing è stato finora effettivamente corretto. Non è un limite del modello, ma della velocità della pipeline che va dalla disclosure alla remediation effettiva.

Per le aziende il messaggio è chiaro: aumentare la capacità di discovery senza aver prima rafforzato la capacità di remediation produce un backlog crescente di vulnerabilità note ma non risolte — una situazione potenzialmente peggiore, dal punto di vista del rischio e della responsabilità, rispetto a non aver scansionato affatto.

Il flusso di remediation segue tipicamente quattro fasi: rilevamento della vulnerabilità (il modello ragiona sul comportamento del codice seguendo il flusso dei dati tra i file), analisi del contesto e triage (valutazione d'impatto sull'intera codebase), generazione della patch con verifica adversarial (il modello sottopone il proprio risultato a una critica prima di presentarlo), e validazione in sandbox (generazione autonoma di unit test e verifica che la patch non causi regressioni).

## Implicazioni regolatorie nel quadro dell'AI Act

Modelli di classe Mythos rientrano con elevata probabilità nella categoria di modelli GPAI a rischio sistemico prevista dall'AI Act, data la soglia di compute cumulativo (10^25 FLOP) e i considerando che citano esplicitamente le capacità cyber offensive come fattore di rischio sistemico. Gli obblighi per i fornitori includono valutazioni del modello, adversarial testing documentato, tracciamento e segnalazione di incidenti gravi, e condivisione delle valutazioni con l'AI Office. Questi obblighi diventano pienamente applicabili dal 2 agosto 2026, con sanzioni fino al 3% del fatturato annuo globale.

Per le aziende che integrano questi modelli, conta soprattutto l'articolo 53, che impone ai fornitori di GPAI di fornire ai soggetti downstream informazioni su capacità e limitazioni del modello — un punto chiave da verificare contrattualmente.

## Valutare la propria capacità di remediation prima di potenziare la discovery

Prima di introdurre strumenti AI-assisted per la scoperta di vulnerabilità, un'azienda dovrebbe valutare onestamente la propria capacità attuale di gestire i risultati: qual è oggi il tempo medio di remediation per vulnerabilità critiche, esiste già un backlog non risolto, il triage si basa su criteri di exploitability reale o solo su severità tecnica generica? Un approccio incrementale — iniziare su un perimetro limitato, dimensionare il team in base ai risultati osservati, automatizzare il retest, ed estendere solo successivamente la copertura — evita l'effetto, osservato da diversi analisti, di un volume di finding che il processo organizzativo non è in grado di assorbire.

## Integrazione nei processi e modifiche alla governance

Sul piano operativo, l'integrazione richiede discovery potenziata nella pipeline CI/CD, triage automatizzato basato su indicatori di rischio reale (CISA KEV, punteggio EPSS), nuovi SLA di patching (il vecchio standard dei 30 giorni non è più adeguato), estensione delle stesse aspettative a fornitori e supply chain, e un approccio shift-left con SAST e pentesting automatizzato integrati in CI/CD.

Anche la governance di un'azienda deve evolvere per valorizzare al massimo l'introduzione di questi strumenti: verifica della compliance AI Act dei fornitori di modelli, una funzione dedicata di AI Security Governance che faccia da ponte tra security, ingegneria e legale, politiche di accesso esplicite agli strumenti Mythos-class (con attenzione a data retention e GDPR), reporting periodico al vertice aziendale sugli indicatori di processo e coordinamento con i framework normativi esistenti (NIS2, Cyber Resilience Act).

## Una proposta: red/blue teaming con due istanze di modello

Una possibile architettura, pensata per restare interamente entro i limiti dei classificatori commerciali (senza richiedere l'accesso a una versione "senza filtri"), prevede due istanze di modello con ruoli opposti — un Red Agent che analizza il codice e produce un report di vulnerabilità, e un Blue Agent che genera la patch correttiva e i relativi unit test — orchestrate da un arbitro software che gestisce la sandbox e valida i risultati contro la suite di test aziendale, in un ciclo a più round che include anche un contro-attacco del Red Agent sulla patch generata.

Un'architettura di questo tipo deve prevedere anche la protezione contro attacchi ai modelli coinvolti (trattando il codice analizzato come dato non fidato, vista la possibilità di prompt injection nascosta nel codice stesso), e può beneficiare dell'uso di modelli di fornitori diversi per i due ruoli, per evitare che eventuali punti ciechi sistematici di un singolo modello restino non rilevati. Questa eterogeneità consente inoltre di costruire un meccanismo di scoring comparativo tra modelli/fornitori, utile sia per le decisioni di sourcing che per finalità di audit.

## Oltre la sospensione: una trasformazione ormai ineludibile

La sospensione di Fable 5 e Mythos 5 è, con tutta probabilità, una situazione temporanea. Ma indipendentemente da come e quando questo specifico episodio si chiuderà, la tendenza di fondo che lo precede è destinata a restare: l'uso di sistemi di intelligenza artificiale per individuare vulnerabilità del software e proporne la correzione non è più un'opzione sperimentale. Se un'azienda non se ne avvale attraverso i modelli Claude — per scelta o per indisponibilità temporanea — la stessa capacità è e sarà offerta da altri fornitori. Il "dentifricio è uscito dal tubetto": la domanda rilevante non è se questa tecnologia verrà adottata nei processi di sviluppo e manutenzione del software, ma quando, da chi, e con quali garanzie.

Resta quindi cruciale rafforzare la capacità organizzativa di remediation, monitorare i vincoli normativi applicabili (AI Act, NIS2, Cyber Resilience Act, DORA) e introdurre gli interventi organizzativi necessari per gestire questa trasformazione — indipendentemente da quale specifico modello, di quale specifico fornitore, sarà disponibile in un dato momento.
