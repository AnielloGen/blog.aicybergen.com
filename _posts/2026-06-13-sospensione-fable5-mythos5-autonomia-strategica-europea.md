---
layout: post
title: "La sospensione di Fable 5 e Mythos 5: un campanello d'allarme per l'autonomia strategica europea"
date: 2026-06-13
categories: [cybersecurity, ai-policy]
description: "L'export control USA che ha sospeso globalmente Claude Fable 5 e Mythos 5 apre una nuova dimensione nel dibattito sull'autonomia strategica europea in materia di cybersecurity e AI."
---

Il 12 giugno 2026, tre giorni dopo il lancio di Claude Fable 5 e Claude Mythos 5 — i modelli più capaci mai rilasciati da Anthropic, con prestazioni cyber descritte come "sostanzialmente superiori" a qualsiasi modello precedente — il governo statunitense ha emesso una direttiva di export control che ha costretto Anthropic a sospendere l'accesso a entrambi i modelli a livello globale, per tutti i clienti, senza una timeline di ripristino.

Per chi segue l'AI Act e la governance europea della cybersecurity, questo episodio merita attenzione non tanto per la disputa tecnica che lo ha innescato, quanto per il precedente che stabilisce e per cosa rivela sulla posizione strategica dell'Europa.

## Cosa è successo

La sequenza dei fatti, ricostruita dalle fonti disponibili:

- Il 9 giugno, Anthropic lancia Fable 5 come primo modello della "classe Mythos" generalmente disponibile, accompagnandolo con un avviso esplicito sui rischi: senza le opportune protezioni, le capacità cyber del modello avrebbero potuto essere impiegate per causare danni seri.
- Un ricercatore indipendente rivendica pubblicamente di aver aggirato i classificatori di sicurezza del modello tramite tecniche di decomposizione multi-agente, sostituzioni Unicode e framing narrativo, arrivando anche a estrarre il system prompt del modello.
- Il 12 giugno alle 17:21 ora della costa orientale USA, il Dipartimento del Commercio statunitense — secondo le ricostruzioni giornalistiche, tramite il Segretario al Commercio — invia ad Anthropic una direttiva che cita autorità di sicurezza nazionale e ordina la sospensione dell'accesso a Fable 5 e Mythos 5 per qualsiasi cittadino straniero, dentro o fuori gli Stati Uniti, inclusi i dipendenti di Anthropic con cittadinanza non statunitense.
- Non potendo applicare la restrizione in modo selettivo in tempo reale, Anthropic disabilita entrambi i modelli per tutti gli utenti, ovunque.
- Anthropic contesta pubblicamente la proporzionalità della misura, sostenendo che l'unica prova fornita finora riguarda un jailbreak ristretto e non universale — essenzialmente la capacità di chiedere al modello di leggere una codebase e correggere difetti software — e che un livello di capacità equivalente è già disponibile in altri modelli, incluso GPT-5.5 di OpenAI.

Gli altri modelli di Anthropic, inclusi Opus 4.8 e Sonnet 4.6, restano operativi e non sono interessati dalla direttiva.

## Perché è un precedente, non un incidente

Le sospensioni di modelli AI non sono una novità in assoluto, ma finora i controlli all'esportazione nel settore AI avevano riguardato hardware (chip), pesi dei modelli o dataset — beni che possono essere fisicamente o tecnicamente controllati alla frontiera. Qui, per la prima volta, un governo ha imposto un controllo all'esportazione sull'accesso a un'API di inferenza di un modello commerciale già distribuito a centinaia di milioni di utenti: non un trasferimento di tecnologia, ma l'uso quotidiano di un servizio cloud.

Tre elementi rendono questo precedente particolarmente significativo:

**Il criterio è la cittadinanza dell'utente, non la sua collocazione.** La direttiva si applica a "qualsiasi cittadino straniero, dentro o fuori gli Stati Uniti". Un'azienda europea che utilizzi questi modelli tramite infrastrutture cloud europee non è, per questo solo fatto, esente da impatti analoghi: ciò che conta è la nazionalità di chi invia la richiesta, non dove risiede il server o l'utente.

**La sospensione è arrivata senza preavviso, senza finestra di appello e senza una classificazione del rischio per livelli.** A differenza del quadro usato per i controlli sui chip — basato su soglie di compute, classificazioni per alleanza, e canali di esenzione per uso civile e accademico — qui non vi è stata alcuna gradualità: una lettera, e l'accesso globale a un prodotto commerciale si è fermato in poche ore.

**Il meccanismo di enforcement ha trasformato un problema di conformità in un problema operativo per chiunque, ovunque.** Anthropic non aveva (e non ha) un modo per applicare la restrizione solo ai cittadini statunitensi che usano il modello da posizioni sensibili: l'unica opzione compatibile con i tempi imposti è stata lo spegnimento totale. Per i clienti europei che avessero costruito processi critici attorno a questi modelli significa che la continuità del servizio dipende da una decisione di politica estera di un paese terzo, presa con un orizzonte di preavviso pari a zero.

## L'impatto economico per le imprese europee

Sul piano pratico, le imprese europee che si affidano a modelli di frontiera per processi di cybersecurity, sviluppo software o ricerca devono ora considerare una variabile che fino a pochi giorni fa era marginale: la cosiddetta *access surface* del modello. Oltre a intelligenza, costo, latenza e finestra di contesto, la domanda diventa: chi può usare questo modello, da quale giurisdizione, e quanto è esposta la continuità del servizio a decisioni che l'azienda cliente non può influenzare né prevedere?

