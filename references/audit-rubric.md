# Rubrica audit privacy web — versione 1

Gli score misurano i controlli tecnici/documentali del campione, non probabilità di sanzione, certificazione o percentuale di conformità al GDPR. Usa gli stessi controlli nei confronti temporali. Non dedurre requisiti normativi dalla rubrica: consulta le fonti ufficiali aggiornate e giustifica l'applicabilità.

## Categorie e controlli

Ogni categoria contiene quattro controlli, di pari peso. Un controllo è soddisfatto solo se lo sono tutti gli aspetti applicabili elencati. Riporta separatamente esistenza di una dichiarazione e verifica della sua attuazione.

| Categoria | Controlli |
|---|---|
| Informative e trasparenza | I1: informative reperibili e accessibili nei punti di raccolta; I2: titolare e contatti identificati, DPO se applicabile; I3: finalità, basi giuridiche e obbligatorietà/conseguenze del conferimento descritte per i trattamenti osservati; I4: destinatari, conservazione o criteri, trasferimenti e garanzie se applicabili dichiarati e coerenti con le evidenze |
| Cookie e tracciamenti | T1: cookie/storage e richieste inventariati prima delle interazioni con osservabilità adeguata; T2: tracciamenti soggetti a consenso bloccati prima della scelta; T3: finalità, fornitori e durate osservate coerenti con l'informativa; T4: caricamenti differiti e pagine campionate non introducono tracker non dichiarati o non autorizzati |
| Gestione del consenso | C1: rifiuto/chiusura realmente disponibili senza consenso forzato, con scelte chiare e accessibili; C2: scelte granulari applicabili e assenza di preselezione dei trattamenti facoltativi; C3: scelte persistono e sono rispettate dopo ricaricamento/navigazione; C4: revoca o modifica facilmente accessibile e rispettata nei trattamenti futuri |
| Form e raccolta dati | F1: informativa pertinente disponibile prima dell'invio; F2: campi e obbligatorietà proporzionati alla finalità, senza richieste eccedenti evidenti; F3: eventuali consensi marketing/profilazione separati, facoltativi e non preselezionati, senza confonderli con la presa visione; F4: destinazioni tecniche visibili, CAPTCHA/chat/upload coerenti con informativa e gestione del consenso quando richiesto |
| Servizi esterni | E1: fornitori effettivamente osservati identificati e spiegati; E2: embed/widget soggetti a consenso rispettano il blocco preventivo; E3: trasferimenti e garanzie pertinenti descritti senza contraddizioni con evidenze disponibili; E4: interazione con link esterni distinta dall'incorporamento automatico, con informazione comprensibile sui servizi interessati |
| Diritti e controllo dell'utente | D1: diritti applicabili e modalità di esercizio descritti; D2: recapito/canale privacy utilizzabile e reperibile, senza test di invio; D3: diritto di reclamo all'autorità descritto; D4: revoca/opposizione/disiscrizione previste dove applicabili, valutando solo interfacce/documenti accessibili senza account o invii |
| Sicurezza osservabile | S1: HTTPS e trasporto delle destinazioni form osservabili senza contenuti attivi misti; S2: attributi Secure/HttpOnly/SameSite adeguati alla funzione dei cookie osservati, senza pretendere HttpOnly per cookie che devono essere letti da JS; S3: nessuna esposizione evidente di dati personali o credenziali in URL, pagine o risorse campionate; S4: input sensibili non trasmessi a terzi prima dell'invio/consenso ove richiesto, verificabile solo con strumenti e test autorizzati |

L'inventario T1 è una misura della verificabilità tecnica, non un obbligo di pubblicare un inventario di richieste HTTP. Assenza di form, tracker soggetti a consenso o cookie può rendere intere categorie o singoli controlli non applicabili, ma va sostenuta da copertura adeguata. Non classificare cookie tecnici come non conformi soltanto perché manca un banner.

## Stati e calcolo

Per ogni controllo conserva ID, stato, evidenza, URL/scenario, motivazione e limite:
- **2 — soddisfatto:** evidenza sufficiente per tutti gli aspetti applicabili nel campione.
- **1 — parziale:** almeno un aspetto verificato ma incompleto o incoerente; descrivi cosa manca.
- **0 — non soddisfatto:** evidenza di problema o assenza verificata di un elemento applicabile.
- **U — non verificato:** strumenti/accesso/evidenze insufficienti. Non significa zero e non significa superato.
- **NA — non applicabile:** esclusione motivata con evidenze. Non usare NA per nascondere un controllo non eseguibile.

Se un controllo combina aspetti sconosciuti e nessun difetto osservato, usa U anziché 2. Se un difetto è osservato, puoi assegnare 0/1 esplicitando anche gli aspetti non verificati; lo score non implica una verifica completa di questi ultimi.

