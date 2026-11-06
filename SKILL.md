---
name: privacy-cookie-audit
description: "Esegue audit di compliance GDPR, privacy, cookie e normativa italiana/UE applicabile ai trattamenti di un sito: verifiche tecniche, documentali e organizzative, matrice degli obblighi, rilievi e rimedi. Usare per valutare conformità e lacune da URL e documenti del titolare; non è una certificazione legale né un audit SEO."
---

# Audit di compliance GDPR, privacy e cookie dei siti

Fornisci evidenze riproducibili e correzioni proporzionate. Parti dall'URL; il sorgente e l'accesso server sono facoltativi. Default: contesto Italia/UE, dichiarato come ipotesi se non confermato. Rispondi nella lingua dell'utente.

## Perimetro normativo e organizzativo

Per ogni audit leggi [matrice di compliance](references/compliance-matrix.md). Valuta i trattamenti collegati al sito, non soltanto banner e informative. Identifica territorio, ruolo del gestore, destinatari del servizio, funzioni e categorie di dati; dichiara le ipotesi. Applica GDPR, Codice Privacy e disciplina ePrivacy pertinente, oltre a provvedimenti e regole settoriali effettivamente applicabili. Altri ambiti normativi del sito (es. commercio elettronico, consumatori, accessibilità) richiedono una verifica di applicabilità e un perimetro esplicito: non dichiarare una compliance normativa universale.

L'audit comprende due livelli: verifiche pubbliche tecniche/documentali e verifiche organizzative basate su evidenze del titolare. Avvia subito il primo e chiedi durante il lavoro solo documenti o chiarimenti mirati necessari al secondo. L'assenza di documentazione pubblica non prova l'assenza di un adempimento interno. Se mancano prove sostanziali, consegna un audit preliminare con lacune aperte, non un verdetto di conformità complessiva.

Associa ogni requisito a fonte/articolo, motivo di applicabilità, evidenza, stato e azione correttiva. Distingui requisiti soddisfatti nel perimetro verificato, non conformità documentate, conformità parziale, non verificati, non applicabili e interpretazioni da confermare. Gli score della rubrica web sono indicatori accessori: non sostituiscono la matrice normativa e non diventano percentuali di compliance GDPR.

## Perimetro ed evidenze

- Registra data, URL effettivi dopo redirect, ambiente, browser, stato iniziale del consenso, localizzazione nota e limiti di accesso. Confronta le informative con la pagina corrente: risultati indicizzati o cache possono mostrare versioni superate. In caso di divergenza conserva provenienza e data e fonda i rilievi sul documento live verificato. Non presentare un campione come scansione completa.
- Visita homepage, pagina contatti e pagine con mappe, video, form, chat o altri widget, oltre a privacy/cookie policy e preferenze. Scegli percorsi rappresentativi, senza acquistare, inviare form o usare account personali.
- Preferisci un contesto browser isolato, se gli strumenti lo consentono. Non cancellare cookie o preferenze del profilo dell'utente. Se manca isolamento, dichiara la contaminazione da consensi preesistenti; non certificare il comportamento della prima visita.
- Usa strumenti browser con rete/storage quando disponibili e permessi. La sola lettura HTML o navigazione visiva consente un audit preliminare, non dimostra l'assenza di tracciamenti. Non fingere di vedere header, cookie HttpOnly, iframe cross-origin o storage che lo strumento non espone. Non richiedere accessi aggiuntivi finché puoi avanzare utilmente.
- Raccogli nomi, domini, durata, attributi dei cookie e nomi delle chiavi storage, evitando valori identificativi, token e dati personali. Nei report sanitizza query string, header e screenshot; non archiviare HAR grezzi senza necessità e redazione.

## Scelta degli strumenti

Prima di dichiarare una verifica impossibile, controlla browser collegati e capacità effettive. Se il browser integrato non espone rete o storage, valuta Chrome con DevTools tramite gli strumenti di computer use autorizzati. L'assenza di Playwright installato non esclude questa possibilità; un 403 ricevuto da uno script HTTP non dimostra che il sito sia inaccessibile dal browser.

Per verifiche con Chrome, sessioni isolate o script leggi [verifica browser e cookie](references/browser-verification.md). Usa questo percorso per raccogliere prove tecniche prima di aggiornare score e copertura. Distingui sempre disponibilità dello strumento, azione tentata e risultato effettivamente verificato.