Per un'impresa che avesse pianificato di costruire pipeline di scoperta e remediation delle vulnerabilità attorno a Fable 5, lo scenario concreto è il seguente: un fornitore di servizi essenziali, magari soggetto a obblighi NIS2 di gestione del rischio cyber, si trova da un giorno all'altro privato dello strumento su cui aveva costruito parte della propria postura di sicurezza, senza preavviso e senza un percorso di rimedio chiaro. Il fallback verso modelli di capacità inferiore (Opus 4.8, Sonnet 4.6) è disponibile, ma rappresenta comunque una discontinuità operativa imposta dall'esterno — esattamente il tipo di rischio di continuità che la regolamentazione europea su resilienza digitale (NIS2, Cyber Resilience Act, DORA per il settore finanziario) chiede alle aziende di mappare e mitigare per i propri fornitori critici.

C'è poi un effetto di secondo livello, più strutturale: se l'accesso ai modelli di frontiera può essere sospeso con queste modalità, il vantaggio competitivo che un'azienda europea potrebbe costruire investendo nell'adozione di AI avanzata per la cybersecurity — un'area in cui, come discusso in precedenza, la capacità di scoperta delle vulnerabilità ha fatto un salto di scala — diventa esso stesso un asset non pienamente sotto il proprio controllo. Questo non significa che l'adozione non vada fatta; significa che va fatta con piani di contingenza espliciti.

## Il nodo dell'autonomia strategica

Il dibattito europeo sulla sovranità tecnologica e digitale — di cui fanno parte iniziative come il sostegno a modelli linguistici sviluppati in Europa, gli investimenti in capacità di calcolo e le discussioni su una possibile certificazione europea per i servizi cloud — viene da questo episodio rafforzato su un fronte specifico: la cybersecurity.

Fino a oggi, la dipendenza da fornitori extra-UE per le capacità AI più avanzate era discussa principalmente in termini di conformità regolatoria (l'AI Act impone obblighi ai fornitori di modelli GPAI a rischio sistemico) e di competitività industriale. L'episodio Fable 5/Mythos 5 aggiunge una terza dimensione, quella della continuità operativa in un ambito — la difesa cyber delle infrastrutture critiche — dove un'interruzione improvvisa ha conseguenze che vanno oltre il disagio per un singolo cliente enterprise.

Tre considerazioni per chi guarda a questo tema dal punto di vista delle politiche europee:

**L'autonomia strategica non significa autosufficienza immediata, ma diversificazione e portabilità.** Al momento non è ancora disponibile una soluzione europea che, nel breve termine, possa offrire le capacità di un modello Mythos-class. Pertanto, la lezione operativa è che le architetture di adozione di questi strumenti dovrebbero essere progettate per essere portabili tra più modelli, includendo dove possibile opzioni ospitate o sviluppate in UE come elemento di mitigazione, anche a fronte di capacità inferiori.

**Il tema si interseca direttamente con la cybersecurity delle infrastrutture critiche.** Se la difesa cyber europea finisce per dipendere in modo significativo da strumenti la cui disponibilità può essere alterata da decisioni di un governo terzo, la resilienza digitale del continente — obiettivo dichiarato di NIS2 e del Cyber Resilience Act — acquisisce una dipendenza esterna che i framework attuali non sono pensati per misurare. Vale la pena chiedersi se le valutazioni di rischio sui fornitori critici previste da questi framework dovrebbero includere esplicitamente lo scenario di una sospensione dell'accesso imposta da controlli all'esportazione di un paese terzo.

**La velocità con cui questo è accaduto — 48 ore dal lancio, nessuna finestra di appello — è essa stessa il punto.** Per le imprese europee, pianificare per scenari di questo tipo non è più un esercizio teorico. La domanda da porsi, per chi sta valutando l'adozione di strumenti AI avanzati nei propri processi critici, non è più solo "questo strumento è efficace", ma anche "cosa succede alla nostra operatività se questo strumento smette di essere disponibile da un'ora all'altra, e per quanto tempo".

## In sintesi

L'episodio della sospensione di Fable 5 e Mythos 5 non riguarda, in fondo, la fondatezza tecnica del jailbreak che l'ha innescata — un punto su cui Anthropic e il governo statunitense restano in disaccordo, e su cui non è possibile pronunciarsi senza maggiori dettagli. Riguarda invece il fatto che è ora dimostrato, con un caso concreto, che l'accesso a capacità AI di frontiera per la cybersecurity può essere interrotto globalmente, senza preavviso, sulla base di decisioni di politica estera di un singolo paese. Per l'Europa, che dipende in larga misura da fornitori extra-UE per queste capacità mentre costruisce in parallelo un proprio quadro normativo sulla resilienza digitale, questo è un argomento concreto — non ideologico — a favore di un'autonomia strategica che, sul fronte cybersecurity, significa soprattutto diversificazione dei fornitori, portabilità delle architetture, e investimento in capacità di calcolo e modelli europei.

---

*Per approfondimenti o consulenza sulla conformità all'AI Act e sulla resilienza digitale della tua azienda, scrivici a [info@aicybergen.com](mailto:info@aicybergen.com)*
