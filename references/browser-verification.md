# Verifica con browser, DevTools e script

## Accesso e isolamento

- Scopri i browser collegati e leggi la documentazione delle capacità disponibili. Preferisci API dedicate; se non espongono rete/storage, usa l'interfaccia nativa di Chrome DevTools quando accessibile e autorizzata. Non inventare API di cookie, CDP o intercettazione.
- Usa una scheda dedicata. Preferisci una nuova sessione isolata o finestra in incognito, senza cancellare cookie, storage o preferenze del profilo dell'utente. Non presumere che ogni finestra incognito abbia uno storage distinto: le finestre incognito aperte possono condividere la sessione.
- Se non puoi accertare uno stato iniziale pulito, dichiara la possibile contaminazione e limita le conclusioni. Non attribuire al sito cookie già presenti per altre visite o account del fornitore.
- Non indebolire blocchi dei cookie, protezioni del browser o CAPTCHA per ottenere un risultato. Registra modalità del browser, cache, blocchi ed errori che possono influire sul campione; non risolvere CAPTCHA senza l'autorizzazione prevista dagli strumenti.

## Raccolta delle prove

1. Quando possibile attiva Network prima della navigazione iniziale. Se inizi dopo il caricamento, documenta il limite: un ricaricamento non ricostruisce la prima visita. Distingui richieste trasferite in rete da risorse servite da cache.
2. Osserva caricamento, attese motivate, scorrimento fino ai widget e navigazione fra pagine rappresentative. Registra richieste effettive, domini, tipo, stato e scenario; una URL nello script o nel DOM prova l'incorporamento, non l'esecuzione o la trasmissione.
3. In Application ispeziona Cookies, Local Storage, Session Storage e gli altri archivi pertinenti accessibili. Per i cookie raccogli nome, dominio, percorso, scadenza/sessione, Secure, HttpOnly, SameSite ed eventuale partizionamento. Per gli archivi raccogli solo chiavi e finalità osservabili, senza valori personali.
4. Nascondi o escludi le colonne Value e i payload identificativi prima di acquisire screenshot o esportare evidenze, quando possibile. Sanitizza anche le risposte degli strumenti prima di stamparle: non basta una regex per stringhe lunghe, perché token e identificatori possono essere brevi o strutturati. Non aprire anteprime dei valori. Non esportare HAR grezzi o cookie jar del profilo.
5. Se un attributo non compare nella vista, distingui assenza verificata da colonna nascosta o dato non esposto. HttpOnly non è sempre appropriato per un cookie letto da JavaScript. Secure assente è un rilievo tecnico da valutare nel contesto, non prova di un attacco riuscito.
6. Ripeti rifiuto, accettazione, granularità, revoca e persistenza soltanto per meccanismi presenti e con sessioni indipendenti quando possibili. Non marcare NA solo perché manca il banner: prima accerta se esistono trattamenti soggetti a consenso.

Nessun invio di form, creazione account o acquisto è necessario all'audit ordinario. La verifica di trasmissioni durante la compilazione richiede un test autorizzato con dati sintetici; se non eseguito, resta U.

## Valutazione per servizio e necessità del consenso

Per ogni servizio rilevato (anche telemetria, CDN, font, immagini remote, CAPTCHA, mappe, video, chat e login esterno):

- Associa alle richieste il servizio/funzione e l'iniziatore osservabile; distingui codice incorporato, esecuzione, trasmissione riuscita e richiesta bloccata. Identifica domini, endpoint sanitizzati, momento di attivazione e categorie di dati osservabili, senza conservare valori o payload personali. Se pertinente, ispeziona metadati e struttura dei payload in modo redatto; la sola risposta 204 non rivela quali dati siano stati inviati.
- Verifica se vengono scritte o lette informazioni sul dispositivo, con cookie, storage o altri strumenti, e per quali finalità. Considera anche tracciamento senza cookie; la mera presenza di chiamate di rete non basta a provare profilazione o accesso al terminale soggetto a consenso.
- Consulta documentazione tecnica e privacy ufficiale del servizio e confrontala con configurazione ed evidenze del sito. L'affermazione del fornitore «privacy friendly» o «senza cookie» non sostituisce questa analisi; non attribuire al servizio tutti i trattamenti descritti in una policy generale del fornitore.
- Valuta separatamente: (a) consenso preventivo per archiviazione/accesso al terminale e relativa eventuale esenzione ai sensi dell'art. 122 del Codice Privacy e indicazioni del Garante; (b) base giuridica e trasparenza GDPR per i dati personali trattati, anche senza cookie. Il legittimo interesse GDPR non sostituisce un consenso richiesto per gli strumenti sul dispositivo.
- Per un'esenzione tecnica motiva la stretta necessità rispetto alla comunicazione o al servizio esplicitamente richiesto dall'utente, senza considerare sufficiente l'utilità per il gestore. Per analytics verifica le condizioni pertinenti delle FAQ e linee guida del Garante (aggregazione, minimizzazione, combinazione e comunicazione dei dati, secondo l'assetto applicabile). Se tali condizioni non sono osservabili, elenca le prove mirate mancanti; non presumere l'esenzione.
- Concludi con uno dei tre esiti: **consenso richiesto**, **esenzione motivata per la specifica funzione/configurazione**, **da accertare**. Indica fonte corrente, ragionamento, livello di evidenza (osservato/inferito/non verificato), eventuale trattamento avviato prima della scelta e conseguenza pratica. «Da accertare» richiede una lacuna concreta, come configurazione analytics, dati del payload o condizioni contrattuali, non una formula generica.