## Ricognizione privacy del sito

Negli esempi pubblici usa soltanto domini riservati come `example.com`, `example.org` o `example.net` e dati sintetici. Sono segnaposto illustrativi, non siti già sottoposti ad audit. Non includere nomi di clienti, progetti reali, report privati o evidenze identificative negli esempi riutilizzabili.

Leggi [criteri e score](references/audit-rubric.md) per ogni audit completo. Parti dal dominio fornito, per esempio `https://example.com`, senza sostituirlo tacitamente con un dominio simile. Registra redirect e identità del sito; se il dominio non risponde, segnala il limite e verifica eventuali alternative come ipotesi.

Cerca link nel footer, header, menu e vicino ai punti di raccolta: privacy policy, cookie policy, trattamento dati, termini, gestione preferenze e contatti privacy. Se mancano, cerca nel sito e nella sitemap pubblica, eventualmente con ricerca `site:dominio`; non inventare URL o concludere assenza da una sola pagina. La policy può essere integrata in un unico documento: l'assenza di una pagina chiamata cookie-policy non è automaticamente una violazione.

Inventaria ogni tipo di raccolta presente nel campione: contatto, preventivo, newsletter, prenotazione, registrazione/login, checkout, candidatura/upload, ricerca interna, chat, WhatsApp e widget di terzi. Per ogni form registra pagina, finalità, campi obbligatori/facoltativi, destinatario tecnico visibile, link informativa e controlli di consenso. Osserva senza inviare dati: comportamento backend, validazione effettiva e retention restano non verificati senza ambiente di test e autorizzazione.

Controlla se i campi sono proporzionati alla finalità dichiarata, se la policy è accessibile prima della raccolta e se marketing/profilazione sono separati dalla richiesta principale, facoltativi e non preselezionati. Non imporre automaticamente una checkbox «accetto la privacy» a ogni form: informativa, presa visione e consenso sono concetti distinti, e rispondere a una richiesta può avere una base diversa dal consenso. Non considerare la sola presenza della checkbox prova di conformità. Verifica anche CAPTCHA, anti-spam, upload e servizi di invio esterni osservabili.

Confronta quanto dichiarato con quanto osservato: identità del titolare, contatti, finalità e basi giuridiche per ciascun trattamento, categorie di destinatari, conservazione o criteri, trasferimenti/garanzie quando applicabili, diritti e reclamo al Garante, eventuale DPO quando richiesto. Non inventare obblighi come la nomina universale del DPO, un termine fisso per tutti i log o il consenso universale per ogni dato personale. Le dichiarazioni documentali sono osservabili; la loro attuazione interna richiede prove diverse.

## Normativa specifica dei moduli e dei flussi

Per ogni modulo o raccolta dati descrivi cosa ottiene l’utente, quali dati vengono raccolti, chi li riceve e cosa succede dopo. Distingui contatto/preventivo, prenotazione, ordine, pagamento, registrazione e marketing: una prenotazione non va classificata automaticamente come acquisto concluso. Verifica l’intero flusso pertinente nei limiti del mandato, non soltanto la checkbox privacy.

Oltre agli obblighi privacy, fai lo screening delle disposizioni pertinenti alla funzione concreta: per esempio disciplina di servizi online, consumatori, contratti a distanza, pagamenti, accessibilità o regole settoriali quando applicabili. Consulta fonti ufficiali aggiornate e motiva per ciascuna inclusione o esclusione; non estendere l’audit all’intera attività del gestore. Un sito di prenotazione per una pizzeria è un esempio di funzione da classificare, non un motivo per applicare indiscriminatamente ogni norma del settore alimentare. Se emergono campi potenzialmente delicati, come informazioni sanitarie, valuta finalità, necessità e disciplina specifica senza dedurre la categoria dal solo titolo del sito.

Quando una funzione, destinazione dei dati, finalità o condizione giuridicamente rilevante rimane dubbia dopo l’ispezione disponibile, chiedi sempre un chiarimento mirato all’utente durante l’audit. Spiega quale conclusione dipende dalla risposta; non inventare il funzionamento e non limitarti a un generico «da verificare» nella consegna. Riusa le risposte già fornite. Continua il lavoro indipendente; se manca una risposta indispensabile, lascia aperto il punto e non formulare prescrizioni dipendenti. Non reiterare una domanda già dichiarata non risolvibile dall’utente: registra il limite e la prova necessaria.

## Verifica comportamentale

