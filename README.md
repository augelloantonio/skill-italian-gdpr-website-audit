# skill-italian-gdpr-website-audit

Skill Codex per audit di compliance GDPR, privacy, cookie e normativa italiana/UE applicabile ai trattamenti di un sito. Integra verifiche pubbliche e documenti del titolare, con evidenze e fonti ufficiali aggiornate.

## Installazione e uso

Scarica il repository e installane il contenuto nella cartella `privacy-cookie-audit` della directory personale delle skill Codex (`~/.codex/skills/privacy-cookie-audit`). La cartella deve contenere `SKILL.md`, `agents/` e `references/`. Se è già presente una versione della skill, confrontala prima di sostituirla.

Il nome del repository è `skill-italian-gdpr-website-audit`; il nome di invocazione della skill resta `privacy-cookie-audit`.

Esempio di richiesta:

> Usa $privacy-cookie-audit su https://example.com e produci un audit di compliance con matrice normativa, verifiche tecniche e documentali, lacune organizzative e rimedi prioritari.

Per confrontare due verifiche:

> Usa $privacy-cookie-audit su https://example.org e confronta i risultati con la baseline che ti fornisco, distinguendo cambiamenti del sito e differenze nel campione.

I domini `example.com`, `example.org` ed `example.net` sono segnaposto illustrativi: sostituiscili con l'URL da analizzare. Gli esempi non rappresentano audit eseguiti né risultati su siti reali. Usa soltanto dati sintetici negli esempi condivisi e non pubblicare report, screenshot o baseline contenenti dati personali o informazioni riservate.

## Cosa controlla

- Informative privacy, cookie e trattamento dei dati.
- Cookie, storage, tracciamenti e richieste esterne osservabili.
- Banner, rifiuto, accettazione, granularità e revoca del consenso.
- Form di contatto, newsletter, prenotazioni, registrazione e altre raccolte dati.
- Servizi esterni, mappe, CAPTCHA e widget.
- Diritti dell'utente e sicurezza osservabile.

La matrice normativa comprende 13 ambiti: applicabilità e ruoli, liceità, consenso e casi particolari, trasparenza, cookie, marketing, diritti, conservazione, accountability, fornitori e trasferimenti, sicurezza, DPIA/DPO e norme ulteriori pertinenti. Ogni obbligo deve avere fonte, applicabilità, evidenza e stato.

La rubrica web accessoria comprende 28 controlli in sette categorie, con score 0–100, copertura ed evidenze. I controlli non verificabili restano espliciti; una media alta non nasconde le criticità gravi.

## Strumenti e limiti

Servono strumenti per consultare le fonti ufficiali e navigare il sito. Le verifiche comportamentali richiedono accesso a rete e storage del browser, quando disponibile e autorizzato. La skill non include un crawler o uno scanner autonomo.

La sola navigazione visiva non permette di verificare integralmente cookie, rete e storage. Conservazione reale dei dati, accessi, contratti e processi interni richiedono evidenze aggiuntive. Gli score sono indicatori tecnici e documentali, non certificazioni di conformità legale.

La skill consulta le fonti normative correnti durante ogni audit e distingue obblighi documentati, interpretazioni e miglioramenti facoltativi. Supporta confronti fra verifiche ma non attiva automaticamente monitoraggi ricorrenti.

## File

- [SKILL.md](SKILL.md): istruzioni operative e fonti ufficiali.
- [Matrice di compliance](references/compliance-matrix.md): requisiti normativi, prove organizzative e stati.
- [Rubrica](references/audit-rubric.md): controlli, formule e criteri di valutazione.
- [Verifica browser](references/browser-verification.md): raccolta delle prove, consenso per servizio e gestione delle incertezze.
- [Metadata Codex](agents/openai.yaml): nome visualizzato e prompt iniziale.