Per ogni categoria:
- `applicabili = numero di controlli diversi da NA`.
- `verificati = numero di controlli con stato numerico`.
- `copertura = 100 * verificati / applicabili`.
- `score = 100 * somma(stati numerici) / (2 * verificati)`; arrotonda all'intero solo in presentazione.
- Se applicabili = 0: categoria NA, nessun voto.
- Se verificati = 0: score non attribuibile, copertura 0%.
- Se copertura < 75%: mostra l'eventuale score come **provvisorio**, mai come verdetto favorevole.

L'indice complessivo, facoltativo, è la media non arrotondata degli score delle categorie applicabili, a pesi uguali. Mostralo soltanto se tutte queste categorie raggiungono il 75% di copertura e nessuna è priva di score. Altrimenti scrivi «indice complessivo non attribuito: copertura insufficiente». Riporta sempre la copertura totale e il campione. Le soglie sono convenzioni della rubrica, non soglie del Garante.

Esempi di verifica aritmetica:
- [2, 2, U, NA] → score 100 provvisorio; copertura 2/3 = 67%. Non è una categoria verificata al 100%.
- [2, 1, 0, U] → score 50; copertura 75%; conserva il limite del quarto controllo.
- [NA, NA, NA, NA] → NA, esclusa dalla media.
- [U, U, U, U] → non attribuibile, copertura 0%.

## Priorità e consegna

La gravità è distinta dal voto: evidenzia in apertura tracciamenti non autorizzati osservati, rifiuto inefficace, consenso marketing forzato o esposizioni di dati/credenziali. Una buona media non compensa questi rilievi. Non attribuire automaticamente gravità critica a un'ipotesi non verificata.

Consegna:
1. Dominio, data, pagine e scenari esaminati; limite principale.
2. Tabella normativa a semaforo e rilievi ordinati per impatto, con prove, fonte pertinente, azione e verifica di chiusura.
3. Piano di azioni con priorità e natura, seguito da istruzioni operative di correzione.
4. Appendice finale: score di conformità osservabile e score web per categoria, copertura, controlli U e NA e principali limiti.
5. Nel corpo del report, dichiarazioni o configurazioni da verificare lato server/titolare: conservazione reale, gestione richieste privacy, contratti, accessi, cancellazione, eventuali consensi registrati. Non dedurre tali aspetti dallo score frontend.

Per un report persistente salva anche rubric_version=1 e gli stati dei singoli controlli; non memorizzare soltanto i voti. Confronta punteggi soltanto a rubrica e campione comparabili, segnalando nuove pagine o cambiamenti nell'osservabilità.

Prima dell’appendice finale dei punteggi presenta la lista di azioni con priorità definita in SKILL.md: collega ogni voce a un rilievo, distingui obbligo accertato/obbligo condizionato/verifica da completare/consiglio facoltativo e indica responsabile suggerito, dipendenze e criterio di chiusura. Le priorità operative non sono voti di conformità o scadenze legali.

## Score di conformità osservabile — convenzione v1

Affianca agli score web uno score normativo distinto. Dalla matrice ricava un elenco di requisiti specifici non sovrapposti: lo stesso difetto non va contato più volte attraverso articoli o categorie diverse. Definisci il perimetro prima del calcolo e riporta anche i requisiti ignoti o di applicabilità incerta, senza selezionare solo quelli favorevoli. Per ogni requisito indica fonte, applicabilità, prova e stato: 2 soddisfatto nel perimetro verificato; 1 adempimento parziale con lacuna dimostrata; 0 inosservanza dimostrata; U non verificato o applicabilità aperta; NA non applicabile motivato. Dividi i requisiti compositi quando consentito dalle prove.

Formula: `100 * somma(stati numerici) / (2 * numero di requisiti con stato numerico)`. Copertura: `100 * requisiti con stato numerico / requisiti diversi da NA`. U non vale zero né superato. Se nessun requisito ha esito numerico, score non attribuibile. Mantieni ogni calcolo ricostruibile dal registro.

Intitola il risultato «Score di conformità osservabile: X/100 sui requisiti valutati», con copertura in conteggio e percentuale accanto. Con copertura inferiore al 75% indica «provvisorio — prove incomplete»; la soglia è una convenzione, non normativa. Non chiamarlo «sito conforme X%», non usarlo come certificazione, non confrontarlo con score di diverso perimetro o versione. Descrivi quali tipi di adempimenti il numero rappresenta e quali restano aperti; un voto documentale non verifica attuazione e liceità dei trattamenti. Evidenzia comunque i difetti gravi, che il voto medio non compensa.

In fondo al report presenta prima questo score con il relativo registro, poi gli score web preesistenti con copertura e limiti. Le azioni precedono entrambi.