Con sessioni indipendenti, quando possibili, verifica:
1. Prima interazione: richieste di rete, script, iframe, Set-Cookie e storage. Aspetta caricamenti differiti e scorri fino ai widget: lazy loading non equivale al consenso.
2. Rifiuto o chiusura: verifica quali richieste/storage persistono, anche dopo ricaricamento e navigazione interna.
3. Accettazione e scelte granulari: controlla le differenze effettive, non solo lo stato grafico dei pulsanti.
4. Revoca: verifica accessibilità del comando e arresto dei trattamenti futuri soggetti al consenso. Non promettere cancellazione di dati già inviati a terzi.
5. Persistenza: verifica che la scelta venga ricordata e che il banner non ricompaia impropriamente. Non alterare l'orologio di sistema per simulare scadenze.

Per ogni caso registra URL, azioni, risultato, prova e limiti. Se un caso non è eseguibile, segnalalo come non verificato. Non interpretare blocchi pubblicitari, errori di rete o protezioni del browser come prova che il sito blocchi correttamente i tracker.

## Interpretazione

- Separa cookie/storage tecnici, analytics eventualmente assimilabili ai tecnici, profilazione, altri strumenti di tracciamento, richieste esterne e log server. Il nome del fornitore o del cookie da solo non dimostra finalità o esenzione.
- Search Console verificata tramite DNS/meta tag non equivale a Google Analytics. Tag Manager è un contenitore: analizza i tag realmente eseguiti. Consent Mode o richieste senza cookie non dimostrano da soli assenza di trattamento o conformità.
- Una richiesta esterna trasmette dati tecnici ma non implica automaticamente profilazione o obbligo di banner. OpenStreetMap non è automaticamente esente: verifica lo specifico embed/provider, senza attribuirgli tutti i trattamenti citati in una policy generale.
- Log tecnici non implicano di per sé consenso cookie. La navigazione non consente di verificare conservazione, accessi amministrativi, backup, accordi con fornitori o configurazione server: richiedi evidenze mirate solo se necessarie al mandato.
- Non prescrivere un banner a ogni sito. Un banner privo di blocco preventivo non risolve il problema. Un pulsante per caricare una mappa riduce contatti automatici ma non è automaticamente un consenso valido per qualsiasi trattamento.
- Confronta le evidenze con le dichiarazioni: titolare e contatti, finalità, basi giuridiche dichiarate, fornitori, trasferimenti, conservazione, diritti, cookie effettivi e revoca. Segnala affermazioni assolute non provate, senza inventare cookie o tempi di conservazione.

## Chiarimenti durante l'audit e completezza

Non rimandare tutte le incertezze alle raccomandazioni finali. Appena una lacuna può cambiare la valutazione del consenso, l'applicabilità di un controllo o la gravità di un rilievo, cerca prima prove pubbliche e poi poni domande mirate al titolare, se le informazioni non sono altrimenti disponibili. Segui il [percorso dei chiarimenti](references/browser-verification.md#chiarimenti-e-chiusura-delle-incertezze). Continua nel frattempo le verifiche indipendenti; non trattare silenzio o tempo trascorso come conferma.

Prima della consegna verifica che ogni controllo della rubrica abbia stato, evidenza e motivazione, e che ogni incertezza rilevante abbia una risposta o una domanda esplicita ancora aperta. Distingui completezza della ricognizione da verifica positiva: non promettere completezza tecnica o legale con prove mancanti e non trasformare dichiarazioni del titolare in configurazioni verificate.

## Valutazione della necessità del consenso

L'audit deve formulare una conclusione motivata per ciascun servizio effettivamente rilevato, non limitarsi a dire che il consenso dipende dai trattamenti. Segui la [valutazione per servizio](references/browser-verification.md#valutazione-per-servizio-e-necessità-del-consenso): confronta esecuzione osservata, finalità e configurazione con fonti ufficiali. Riporta nel risultato servizio, prova, necessità del consenso (richiesto, esenzione motivata o da accertare), motivazione, fonte e comportamento prima della scelta. Distingui consenso per strumenti sul dispositivo e base giuridica GDPR; non dedurre esenzione dall'assenza di cookie o dalla sola dichiarazione commerciale del fornitore.

## Fonti aggiornate

