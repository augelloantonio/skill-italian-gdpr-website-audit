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

Se richiesto un report persistente, salva una sintesi Markdown e una baseline JSON con data, scope, scenari, domini, metadati cookie/storage, hash delle policy e rilievi; nessun valore identificativo. Confronta baseline omogenee, separando cambiamenti reali da differenze di browser, scope o osservabilità. Alla prima esecuzione dichiara che manca una baseline.

La skill è eseguibile su richiesta e non attiva da sola monitoraggio continuo. Se l'utente chiede una schedulazione, usa gli strumenti di automazione disponibili e chiarisci solo URL/frequenza mancanti. Di default notifica cambiamenti significativi, nuovi tracker, regressioni del consenso o impossibilità persistenti di verificare; resta silenzioso se tutto è invariato. Non correggere o pubblicare il sito senza un mandato di modifica.