Includi nel report una tabella: servizio/funzione | richieste o storage osservati e scenario | consenso richiesto/esenzione/da accertare | motivazione e fonte | blocco prima della scelta e revoca | prove mancanti. Mantieni separata l'eventuale base giuridica GDPR. Se tutti i servizi risultano tecnici/esenti con copertura sufficiente, motiva perché un banner non è necessario e assegna NA solo ai controlli realmente non applicabili. Se emerge un servizio soggetto a consenso, verifica blocco preventivo e gestione della scelta; l'assenza del banner non esaurisce il rilievo.

## Script e fallback

Uno script HTTP può leggere redirect e Set-Cookie delle risposte ricevute, ma non esegue JavaScript, iframe o caricamenti differiti. document.cookie non mostra HttpOnly né tutti i cookie delle origini terze; da solo non basta per un inventario completo.

Se serve automazione, verifica prima la disponibilità di un browser automatizzabile e delle sue librerie. Usa un contesto temporaneo dedicato e le API documentate; evita profili personali, debug remoto esposto e installazioni o modifiche al progetto non autorizzate. Preferisci la verifica con il browser già collegato quando sufficiente. Se uno script riceve 403, verifica la normale navigazione con il browser senza aggirare protezioni.

Se resta un blocco, indica tentativo, errore e parte del mandato ancora non verificata. Non fermarti alla promessa di poter usare Chrome e non dichiarare un inventario completato dopo aver soltanto aperto DevTools.

## Score e confronto

Applica la rubrica esistente senza aumentare la copertura per la sola disponibilità di nuovi strumenti. Ogni cambiamento di stato deve avere evidenza, URL/scenario e limiti; aspetti sconosciuti senza difetti osservati restano U. Un inventario incompleto non è di per sé un difetto del sito e non giustifica uno stato numerico al posto di U.

Spiega copertura come quota di controlli con valutazione numerica, distinta dallo score e dalla completezza del sito. Mostra conteggi oltre alle percentuali e segnala i voti provvisori. Distingui variazioni reali del sito da maggiore osservabilità, cambio di sessione o diverso campione. Non attribuire un miglioramento al sito quando è migliorata soltanto la verifica.

## Chiarimenti e chiusura delle incertezze

Mantieni un registro essenziale: punto incerto | controllo/servizio coinvolto | evidenza già raccolta | domanda | risposta e provenienza | prova da verificare | esito aperto/chiuso. Una domanda serve a ottenere una decisione o una prova che il browser non può fornire; non chiedere all'utente ciò che puoi ancora accertare con gli strumenti disponibili.

Poni le domande durante il lavoro, appena diventano rilevanti, raggruppando quelle collegate per ridurre le interruzioni. Usa lo strumento di input asincrono quando disponibile e continua le parti indipendenti. Specifica perché la risposta cambia la conclusione e quali dettagli bastano; non richiedere credenziali, token, cookie grezzi, dati personali o accesso indiscriminato al pannello. Preferisci descrizioni della configurazione e documenti o estratti pertinenti redatti. Una risposta può dichiarare anche «non so» o «non disponibile».

Esempi da adattare alle evidenze, senza usarli come questionario obbligatorio:

- Analytics: quale prodotto e funzione sono abilitati (Web Analytics, Browser Insights/RUM o altri)? Quali opzioni, conservazione, aggregazione e condizioni sul riutilizzo/combinazione dei dati si applicano? La risposta serve a verificare l'esenzione, non basta il nome del prodotto.
- Anti-bot: quali superfici protegge e perché deve attivarsi prima dell'interazione? È abilitata la pre-clearance o altra funzione che cambia cookie e trattamento?
- Fornitori: quali accordi e garanzie sui trasferimenti si applicano al servizio effettivo? Chiedi la sola evidenza pertinente e redatta.
- Conservazione: quali tempi sono effettivamente applicati a log, email e backup e come vengono eseguite le cancellazioni? Distingui dichiarazione e attuazione dimostrata.
- Consenso e diritti: chi gestisce le richieste e quali procedure o registrazioni possono essere verificate senza inviare richieste reali o usare account personali?

Valuta ogni risposta contro le evidenze osservate; se è contraddittoria, chiedi un chiarimento specifico. Marca come **dichiarato dal titolare** ciò che non è stato riscontrato. Non innalzare automaticamente score o copertura sulla base di una risposta: applica i requisiti di evidenza del singolo controllo della rubrica. Per controlli documentali una dichiarazione nel documento può essere evidenza sufficiente della sua presenza, non della sua attuazione.

Alla chiusura del lavoro indipendente, se una risposta indispensabile è ancora pendente, consegna soltanto un esito preliminare con le domande aperte e indica che l'audit resta incompleto; riprendi quando arrivano le risposte. Se il titolare non può fornire la prova, registra il limite e mantieni U o il difetto effettivamente dimostrato. Non reiterare richieste già risposte e non presumere violazioni dal mancato riscontro.

Controllo di completezza finale: copertura delle pagine e degli scenari dichiarati; inventario dei servizi con conclusione sul consenso; tutti i controlli della rubrica motivati; risposte e prove riconciliate; domande residue con impatto esplicito; score ricalcolati senza assimilare ignoto a superato. «Audit completo» richiede che siano chiuse le lacune rilevanti del perimetro concordato; non equivale a certificazione legale.