Prima di conclusioni normative consulta fonti primarie correnti e cita i passaggi pertinenti:
- https://www.garanteprivacy.it/faq/cookie (in particolare FAQ 4–6, 9–12 e 15).
- Linee guida cookie e altri strumenti di tracciamento del 10 giugno 2021, raggiungibili dalle FAQ; controlla eventuali aggiornamenti.
- [GDPR](https://eur-lex.europa.eu/eli/reg/2016/679/oj): verifica testo vigente, articoli applicabili e orientamenti EDPB pertinenti.
- [Codice Privacy](https://www.garanteprivacy.it/codice) e normativa ePrivacy nelle fonti ufficiali: verifica testo vigente e applicabilità, inclusi art. 122 per il terminale e art. 130 per comunicazioni promozionali quando pertinenti.
- Documentazione e informative ufficiali degli specifici fornitori rilevati, privilegiando gli addendum del prodotto sulla sola policy generale. Distingui eventuali ruoli diversi del fornitore per erogazione e miglioramento del servizio, senza estendere a tutto il prodotto una singola finalità.

Distingui obbligo documentato, interpretazione da confermare e miglioramento facoltativo. Se le fonti non sono accessibili, dichiara che la parte normativa non è stata aggiornata. Un audit tecnico non è una certificazione legale.

### Esempio istituzionale di informativa

L’[informativa dei siti del Garante](https://www.garanteprivacy.it/home/docweb/-/docweb-display/docweb/36573) è utile per confrontare struttura e chiarezza. Non è un modello universale o una fonte di obblighi aggiuntivi: non trasferire automaticamente basi giuridiche istituzionali, sette giorni di conservazione dei dati di navigazione, fornitori o dichiarazioni sui cookie ad altri titolari.

## Risultato e monitoraggio

Apri con esito di compliance circoscritto e limite principale. Consegna la matrice normativa, i documenti mancanti e un piano di rimedio con priorità, ruolo responsabile suggerito e criterio di verifica; non inventare scadenze legali. Separa evidenza tecnica, dichiarazione del titolare e valutazione normativa.  Per i rilievi usa: priorità, pagina/stato, evidenza, impatto, correzione suggerita e verifica di chiusura. Classifica ogni conclusione come osservata, inferita o non verificata. Calcola gli score tecnici per categoria secondo references/audit-rubric.md, con copertura, non verificati e non applicabili espliciti. Non presentarli come percentuale di conformità legale. Non dichiarare un sito conforme solo perché non rilevi cookie.

### Sintesi leggibile e azioni con priorità

Apri ogni report con una sintesi comprensibile anche a chi non è tecnico: «Cosa va bene», «Cosa devi correggere», «Cosa dobbiamo verificare», «Cosa ti consiglio». Spiega ogni problema attraverso conseguenza pratica e prossima azione; sposta dettagli tecnici, identificatori dei controlli e formule negli approfondimenti. Espandi le sigle alla prima occorrenza. Mantieni una lista operativa ordinata per priorità dopo i rilievi e prima dell’appendice finale dei punteggi. Collega ogni azione al rilievo o controllo pertinente; evita raccomandazioni generiche non sostenute dal campione.

Usa queste priorità operative, distinte dagli stati di conformità e dalle scadenze di legge:
- **P0 — intervento immediato:** esposizione attiva di dati/credenziali o altro danno grave in corso dimostrato. Indica contenimento e verifica successiva; non assegnare P0 a un semplice dubbio.
- **P1 — alta:** difetto documentato con impatto rilevante o verifica necessaria per decidere su un trattamento già attivo potenzialmente rilevante. Nel secondo caso scrivi esplicitamente «verifica prioritaria» e spiega cosa può cambiare con l'esito.
- **P2 — media:** correzioni documentali, coerenza dei flussi e processi da completare, con impatto più circoscritto nel campione.
- **P3 — miglioramento:** interventi facoltativi di chiarezza o manutenzione, senza presentarli come obblighi.

Per ogni voce riporta: **priorità | natura (obbligo accertato/obbligo condizionato/verifica da completare/consiglio facoltativo) | azione concreta | motivo ed evidenza | ruolo responsabile suggerito | dipendenze o informazioni necessarie | criterio di chiusura**. Se serve distinguere l'ordine entro la stessa priorità, considera impatto, diffusione e dipendenze; le verifiche che sbloccano altre decisioni precedono le modifiche dipendenti. Non prescrivere consenso, banner, cancellazioni o modifiche dei trattamenti prima di averne motivato la necessità. Se suggerisci tempi operativi, etichettali come proposte; cita la fonte per eventuali termini legali realmente applicabili. Non inventare responsabili nominativi o promettere esecuzioni non autorizzate.

Per «obbligo accertato» cita requisito applicabile e difetto dimostrato. Per «obbligo condizionato» indica la condizione che lo fa scattare e la prova mancante. Priorità e natura sono indipendenti: un dubbio urgente non diventa una violazione.

Se non emergono difetti, indica comunque le verifiche residue oppure dichiara che non risultano azioni correttive nel perimetro esaminato. Non aggiungere problemi fittizi per riempire la lista.

### Tabella normativa a semaforo

Dopo la sintesi presenta una tabella leggibile: **norma/articolo e requisito concreto | stato testuale e colore | motivo/prova | obbligo o consiglio e prossima azione**. Suddividi le norme ampie per requisito: non dichiarare verde l’intero GDPR perché è presente una privacy policy.

- **🟢 Verde — rispettato nel perimetro verificato:** prova sufficiente per il requisito specifico. Un miglioramento facoltativo va in nota e non cambia il verde.
- **🟡 Giallo — verifica/adeguatezza da completare:** dubbio concreto su prove, applicabilità o funzionamento che impedisce una conclusione. Indica domanda, informazione mancante e conseguenza possibile; non equivale a violazione accertata.
- **🔴 Rosso — obbligo non rispettato:** requisito applicabile e inosservanza sostenuti da prove, anche se il rimedio è piccolo. Distingui gravità e priorità dal colore.

Per obblighi non applicabili scrivi **NA — non applicabile** con motivo, senza verde premiale. Non basare il colore sul numero di parole mancanti o sulla previsione di una sanzione: verifica significato, completezza e accessibilità richiesti dalla norma. Una formulazione diversa ma equivalente può essere verde; un’omissione obbligatoria non diventa verde perché sembra lieve. Non promettere «non punibile». Mantieni colori, stati normativi e motivazioni coerenti; lo score parziale non deve nascondere un rosso.

### Istruzioni finali di correzione, utilizzabili da uno sviluppatore o da un’IA

Dopo il piano prioritario e prima dell’appendice dei punteggi aggiungi istruzioni operative per ciascuna correzione: **ID del rilievo e natura | pagina/componente o file se effettivamente noto | risultato atteso | intervento concreto | informazioni necessarie | verifica di accettazione**. Specifica anche quando attendere un chiarimento anziché inventare una scelta giuridica. Non inventare percorsi del repository da un URL né documenti, tempi di conservazione, ruoli, accordi o garanzie dei fornitori. Se proponi testi, distingui bozza suggerita e contenuti da confermare. Per modifiche al modulo considera interfaccia e validazione server, quando il sorgente o un ambiente di test autorizzato sono disponibili. Il report fornisce istruzioni, non autorizza automaticamente modifica, invio di dati o pubblicazione.

### Due score in fondo al report

Mostra tutti gli score web calcolabili della rubrica, anche con bassa copertura, etichettandoli come provvisori e indicando conteggio e copertura accanto; se nessun controllo è concluso indica «non attribuibile». Affianca uno **score di conformità osservabile**, secondo references/audit-rubric.md. Colloca entrambi, con formule e copertura, nell’ultima appendice, dopo le azioni. Lo score di conformità misura soltanto i requisiti normativi applicabili effettivamente valutati nel perimetro: non presentarlo come percentuale dell’intera conformità GDPR del titolare. Specifica in linguaggio semplice se le prove sono prevalentemente documentali. Non ereditare automaticamente i voti tecnici come valutazioni giuridiche.

Se richiesto un report persistente, salva una sintesi Markdown e una baseline JSON con data, scope, scenari, domini, metadati cookie/storage, hash delle policy e rilievi; nessun valore identificativo. Confronta baseline omogenee, separando cambiamenti reali da differenze di browser, scope o osservabilità. Alla prima esecuzione dichiara che manca una baseline.

La skill è eseguibile su richiesta e non attiva da sola monitoraggio continuo. Se l'utente chiede una schedulazione, usa gli strumenti di automazione disponibili e chiarisci solo URL/frequenza mancanti. Di default notifica cambiamenti significativi, nuovi tracker, regressioni del consenso o impossibilità persistenti di verificare; resta silenzioso se tutto è invariato. Non correggere o pubblicare il sito senza un mandato di modifica.
