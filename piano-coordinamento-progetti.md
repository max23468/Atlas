# Atlas - piano di coordinamento operativo dei progetti

Data: 2026-05-23

Stato: piano decisionale approvato, pronto per trasformazione in interventi repo-per-repo.

## Obiettivo

Costruire un coordinamento pieno tra i progetti locali:

- Pratix
- DocMolder
- FiscalBay
- GLM
- SendChimp
- SyncBay
- TRAM
- Atlas
- Sentinel

L’obiettivo non è rendere le repository identiche. L’obiettivo è renderle coerenti con lo stile operativo, le aspettative e il modo di lavorare del maintainer, mantenendo le differenze tecniche reali di ciascun progetto.

Principio guida:

> Standardizzare governance, linguaggio, decisioni, verifiche, GitHub, pubblicazione, roadmap e handoff; lasciare repo-specifici solo runtime, target tecnici e comandi concreti.

## Ambito e metodo

Questo piano è una base di governo operativo, non un intervento di refactor.

Include:

- regole comuni per lavorare nelle repo;
- struttura minima dei documenti governanti;
- criteri comuni per roadmap, backlog, ADR e handoff;
- semantica comune dei comandi operativi;
- criteri per test, verifiche, GitHub, Codex inbox, release e deploy;
- differenze da rispettare tra progetti;
- sequenza operativa di intervento.

Non include:

- modifiche funzionali ai prodotti;
- migrazioni di stack;
- cambio di provider o runtime;
- normalizzazione forzata di provider, runtime o comandi tecnici;
- sostituzione delle policy specifiche già mature;
- eliminazione di differenze tecniche motivate.

Metodo:

1. leggere la repo reale prima di applicare qualsiasi standard;
2. distinguere standard comune e policy repo-specifica;
3. introdurre prima documenti e regole di coordinamento;
4. applicare poi i cambiamenti repository per repository;
5. verificare ogni intervento con i comandi previsti dalla repo, non con una checklist generica.

## Stato ricognizione

Ricognizione iniziale eseguita sulle repository locali in `~/Documents`. Al ricontrollo del 2026-05-24 i checkout operativi risultano sotto `/Users/Matteo/Progetti`.

Risultati principali dello snapshot iniziale, da non riusare senza verifica live:

- tutte le repo hanno `AGENTS.md`;
- tutte le repo sono su `main` allineato a `origin/main`;
- non risultano worktree temporanei attivi;
- non risultano PR aperte su GitHub;
- tutte le repo hanno una `Codex feedback inbox`;
- tutte le inbox Codex risultavano senza thread actionable al momento della ricognizione;
- il workflow `Codex PR comments` e lo script `.github/scripts/handle-codex-pr-comments.mjs` sono già uniformi in tutte le repo.

## Decisioni approvate prima dell’esecuzione

Prima di aprire interventi sulle singole repo sono fissate queste scelte:

1. posizione canonica della roadmap: `docs/ROADMAP.md`;
2. posizione canonica dell’indice documentale: `docs/INDEX.md`;
3. posizione canonica del backlog: `docs/BACKLOG.md`;
4. formato ADR minimo: cartella, naming, stati e template;
5. livello minimo GitHub per tutte le repo: PR template, issue template, branch protection, title check;
6. regola comune per commenti Codex: inbox obbligatoria prima di PR/pubblicazione;
7. definizione condivisa di “pubblica”, “deploya” e “rilascia”;
8. frequenza della manutenzione periodica;
9. disciplina operativa per coordinare gli interventi senza perdere contenuti o contesto;
10. applicabilità obbligatoria di React Doctor nelle app React dopo release minor `X.Y.Z`.
11. baseline obbligatoria per nuovi progetti, così ogni nuova repo nasce già coordinata.
12. confine generale tra ciò che resta in root e ciò che deve stare in `docs/`.
13. baseline toolchain e versioni minime per nuovi progetti.

Queste decisioni non sono tutte complesse. Sono però esplicite, così il piano non trasferisce ambiguità da una repo all’altra.

Regole di partenza approvate:

- non rinominare documenti già maturi solo per uniformare i path, con eccezione della roadmap;
- standardizzare prima la reperibilità: `README.md` e `AGENTS.md` devono indicare sempre i documenti canonici;
- usare `docs/ROADMAP.md` come unica posizione canonica della roadmap;
- usare `docs/INDEX.md` come indice documentale unico;
- usare `docs/DECISIONS.md` come indice decisionale e `docs/decisions/` come standard per ADR puntuali;
- non creare due file Markdown con lo stesso basename nella stessa repo;
- mantenere `Codex PR comments` e `Codex feedback inbox` come standard comune già acquisito;
- rendere React Doctor obbligatorio nelle app React dopo ogni release minor dello schema `X.Y.Z`;

## Aggiornamento stato 2026-05-24

Questo piano nasce come snapshot del 2026-05-23. Prima di applicarlo a una repo, verificare sempre il checkout reale.

Novità recepite:

- Atlas è ora un progetto Git/GitHub dedicato, repository privata `https://github.com/max23468/Atlas`.
- SendChimp non è più solo documentazione: ha scaffold runtime Next.js/React con Vercel, Neon Free/Postgres 17 e Neon Auth. Resta però MVP manuale, senza invii WhatsApp automatici produttivi e con vincolo free-tier.
- DocMolder usa Python `>=3.11` nel manifest, testa anche Python `3.13` in CI e documenta Python `3.13` come runtime preferito per sviluppo operativo/VPS. Non trattarlo come progetto `>=3.10`.
- FiscalBay è stato riallineato a Python `3.13` come baseline unica per
  manifest, lint/typecheck, CI, package build e VPS. Le vecchie note sullo
  stato misto `3.10` sono storiche e non vanno usate come policy corrente.
- Sentinel non è più descrivibile come sola cache locale: al ricontrollo del 2026-05-24 esiste `/Users/Matteo/Progetti/Sentinel`, repo GitHub privata `max23468/Sentinel` su `main`, con CLI Node.js/TypeScript, workflow schedulato/dispatch e output applicativi committabili.

Conseguenza: l'ordine operativo va rivalutato prima di ogni applicazione repo-per-repo. In particolare, SendChimp non va più trattato come docs-only. GLM e TRAM sono stati usati come primi pilot di allineamento su repo esistenti; Sentinel va invece trattata come baseline runtime separata, non più come repo senza remote.

Tabella decisionale approvata:

| Area | Decisione | Stato |
| --- | --- | --- |
| Roadmap | Usare `docs/ROADMAP.md` come unica roadmap canonica; eventuali `ROADMAP.md` in root vanno migrati o sostituiti con rinvio temporaneo | Approvato |
| Indice documentale | Usare `docs/INDEX.md` come indice documentale unico; eventuali `docs/README.md` vanno migrati o sostituiti con rinvio temporaneo | Approvato |
| Backlog | Usare `docs/BACKLOG.md` come backlog unico separato dalla roadmap | Approvato |
| ADR | Usare `docs/DECISIONS.md` come indice decisionale e `docs/decisions/` come standard per nuove ADR puntuali | Approvato |
| Basename Markdown | Non creare due file Markdown con lo stesso basename nella stessa repo | Approvato |
| GitHub baseline | PR template, issue template minima, PR title check, Codex inbox, workflow Codex PR comments; Dependabot come standard pieno nelle repo con dipendenze o manifest compatibili; branch protection solo per repo operative/condivise | Approvato |
| Commenti Codex | Controllo obbligatorio della `Codex feedback inbox` prima di PR ready, merge, pubblicazione, deploy o release | Approvato |
| Publish/deploy/release | Usare una semantica e un protocollo comuni per `pubblica`, `deploya` e `rilascia`; ogni repo dichiara solo target e comandi tecnici | Approvato |
| Manutenzione | Check leggero mensile più controllo obbligatorio prima di publish, deploy o release | Approvato |
| React Doctor | Obbligatorio nelle app React dopo ogni release minor `X.Y.Z`; applicabile anche a SendChimp, che oggi ha runtime React/Next.js | Approvato |
| Nuovi progetti | Avviare ogni nuova repo da una baseline completa: governance, docs, GitHub, verifiche, release/deploy policy e handoff | Approvato |
| Root vs docs | Root solo per ingresso, istruzioni agenti, configurazione/tooling e sorgente; `docs/` per governance, roadmap, decisioni, contesto e approfondimenti | Approvato |
| Coordinamento operativo | Applicare il piano con controllo centrale, discovery read-only iniziale, una repo per volta in scrittura e nessuna perdita di contenuti | Approvato |
| Toolchain/versioni | Ogni repo deve dichiarare runtime, package manager, engines, lockfile e versioni minime in configurazione più `docs/TOOLCHAIN.md`; baseline: latest LTS per Node, latest stable compatibile per Python, guardrail repo-specifici dove esistono | Approvato |

Elementi recepiti nel piano:

- separare standard di coordinamento e template operativo per nuovi progetti;
- aggiungere una mappa `source of truth` per ogni repo;
- rafforzare la classificazione di maturità con requisiti minimi e limiti;
- aggiungere una definizione di “pronto per intervenire” su una repo;
- aggiungere un registro dei vincoli repo-specifici;
- trasformare la baseline nuovi progetti in un kit di avvio riusabile;
- applicare una cadenza di manutenzione leggera mensile e obbligatoria prima di publish/deploy/release.

## Lista aggiornata dei punti da uniformare

### 1. AGENTS.md

Uniformare struttura e contenuto minimo:

- priorità delle istruzioni: sistema/developer, `AGENTS.md`, eventuali `AGENTS.md` più profondi, documenti canonici, richiesta utente, convenzioni reali e assunzioni marginali;
- identità, fase, perimetro, assi di validità e non-obiettivi;
- fonti primarie da leggere prima di modifiche non banali, incluse guide, runbook, codice, test e configurazioni collegate;
- workflow iniziale: `git status --short`, lettura file vicini, controllo inbox, scelta verifiche e valutazione docs/changelog/versioning/release/deploy;
- gestione modifiche non proprie, branch dedicata, worktree quando serve e cleanup con controllo `git branch -vv`/`git worktree list` quando applicabile;
- branch/PR default per lavori non banali; commit diretto su `main` solo per micro docs-only ammessi dalla policy locale;
- `Codex feedback inbox` obbligatoria prima di PR ready, merge, pubblicazione, deploy o release;
- verifiche proporzionate in corsie `veloce`, `standard` e `completa`, con comandi repo-specifici;
- semantica di `pubblica` completa ma proporzionata: canale canonico, verifiche, inbox, valutazione release/deploy, verifica finale e cleanup;
- release e deploy valutati insieme quando entrambi applicabili;
- versioning, changelog, categorie Conventional Commit e rilascio valutati a ogni chiusura, anche quando il risultato è `Non versionato`;
- nessuna release o changelog affidati a bot automatici come fonte primaria senza decisione esplicita;
- GitHub, PR, merge, self-review, PR title check e divieto di nuove automazioni non decise;
- documentazione canonica, roadmap, backlog, decisioni, anti-duplicati e anti-perdita;
- UI/React/browser checks quando applicabili, prendendo il modello più completo emerso da Pratix, GLM, SendChimp, SyncBay e TRAM;
- provider, API, fonti aggiornabili, costi/free-tier, privacy e minimizzazione;
- deploy, produzione, verifica live, rollback/runbook e attivazioni produttive solo se decise;
- sicurezza, dati, segreti, `.env`, dati reali, screenshot/report e controlli booleani;
- file generati, temporanei e output applicativi committabili solo se dichiarati;
- risposta finale uniforme;
- definizione di completamento unica.

### 2. Catalogo documentazione

Ogni repo deve avere un catalogo documentale leggibile e prevedibile.

Regola generale:

- la root deve restare il punto di ingresso e di esecuzione;
- `docs/` deve contenere governance, decisioni, roadmap, contesto, guide e approfondimenti;
- un file resta in root solo se serve subito a orientare, avviare, configurare o far funzionare il progetto;
- un documento va in `docs/` se serve a spiegare, governare, decidere, ricordare o approfondire.

Struttura minima approvata:

- `README.md`: ingresso rapido;
- `AGENTS.md`: regole operative per Codex e agenti;
- `CHANGELOG.md`: solo se la repo ha versioning o release;
- `docs/ROADMAP.md`;
- `docs/INDEX.md`;
- `docs/BACKLOG.md`;
- `docs/TOOLCHAIN.md`;
- `docs/CONTEXT.md` oppure `docs/context.md`;
- guida Git/pubblicazione;
- guida versioning/release se applicabile;
- guida deploy/operations se esiste runtime;
- ADR o documento decisioni;
- guida sicurezza/privacy/dati quando il progetto tratta dati reali o provider esterni.

Regola anti-duplicati:

- non devono esistere due documenti con lo stesso titolo, scopo o ruolo canonico;
- se due documenti coprono la stessa funzione, va scelto un solo source of truth;
- il documento non canonico va migrato, archiviato o trasformato in rinvio temporaneo;
- i rinvii temporanei devono indicare chiaramente il documento canonico;
- evitare coppie come `docs/README.md` e `docs/INDEX.md` con contenuto equivalente.

Regola anti-perdita:

- nessun contenuto va perso durante migrazioni, merge documentali o rinomini;
- prima di eliminare, archiviare o sostituire un documento bisogna verificare che ogni informazione utile sia stata migrata, collegata o dichiarata superata;
- se un contenuto viene rimosso per uniformità, la rimozione deve essere esplicita nel riepilogo dell’intervento;
- i rinvii temporanei sono preferibili alla cancellazione quando non è certo che tutto il contenuto sia stato assorbito;
- le migrazioni devono preservare link, riferimenti operativi, comandi, vincoli, decisioni e contesto storico utile;
- strumenti, automazioni e riscritture non devono perdere pezzi: la perdita di contenuto è ammessa solo su decisione esplicita.

### 2.1 Root e docs

La root non deve diventare un archivio documentale.

In root devono stare:

- `README.md`: porta d’ingresso del progetto;
- `AGENTS.md`: regole operative per Codex e agenti;
- `CHANGELOG.md`: storico release, se la repo ha versioning o release;
- `LICENSE`, se applicabile;
- file di configurazione richiesti dagli strumenti;
- lockfile e manifest runtime;
- `.env.example` o equivalenti, se utili al setup;
- `.github/`, perché è configurazione GitHub;
- directory sorgente, test, script e asset runtime;
- configurazioni deploy richieste dalla piattaforma.

In `docs/` devono stare:

- `docs/ROADMAP.md`;
- `docs/INDEX.md`;
- `docs/BACKLOG.md`;
- contesto e handoff;
- ADR e decisioni pending;
- backlog, piani e milestone;
- architettura;
- data model;
- guide operative;
- versioning e release policy estese;
- toolchain, runtime e versioni minime;
- deploy, operations, runbook, health e rollback;
- sicurezza, privacy, segreti, provider e API;
- brand, glossario, tono e posizionamento;
- ricerche, benchmark, report e analisi;
- allegati documentali non runtime.

Eccezioni ammesse:

- file richiesti in root da framework, package manager, deploy platform o GitHub;
- `CHANGELOG.md` in root, perché è uno standard riconoscibile e spesso collegato alla release;
- documenti brevissimi nel `README.md`, purché rimandino alla fonte completa in `docs/`;
- template GitHub dentro `.github/`, perché sono configurazione operativa, non documentazione di prodotto.

Regola pratica: se un contenuto serve a “usare o avviare” la repo, può stare in root; se serve a “capire, decidere o governare” la repo, sta in `docs/`.

### 3. Roadmap

La gestione della roadmap va inserita esplicitamente.

Standard approvato:

- una sola roadmap canonica per repo, sempre in `docs/ROADMAP.md`;
- distinguere `Ora`, `Prossimo`, `Più avanti`, `Bloccato`, `Fatto`;
- non lasciare lunghe checklist completate come archivio;
- spostare decisioni stabili in ADR o documentazione;
- usare la roadmap per priorità e stato, non per dettagli di implementazione;
- aggiornare la roadmap quando cambia direzione, priorità, fase o backlog;
- non aggiornarla per micro-decisioni già chiuse nello stesso intervento;
- indicare sempre il prossimo passo operativo reale.

### 4. Backlog

Separare roadmap e backlog.

Standard approvato:

- una sola backlog canonica per repo, sempre in `docs/BACKLOG.md`;
- la roadmap descrive direzione, priorità e fase;
- il backlog raccoglie idee, debiti, bug, ipotesi, attività non ancora scelte;
- un elemento nel backlog non è scope approvato;
- quando un elemento diventa prioritario, viene promosso in roadmap;
- quando una decisione diventa stabile, viene spostata o collegata ad ADR/documentazione.

Categorie standard:

- idee prodotto;
- backlog tecnico;
- bug;
- debiti;
- idee future;
- decisioni sospese;
- attività operative ricorrenti.

Regola: un’idea non decisa non deve diventare scope implicito.

### 5. ADR e lifecycle decisionale

Uniformare quando serve una decisione formale.

Standard approvato:

- le nuove ADR vanno in `docs/decisions/`;
- naming standard: `NNNN-slug-breve.md`;
- `docs/decisions/template.md` deve esistere in ogni repo con governance viva;
- `docs/DECISIONS.md` deve indicizzare le decisioni;
- `docs/INDEX.md` deve collegare `docs/DECISIONS.md` e `docs/decisions/`;
- `docs/DECISIONS_PENDING.md` o `docs/decisions-pending.md` può restare per decisioni non ancora approvate;
- non creare documenti duplicati con stesso titolo o stessa decisione.
- non creare due file Markdown con lo stesso basename nella stessa repo.

Serve ADR quando cambia stabilmente:

- architettura;
- stack;
- deploy;
- dati;
- sicurezza/privacy;
- AI/provider;
- versioning;
- processo operativo;
- perimetro prodotto;
- brand strutturale.

Stati standard:

- `Proposta`;
- `Accettata`;
- `Superata`;
- `Sospesa`;
- `Respinta`.

Quando non serve ADR:

- fix piccolo;
- microcopy;
- chiarimento già coerente con documenti esistenti;
- task operativo senza decisione durevole.

### 6. Handoff e contesto

Ogni repo deve avere un punto di handoff.

Contenuti minimi:

- stato progetto;
- fase corrente;
- ultimo deploy/release rilevante;
- prossima azione reale;
- blocchi aperti;
- rischi noti;
- documenti da leggere per una nuova chat;
- policy specifiche da non dimenticare.

Per repo mature usare `docs/CONTEXT.md`.
Per repo docs-first può bastare `docs/context.md`.

### 7. Versioning

Uniformare la semantica, non necessariamente gli strumenti.

Classificazione comune:

- `MAJOR`: breaking change visibile o contrattuale;
- `MINOR`: nuova funzionalità retrocompatibile;
- `PATCH`: fix, hardening, UI/copy, manutenzione runtime compatibile;
- `Non versionato`: docs interne, piani, ADR, regole agenti, test-only, formattazione isolata, note locali.

Regole comuni:

- valutare sempre impatto versioning prima di chiudere;
- non bumpare per docs interne non operative;
- non mescolare `Non versionato` e voci versionate nello stesso rilascio, se lo script non lo supporta;
- distinguere changelog utente da note interne;
- non fare version bump manuali fuori dal flusso previsto dalla repo.

### 8. Pubblicazione, deploy e release

Uniformare parole chiave, protocollo e gate.

Definizioni comuni:

- `pubblica`: porta il lavoro nel canale canonico della repo, normalmente PR/merge verso branch principale o pubblicazione documentale GitHub;
- `deploya`: aggiorna il runtime o l’ambiente operativo dichiarato dalla repo;
- `rilascia`: crea o chiude una versione, con changelog/tag/release secondo la policy della repo;
- `pubblica tutto`: esegue, nell’ordine corretto, pubblicazione GitHub, eventuale release, eventuale deploy, verifica finale e cleanup.

Standard comune approvato:

1. leggere `AGENTS.md` e source of truth;
2. controllare `git status --short`;
3. controllare `Codex feedback inbox`;
4. eseguire verifiche proporzionate richieste dalla repo;
5. aggiornare docs/versioning/changelog quando previsto;
6. pubblicare tramite PR/merge o canale GitHub previsto;
7. rilasciare solo se la repo ha release policy o se il comando utente lo richiede;
8. deployare solo se esistono target, runbook e verifiche;
9. verificare il risultato nel canale finale;
10. fare cleanup branch/worktree quando previsto;
11. chiudere con stato, versione, canale, verifiche e rischi residui.

Adattatori repo-specifici:

| Repo | `pubblica` | `rilascia` | `deploya` |
| --- | --- | --- | --- |
| Pratix | PR/merge GitHub verso main | `npm run release` secondo policy | Vercel production quando previsto |
| DocMolder | PR/merge GitHub | policy release manuale repo-specifica | VPS/runbook quando previsto |
| FiscalBay | PR/merge GitHub o flusso repo | `scripts/release_now.sh` quando previsto | `scripts/deploy_now.sh`/VPS quando previsto |
| GLM | PR/merge GitHub | `npm run release` quando previsto | Cloudflare Pages solo su richiesta/target dichiarato |
| SendChimp | PR/merge GitHub | release locale se prevista | Vercel solo quando previsto e protetto da Neon Auth; nessun invio automatico |
| SyncBay | PR/merge GitHub | `npm run release` locale quando previsto | Vercel production pilota; Shopify App Store production non attiva |
| TRAM | PR/merge GitHub | SemVer `0.x` secondo ADR `0003`; tag/GitHub Release solo quando richiesto | non applicabile finché manca target deploy approvato |
| Atlas | push/PR verso repository privata GitHub | non applicabile | non applicabile |
| Sentinel | GitHub privata `max23468/Sentinel`, commit su `main` | tag/GitHub Release solo per tool/dashboard | GitHub Actions schedulata/dispatch per runtime; dashboard Vercel/Blob separata |

Regola: il protocollo è comune; cambiano solo comandi, provider e target.

### 9. Commenti Codex

Infrastruttura già uniforme:

- workflow `Codex PR comments`;
- issue `Codex feedback inbox`;
- handler `.github/scripts/handle-codex-pr-comments.mjs`.

Standard approvato:

- controllare la `Codex feedback inbox` prima di PR ready, merge, pubblicazione, deploy o release;
- se ci sono thread actionable, risolverli o dichiarare perché restano fuori scope;
- non usare file Markdown/JSON committati come inbox alternativa;
- ricontrollare i commenti prima del merge quando il flusso è non banale o ha ricevuto nuovi commenti;
- per repo mature, avere anche uno script/report locale di manutenzione GitHub.

Output minimo quando restano thread aperti:

- thread o tema rimasto aperto;
- motivo per cui non viene risolto ora;
- impatto sul merge/pubblicazione/deploy/release;
- prossimo passo o owner.

### 10. GitHub

Uniformare funzionalità e policy, con peso diverso per repo.

Baseline approvata:

- PR template coerente;
- issue template minima;
- `Codex feedback inbox`;
- workflow `Codex PR comments`;
- workflow `pr-title.yml` o controllo equivalente del titolo PR;
- workflow quality/CI proporzionato alla repo;
- `dependabot.yml` solo dove ci sono dipendenze runtime reali;
- branch protection solo quando il progetto è operativo, condiviso o ha release/deploy sensibili;
- `CODEOWNERS` solo dove aggiunge reale controllo, non come burocrazia;
- squash merge con Conventional Commit quando collegato a changelog/release;
- cleanup branch dopo merge.

Regole:

- GitHub baseline non significa stessi workflow ovunque;
- i workflow devono rispettare la policy della repo e il suo stack;
- non introdurre Actions generiche in repo che hanno allowlist o deploy fuori GitHub Actions;
- i template GitHub vivono in `.github/`, non in `docs/`;
- la inbox Codex resta un canale operativo GitHub, non un documento committato;
- ogni repo deve dichiarare la policy su PR draft se diversa dal default;
- la gestione commenti Codex deve seguire la sezione dedicata;
- manutenzione periodica di PR, release e workflow.

### 11. Test e verifiche

Uniformare la classificazione del rischio.

Categorie:

- nessuna modifica / sola analisi;
- docs-only;
- documenti operativi critici;
- test-only;
- runtime piccolo;
- runtime condiviso;
- UI localizzata;
- UI sostanziale;
- database/dati;
- provider/API;
- deploy/config;
- release/versioning.

Regola comune:

- eseguire solo verifiche proporzionate;
- non inventare test non eseguiti;
- dichiarare limiti e rischi residui;
- evitare footer rituali;
- indicare comandi falliti, impatto e prossimo passo.

### 12. React Doctor e qualità React

Standard approvato:

- React Doctor è obbligatorio nelle app React dopo ogni release minor dello schema `X.Y.Z`, cioè quando cambia `Y`;
- non è obbligatorio dopo ogni patch `X.Y.Z` quando cambia solo `Z`, salvo modifiche React trasversali o rischiose;
- è obbligatorio prima di considerare chiusa una release minor React;
- se il comando React Doctor manca, va aggiunto prima della prima release minor a cui si applica;
- il risultato va citato nel riepilogo di release o nella verifica finale;
- eventuali failure vanno risolte o dichiarate come blocker.

Applicabilità:

- Pratix: obbligatorio, già presente come `quality:react-doctor`;
- GLM: obbligatorio quando consolidato come app React con release minor;
- TRAM: obbligatorio quando consolidato come app React con release minor;
- SyncBay: obbligatorio quando consolidato come app React con release minor;
- SendChimp: obbligatorio perché ha runtime React/Next.js quando avrà una release minor applicabile;
- DocMolder e FiscalBay: non applicabile finché restano repo Python/Telegram-first senza app React.

### 13. Stile, tono e lingua

Uniformare aspettative:

- italiano pratico, diretto, operativo;
- accenti e apostrofi corretti;
- no risposte compiacenti senza verifica;
- no risultati inventati;
- no footer rituali sui test;
- prossimi passi concreti;
- UI italiana dove il prodotto è italiano;
- tono coerente con progetto e pubblico.

### 14. Sicurezza, dati e privacy

Regole comuni:

- mai committare segreti;
- mai stampare token o credenziali;
- niente dati reali in fixture, screenshot, log o PR;
- host VPS corretti per progetto;
- credenziali solo da canali previsti;
- provider/API verificati da fonti ufficiali;
- dati sensibili minimizzati;
- documenti reali trattati come riservati;
- verifiche privacy prima di invii a provider esterni o AI.

### 15. Documenti reali e dati sensibili

Da esplicitare in tutte le repo che trattano dati reali.

Esempi:

- GLM: allegati gara e dati di gara;
- TRAM: pacchetti documentali gara e output AI;
- DocMolder: documenti caricati dagli utenti;
- FiscalBay: ordini e dati fiscali eBay;
- SendChimp: campagne, telefoni, consenso;
- SyncBay: shop, listing, clienti, ordini;
- Pratix: dati clienti, pratiche, fatture.
- Sentinel: rispettare `robots.txt`; non copiare segreti, password email, token, cache o HTML completo in Atlas.

Regola: ciò che serve al test deve essere sintetico o anonimizzato.

### 16. Provider, API e dati variabili

Inserire regola comune:

- usare fonti ufficiali aggiornate;
- verificare policy, prezzi, limiti, API, privacy;
- non basarsi su memoria quando il dato può essere cambiato;
- documentare data di verifica quando il dato entra in prodotto o docs;
- distinguere fonte ufficiale, fonte pubblica, assunzione e decisione interna.

### 17. Operatività produzione

Per repo con runtime:

- healthcheck;
- log recenti;
- smoke post-deploy;
- rollback;
- host corretti;
- canale deploy canonico;
- verifica versione live;
- cleanup branch/worktree;
- dichiarazione di cosa è davvero pubblicato.

### 18. Manutenzione periodica

Standard approvato:

- check leggero mensile per tutte le repo;
- check obbligatorio prima di `publish`, `deploy` o `release`;
- check proporzionato alla maturità della repo;
- nessuna release/deploy va considerata chiusa senza controllo dei punti canonici della repo.

Creare o uniformare una checklist ricorrente:

- `git status`;
- branch/worktree stale;
- PR aperte;
- inbox Codex;
- workflow falliti;
- Dependabot;
- release aperte;
- deploy/runtime health;
- documentazione obsoleta;
- roadmap/backlog;
- toolchain/versioni;
- vincoli repo-specifici.

Output minimo del check:

- stato repo;
- anomalie o blocchi;
- azioni da eseguire;
- verifiche eseguite;
- prossima manutenzione o prossimo intervento.
- security/dependency audit dove pertinente.

### 19. Coordinamento tra progetti

Creare uno standard personale comune.

Contenuti:

- come Codex deve leggere una repo;
- come rispondere alle richieste `pubblica`, `deploya`, `rilascia`;
- come gestire commenti bot;
- come fare handoff;
- come distinguere analisi, piano, codice e pubblicazione;
- come non mescolare worktree sporchi;
- come decidere quando chiedere chiarimento.

### 20. Maturità del progetto

Ogni repo va classificata per fase.

Fasi standard:

- `docs-first`;
- `MVP locale`;
- `runtime attivo`;
- `produzione`;
- `operativo con release`;
- `manutenzione/stabilizzazione`.

La fase determina:

- test minimi;
- necessità changelog;
- deploy;
- release;
- GitHub workflow;
- severità dei gate.

Requisiti e limiti standard:

| Fase | Requisiti minimi | Non introdurre ancora |
| --- | --- | --- |
| `docs-first` | `README.md`, `AGENTS.md`, roadmap, indice docs, prima decisione | deploy, release automatiche, branch protection pesante |
| `MVP locale` | comandi dev/verifica, backlog, dati e non-obiettivi chiari | produzione, rollback, processi release complessi |
| `runtime attivo` | build, smoke minimo, env documentate, security/privacy | release pubblica se non serve |
| `produzione` | deploy, health, segreti, rollback, runbook | cambi non verificati, publish ambiguo |
| `operativo con release` | versioning, changelog, release policy, CI verde | bypass dei gate release |
| `manutenzione/stabilizzazione` | check periodico, debiti tracciati, documenti aggiornati | nuove funzionalità senza roadmap |

### 21. Glossario, brand e prodotto

Uniformare processo, non contenuti.

Ogni repo deve chiarire:

- termini canonici;
- termini vietati;
- tono UI;
- posizionamento;
- non-obiettivi;
- brand o naming;
- quando aggiornare glossario/brand.

### 22. Artefatti generati e file temporanei

Regola comune:

- non committare output generati non previsti;
- non toccare file generati a mano;
- pulire `.DS_Store` quando compaiono nel working tree o risultano tracciati per errore, mantenendoli ignorati per il futuro;
- non trattare `.DS_Store` come contenuto progettuale da eliminare o discutere repo per repo;
- controllare `dist`, `.next`, `.output`, `.venv`, `node_modules`, cache e duplicati locali;
- dichiarare se restano file temporanei.

### 23. Lavoro parallelo, branch e worktree

Uniformare:

- controllo `git status` iniziale;
- branch/worktree dedicati per lavori non banali;
- non spostare modifiche non proprie su nuova branch;
- non sovrascrivere diff altrui;
- cleanup dopo merge/pubblicazione;
- handoff se più chat/agent lavorano sullo stesso progetto.

### 24. Nuovi progetti e baseline di avvio

Ogni nuovo progetto deve nascere già con il set minimo di coordinamento.

Obiettivo: non dover recuperare dopo mesi regole, documenti, roadmap, GitHub, verifiche e publish policy.

La baseline di avvio deve chiarire subito:

- identità del progetto;
- problema che risolve;
- perimetro e non-obiettivi;
- fase iniziale;
- stack e motivazione;
- dati trattati;
- provider/API previsti;
- livello GitHub minimo;
- verifiche minime;
- roadmap iniziale;
- backlog separato o sezione backlog;
- ADR iniziali;
- regola versioning;
- significato di pubblicazione, deploy e release;
- handoff per nuove chat;
- gestione Codex inbox e commenti PR;
- regole su sicurezza, privacy e segreti;
- criterio per passare da docs-first a MVP/runtime/produzione.

## Matrice repo

| Repo | Fase attuale | Documentazione | Versioning | Pubblicazione/deploy | GitHub | Verifiche | Priorità allineamento |
| --- | --- | --- | --- | --- | --- | --- | --- |
| Pratix | Produzione SaaS, seconda ondata completata | Canonica in `docs/` con roadmap, index, backlog, context e toolchain; memoria operativa preservata | SemVer locale con `npm run release`, `src/lib/version.ts`; release patch `1.11.15` pubblicata | GitHub + Vercel production; PR `max23468/Pratix#156` mergiata e `publish:finish` passato | Inbox Codex, Quality, Dependabot, template | Prepush guard completo, test mirato e smoke production `/` + `/novita`; React Doctor dopo release minor | Completata: prossimo solo debito reale |
| DocMolder | Produzione operativa Telegram/VPS, seconda ondata completata | Canonica con `docs/BACKLOG.md`, `docs/TOOLCHAIN.md` e `docs/decisions/`; documenti governanti preservati | Policy manuale repo-specifica | PR `max23468/DocMolder#166` mergiata; release/deploy non eseguiti perché docs-only | GitHub molto completo, manutenzione, VPS workflows | preflight publish, hygiene, CI GitHub docs-only | Completata: prossimo solo debito reale |
| FiscalBay | Operativo Telegram/eBay/VPS, seconda ondata completata | Canonica con `docs/BACKLOG.md`, `docs/TOOLCHAIN.md` e `docs/decisions/`; release/operations preservati | `scripts/release_now.sh`, workflow di rilascio manuale locale | PR `max23468/FiscalBay#78` mergiata; fix deploy pubblicato; release/deploy non eseguiti | Workflow allowlist, inbox Codex, PR title; Python `3.13` baseline unica dopo il riallineamento toolchain | `ci_verify`, workflow allowlist, shell syntax e GitHub checks | Completata: prossimo solo debito reale |
| GLM | Web app Cloudflare Pages | Allineata ad Atlas con documenti canonici | `npm run release`, package version | Cloudflare Pages solo su richiesta | CI + Codex inbox, PR template, issue template, PR title | Test, build, smoke, deploy doctor | Completata prima passata: resta scelta debito reale |
| SendChimp | Runtime Next.js iniziale / MVP manuale con primo allineamento Atlas completato | Canonica in `docs/` con roadmap, index, backlog e toolchain; `docs/context.md` resta handoff | SemVer locale previsto; release runtime da governare prima di uso produttivo | Pubblicazione GitHub e Vercel automatico completati; nessun invio WhatsApp automatico | Inbox, docs hygiene, PR title; PR `max23468/SendChimp#20` mergiata | `npm run verify`, `git diff --check`, `npm run release:dry-run`; React Doctor dopo release minor applicabile | Scegliere prossimo debito reale: import campagna Mailchimp, UI anteprima/copia o hardening multi-tenant/Auth |
| SyncBay | Scaffold runtime / MVP Shopify con primo allineamento Atlas completato e release locale 0.6.0 pubblicata | Canonica in `docs/` con roadmap, index, backlog, context e toolchain | `npm run release`, `app/lib/version.ts`; `APP_VERSION=0.6.0` | Pubblicazione GitHub e Vercel automatico completati; no tag/GitHub Release/App Store production | Inbox, template, Dependabot; CI minima; PR `max23468/SyncBay#27`, `#28` e `#29` mergiate | typecheck, lint, build, smoke UI, Prisma validate, audit, React Doctor 100/100 | Scegliere prossimo debito reale: keyset/OAuth eBay o import listing live |
| TRAM | MVP iniziale interno | Documenti governanti consolidati e allineati ad Atlas | SemVer `0.x` con `package.json` come fonte; tag/GitHub Release `v0.2.0` già esistente | GitHub privata; release distinta da deploy; nessun target deploy approvato | Inbox, PR title, quality, repo hygiene | `npm run verify`, test/build/lint | Completata prima passata: resta scelta debito reale |
| Atlas | Docs-first / coordinamento operativo | Canonica in `docs/`, ADR e template | Non applicabile | Repository GitHub privata, no deploy | PR template, issue template minima, PR title check; Codex inbox da riallineare | controllo documenti/link, `git status --short` | Bassa: manca ancora il riallineamento della Codex inbox; workflow GitHub riavviati |
| Sentinel | Monitor operativo Ortix e San Carlo Sviluppo, consolidamento Atlas completato | Canonica in `docs/` con roadmap, index, backlog, context, toolchain e ADR | `package.json` indica `0.1.0`; nessuna GitHub Release | GitHub privata; PR `max23468/Sentinel#1` mergiata; workflow manuale `26369906474` verde e output commit `4b9d151` | Workflow `Sentinel`, PR template, issue template, PR title check; Codex inbox in backlog | `npm test`, `npm run build`, YAML parse, workflow Actions con report e output committati | Completata: prossimo solo osservazione run schedulato o debito reale |

## Source of truth per repo

Questa tabella serve a sapere dove guardare per orientarsi in ogni progetto. Le migrazioni di path sono ammesse solo quando derivano da decisioni approvate, come `docs/ROADMAP.md` e `docs/INDEX.md`.

| Repo | Roadmap | Catalogo docs | Backlog | Contesto/handoff | Decisioni | Release/pubblicazione/deploy |
| --- | --- | --- | --- | --- | --- | --- |
| Pratix | `docs/ROADMAP.md`; `ROADMAP.md` resta rinvio; `docs/memory/roadmap.md` resta memoria operativa | `docs/INDEX.md`; `docs/README.md` resta rinvio | `docs/BACKLOG.md` | `docs/CONTEXT.md`, `docs/memory/README.md` e `docs/memory/*.md` | `docs/decisions/` | `docs/TOOLCHAIN.md`, `docs/guides/versioning-e-release.md`, `docs/guides/deploy.md` |
| DocMolder | `docs/ROADMAP.md`, `docs/MILESTONE_BOARD.md` | `docs/INDEX.md` | `docs/BACKLOG.md` | `docs/CONTEXT.md`, `docs/CODEX_TASK_PACKET.md` | `docs/decisions/`; eventuali registri storici/pending restano come fonti temporanee se presenti | `docs/TOOLCHAIN.md`, `docs/RELEASE_PROCESS.md`, `docs/VERSIONING.md`, `docs/VPS_RUNBOOK.md` |
| FiscalBay | `docs/ROADMAP.md`, `docs/MILESTONE_BOARD.md` | `docs/INDEX.md` | `docs/BACKLOG.md` | `docs/CONTEXT.md` | `docs/decisions/`; `docs/DECISIONS_PENDING.md` come pending temporaneo | `docs/TOOLCHAIN.md`, `docs/RELEASE_POLICY.md`, `docs/OPERATIONS.md`, `docs/RUNBOOK.md` |
| GLM | `docs/ROADMAP.md` | `docs/INDEX.md` | `docs/BACKLOG.md` | `docs/CONTEXT.md` | `docs/decisions/` | `docs/TOOLCHAIN.md`, `docs/guides/versioning-e-release.md`, `docs/guides/cloudflare-pages.md` |
| SendChimp | `docs/ROADMAP.md`; `ROADMAP.md` resta rinvio | `docs/INDEX.md`; `docs/README.md` resta rinvio | `docs/BACKLOG.md` | `docs/context.md` | `docs/decisions/`, `docs/decisions-pending.md` | `docs/TOOLCHAIN.md`, `docs/guides/git-e-pubblicazione.md`, `docs/guides/versioning-e-release.md` |
| SyncBay | `docs/ROADMAP.md`; `ROADMAP.md` resta rinvio | `docs/INDEX.md`; `docs/README.md` resta rinvio | `docs/BACKLOG.md` | `docs/CONTEXT.md` | `docs/decisions/`, `docs/decisions-pending.md` | `docs/TOOLCHAIN.md`, `docs/guides/git-e-pubblicazione.md`, `docs/guides/versioning-e-release.md`, `docs/guides/provisioning-runtime.md` |
| TRAM | `docs/ROADMAP.md` | `docs/INDEX.md` | `docs/BACKLOG.md` | `docs/CONTEXT.md` | `docs/DECISIONS.md` come registro; `docs/decisions/` per ADR puntuali | `docs/TOOLCHAIN.md`, `docs/OPERATIONS.md`; release policy da definire |
| Atlas | `docs/ROADMAP.md` | `docs/INDEX.md` | `docs/BACKLOG.md` | `docs/CONTEXT.md` | `docs/decisions/` | GitHub privata; release/deploy non applicabili |
| Sentinel | `docs/ROADMAP.md` | `docs/INDEX.md` | `docs/BACKLOG.md` | `docs/CONTEXT.md` | `docs/decisions/` | `docs/TOOLCHAIN.md`, `.github/workflows/sentinel.yml`, `package.json` |

Regole:

- `README.md` e `AGENTS.md` devono sempre puntare ai documenti canonici della repo;
- una repo può usare path diversi solo per eccezioni tecniche motivate; roadmap e indice hanno path unico;
- se manca una fonte canonica, il primo intervento documentale deve crearla o dichiararla;
- la migrazione della roadmap a `docs/ROADMAP.md` è una scelta di governance, non una migrazione estetica;
- la migrazione dell’indice a `docs/INDEX.md` è una scelta di governance, non una migrazione estetica;
- la creazione del backlog in `docs/BACKLOG.md` è una scelta di governance, non un archivio di scope implicito;
- le nuove decisioni stabili devono andare in `docs/decisions/`;
- non vanno fatte altre migrazioni di path solo estetiche.

## Standard comune approvato

### A. Contenuti sostanziali per AGENTS.md

Ogni `AGENTS.md` deve integrare in modo granulare, nelle sezioni più adatte alla
repo, questi contenuti sostanziali:

1. Scopo.
2. Priorità delle istruzioni.
3. Identità del progetto.
4. Perimetro, assi di validità e non-obiettivi.
5. Fonti primarie.
6. Workflow operativo prima di lavorare.
7. Branch, worktree e modifiche non proprie.
8. Documentazione, roadmap, backlog, ADR e anti-perdita.
9. Versioning, changelog, release e categorie commit.
10. Pubblicazione, deploy e release.
11. GitHub, PR, merge e Codex feedback inbox.
12. Test e verifiche proporzionate in corsie `veloce`, `standard`, `completa`.
13. UI/React/browser checks quando applicabili.
14. Provider, API, fonti variabili, costi e privacy.
15. Deploy, produzione e verifica live quando applicabili.
16. Sicurezza, privacy, segreti e dati.
17. File generati, temporanei e output applicativi.
18. Pulizia repository.
19. Risposta finale.
20. Definizione di completamento.

La forma e l'ordine restano repo-specifici: non va incollato un blocco comune
Atlas dentro le repo. Le sezioni possono essere più brevi nelle repo docs-first
o non applicabili, ma l'assenza deve essere esplicita quando incide su publish,
release, deploy, verifiche, sicurezza o dati.

### A.1 Root e docs

Standard approvato:

| Posizione | Deve contenere | Non deve contenere |
| --- | --- | --- |
| Root | ingresso, istruzioni agenti, configurazioni, manifest, lockfile, codice, script, test, config deploy | roadmap, ADR, backlog, piani, report, guide lunghe, runbook estesi |
| `docs/` | roadmap, indice, contesto, decisioni, guide, governance, runbook, sicurezza, privacy, brand, glossario, report | configurazioni richieste dai tool, sorgente runtime, lockfile |
| `.github/` | workflow, template, automazioni GitHub | documentazione prodotto generale |

La root deve essere leggibile in pochi secondi. `docs/` deve essere il luogo in cui il progetto conserva memoria, decisioni e profondità.

### B. Catalogo documentale minimo

| Tipo documento | Scopo | Obbligo |
| --- | --- | --- |
| `README.md` | ingresso rapido | sempre |
| `AGENTS.md` | regole operative Codex | sempre |
| `CHANGELOG.md` | storico release o cambi rilevanti | se c’è versioning |
| `docs/ROADMAP.md` | priorità e prossimi passi | sempre |
| `docs/INDEX.md` | catalogo documenti | sempre |
| `docs/BACKLOG.md` | idee, debiti, bug e attività non ancora promosse | sempre |
| `docs/TOOLCHAIN.md` | runtime, package manager, versioni minime e lockfile | sempre se ci sono tool o dipendenze |
| `docs/CONTEXT.md` | handoff per nuove chat | sempre |
| `docs/decisions/` | decisioni stabili | se il progetto ha governance viva |
| guida Git/pubblicazione | cosa significa pubblicare | sempre se repo GitHub |
| guida versioning/release | come si rilascia | se c’è release |
| guida deploy/operations | runtime, health, rollback | se c’è produzione |
| security/privacy | dati, segreti, provider | se tratta dati o API |

### C. Semantica comune dei comandi utente

| Formula utente | Significato comune | Eccezioni |
| --- | --- | --- |
| `procedi` | continua nel perimetro già concordato | se rischioso, chiedere chiarimento |
| `pubblica` | porta il lavoro nel canale GitHub/canonico previsto, con verifiche e inbox Codex | target e comando dipendono dalla repo |
| `deploya` | aggiorna il runtime dichiarato dalla repo, con runbook e verifica finale | non applicabile se la repo non ha runtime |
| `rilascia` | crea/chiude versione secondo policy, con changelog/tag/release se previsti | non applicabile se la repo non ha release policy |
| `pubblica tutto` | esegue protocollo completo: publish, eventuale release, eventuale deploy, verifica e cleanup | non inventa runtime o release se assenti |
| `chiudi la fase` | verifica stato, docs, release/deploy se previsti | non inventare produzione se repo non la ha |
| `solo analisi` | nessuna modifica codice | ok documenti se richiesti esplicitamente |

### D. Roadmap standard

Formato standard:

| Stato | Significato |
| --- | --- |
| `Ora` | lavoro attuale o immediatamente successivo |
| `Prossimo` | backlog prioritario |
| `Più avanti` | futuro reale ma non attuale |
| `Bloccato` | dipende da decisione, accesso, provider o dato esterno |
| `Fatto` | completato, da tenere solo se serve storico breve |

Regole:

- non usare la roadmap come changelog;
- non usare la roadmap come dump di idee;
- rimuovere o archiviare completati vecchi;
- collegare decisioni stabili ad ADR;
- collegare lavori pubblicati a changelog/release quando pertinente.

### E. Manutenzione periodica

Frequenza approvata:

- mensile, per controllo leggero di tutte le repo;
- obbligatoria prima di `publish`, `deploy` o `release`.

Checklist comune:

1. Stato Git locale.
2. Worktree e branch stale.
3. PR aperte.
4. Codex feedback inbox, obbligatoria prima di PR ready/merge/publish/deploy/release.
5. Workflow falliti.
6. Dependabot e security alerts.
7. Changelog/release pendenti.
8. Stato deploy/runtime.
9. Roadmap/backlog obsoleti.
10. Docs di contesto aggiornate.
11. Toolchain/versioni.
12. Vincoli repo-specifici.

## Baseline per nuovi progetti

Questa sezione vale per ogni nuova repository.

Quando parte un nuovo progetto, non deve nascere solo con codice o appunti sparsi. Deve nascere con un set minimo completo, proporzionato alla fase, che permetta a Codex e al maintainer di capire subito cosa fare, cosa non fare, come verificare e come pubblicare.

### Principio

Un nuovo progetto può essere minimale, ma non deve essere ambiguo.

Minimale significa:

- pochi documenti;
- regole brevi;
- test proporzionati;
- nessun processo di release artificiale;
- nessun deploy inventato.

Non ambiguo significa:

- perimetro dichiarato;
- prossimo passo visibile;
- decisioni stabili tracciate;
- regole GitHub presenti;
- verifiche minime definite;
- publish, deploy e release distinti;
- dati e segreti gestiti consapevolmente.

### Starter kit obbligatorio

Ogni nuova repo deve partire almeno con:

| File/area | Scopo | Note |
| --- | --- | --- |
| `README.md` | ingresso umano al progetto | deve spiegare cosa fa, stato, stack e comandi base |
| `AGENTS.md` | regole operative per Codex | deve essere letto prima di modifiche non banali |
| `docs/ROADMAP.md` | direzione e prossimi passi | con sezioni `Ora`, `Prossimo`, `Più avanti`, `Bloccato` |
| `docs/INDEX.md` | catalogo documentale | deve linkare i documenti canonici |
| `docs/HEALTH.md` | snapshot health dei progetti coordinati | per meta-repo o manutenzione periodica, non per ogni app |
| `docs/BACKLOG.md` | idee, debiti e attività non ancora scelte | non deve sostituire la roadmap |
| `docs/TOOLCHAIN.md` | runtime, tool, package manager, versioni minime | deve distinguere baseline ed eccezioni |
| `docs/CONTEXT.md` o equivalente | handoff per nuove chat | utile anche se breve |
| `docs/decisions/0001-*.md` | prima decisione stabile | stack, perimetro o modello operativo |
| guida Git/pubblicazione | cosa significa pubblicare | anche solo una sezione nel README all’inizio |
| guida versioning/release | come si gestiscono versioni | può dichiarare “non ancora applicabile” |
| security/privacy | dati, segreti, provider | obbligatorio se tratta dati reali o API |
| `.github/` baseline | PR/commenti/qualità | proporzionata alla fase |

### Domande iniziali da fissare

Prima o durante la creazione della repo, il progetto deve rispondere a queste domande:

1. Qual è il problema concreto che risolve?
2. Qual è il non-obiettivo più importante?
3. È docs-first, MVP locale, runtime attivo o produzione?
4. Qual è lo stack iniziale e perché?
5. Quali dati tratta?
6. Usa provider esterni o API variabili?
7. Cosa significa “pubblica” in questa repo?
8. Esiste un deploy? Se sì, dove e con quale runbook?
9. Esiste una release? Se sì, con quale versioning?
10. Quali controlli minimi devono passare prima di considerare chiuso un lavoro?
11. Quale documento deve leggere Codex per orientarsi?
12. Qual è il prossimo passo operativo reale?

### Baseline GitHub

Per una nuova repo, il livello minimo approvato è:

- repository su GitHub fin dall’inizio se il progetto non è solo bozza locale;
- branch principale dichiarato;
- PR template;
- issue template minima;
- issue o inbox per commenti Codex;
- workflow `Codex PR comments`;
- workflow `pr-title.yml` o controllo equivalente del titolo PR;
- Dependabot come standard pieno quando ci sono dipendenze o manifest compatibili;
- branch protection solo quando il progetto diventa operativo o condiviso.

### Baseline verifiche

Le verifiche devono nascere proporzionate alla fase.

| Fase | Verifiche minime |
| --- | --- |
| docs-first | controllo link/lingua/struttura se disponibile |
| MVP locale | lint/typecheck/test essenziali |
| runtime attivo | build più smoke minimo |
| produzione | build, test, smoke, health, rollback/runbook |
| operativo con release | controlli release, changelog/versioning, CI verde |

Regola: non introdurre test simbolici solo per dire che esistono. Meglio pochi check reali e mantenibili.

### Baseline toolchain e versioni

Ogni nuova repo deve dichiarare la propria toolchain in modo esplicito.

File e campi obbligatori quando applicabili:

- `docs/TOOLCHAIN.md`: fonte leggibile per runtime, tool, versioni minime, package manager, lockfile ed eccezioni;
- `package.json` con `engines` e `packageManager` per progetti Node/npm;
- `.node-version` per progetti Node;
- `package-lock.json` per progetti npm;
- `pyproject.toml` con `requires-python` per progetti Python;
- `.python-version` per progetti Python quando utile al setup locale;
- lockfile Python se il gestore scelto lo prevede;
- note su tool esterni richiesti, per esempio Vercel CLI, Wrangler, gh, Supabase CLI, Docker o Make.

Il criterio approvato è usare la versione più nuova ragionevolmente supportata dal progetto, non una versione vecchia per prudenza generica.

Distinzione:

- per runtime con linea LTS, usare la latest LTS supportata dallo stack;
- per runtime senza LTS equivalente, usare la latest stable compatibile con dipendenze, deploy e strumenti;
- non usare una release Current/preview solo perché è la più recente;
- per repo esistenti, rispettare i guardrail attuali finché non c’è decisione esplicita di upgrade.

Baseline comune per nuovi progetti:

| Area | Baseline |
| --- | --- |
| JavaScript/TypeScript | latest Node LTS supportata dallo stack; al momento Node `24.x` |
| npm | latest npm stabile compatibile con la Node LTS scelta, con `packageManager` dichiarato |
| Lockfile JS | `package-lock.json` |
| Python | latest Python stable compatibile con dipendenze, deploy e tooling |
| Lint/typecheck/test | comando esplicito nel manifest o nel runbook |
| Version manager | file dichiarativo in root quando utile: `.node-version` o `.python-version` |
| Tool esterni | versione minima o canale stabile documentato in `docs/TOOLCHAIN.md` |

Regole:

- preferire la versione più nuova supportata, non la più vecchia ancora supportata;
- per Node distinguere sempre `latest Current`, `latest LTS` e `baseline del progetto`;
- per Python verificare dipendenze, deploy e tool prima di adottare l’ultima major stabile;
- non fissare una versione unica di React, Vite, Next, TanStack, Wrangler o altre librerie applicative per tutte le repo: dipendono dallo stack;
- fissare invece runtime, package manager e lockfile;
- ogni repo deve pinning o range esplicito nel manifest;
- gli aggiornamenti di toolchain devono passare da roadmap/backlog o ADR se cambiano vincoli stabili;
- le repo esistenti possono restare temporaneamente su baseline diversa se documentata;
- le eccezioni vanno dichiarate in `docs/TOOLCHAIN.md` e, se strutturali, in ADR.

Snapshot attuale da normalizzare gradualmente:

| Repo | Stato toolchain rilevato | Allineamento |
| --- | --- | --- |
| Pratix | Node `24.x`, npm `>=11 <12`, `packageManager: npm@11.14.1` | già allineata alla baseline JS |
| SendChimp | Node `>=24 <27`, npm `>=11 <12`, `packageManager: npm@11.14.1` | già allineata alla baseline JS |
| SyncBay | `.node-version` = `24.16.0`, `engines.node >=24.15 <25`, Docker `node:24.16.0-alpine` | allineata alla baseline Node 24 con floor esplicito |
| GLM | package npm presente, engines/packageManager non dichiarati | da completare |
| TRAM | package npm presente, engines/packageManager non dichiarati | da completare |
| DocMolder | Python `>=3.11` | già allineata alla baseline Python |
| FiscalBay | Python `3.13` in manifest, lint/typecheck, CI, package build e runtime VPS | allineata alla baseline Python corrente |

Nota di lettura:

- Node `24.x` è scelto perché è la latest LTS supportata al momento della ricognizione, non perché sia la latest Current assoluta;
- npm deve seguire la latest stabile compatibile con la Node LTS scelta, senza imporre una patch uguale in tutte le repo;
- Python per nuovi progetti deve puntare alla latest stable compatibile con dipendenze e deploy, non a `>=3.11` per default conservativo;
- FiscalBay usa Python `3.13` come baseline unica dopo l'upgrade completo.

Guardrail per repo esistenti:

- la baseline Python per nuovi progetti è latest stable compatibile con dipendenze, deploy e tooling;
- FiscalBay non deve abbassare il supporto sotto Python `3.13` senza decisione
  esplicita e aggiornamento coerente di manifest, CI, toolchain e policy;
- i controlli di FiscalBay devono restare compatibili con il vincolo dichiarato
  in `pyproject.toml`.

### Baseline versioning, publish e release

Ogni nuova repo deve dichiarare subito una di queste condizioni:

- versioning non applicabile per ora;
- versione locale senza release pubblica;
- changelog manuale;
- SemVer locale;
- automazione di release documentata manuale o tool-specifica;
- release GitHub;
- deploy senza release;
- deploy più release.

La cosa importante non è scegliere subito il processo più maturo. È non lasciare il significato di versione, pubblicazione e rilascio implicito.

### Baseline documentale per fase

| Fase | Documenti sufficienti |
| --- | --- |
| Idea/docs-first | `README.md`, `AGENTS.md`, `docs/ROADMAP.md`, `docs/INDEX.md`, `docs/BACKLOG.md`, `docs/TOOLCHAIN.md`, prima decisione |
| MVP locale | aggiungere guida dev, verifiche, dati, backlog |
| Runtime attivo | aggiungere operations/deploy, env, security/privacy |
| Produzione | aggiungere runbook, health, rollback, release policy |
| Stabilizzazione | aggiungere manutenzione periodica e matrice qualità |

### Criteri di passaggio di fase

Il passaggio di fase deve essere esplicito.

Esempi:

- da docs-first a MVP: esiste uno scope implementabile e verificabile;
- da MVP a runtime attivo: esiste un’app/servizio avviabile con comandi documentati;
- da runtime attivo a produzione: esistono deploy, health, segreti, rollback e dati gestiti;
- da produzione a operativo con release: esistono versioning, changelog, release policy e smoke;
- da operativo a stabilizzazione: esiste manutenzione periodica.

### Template operativo iniziale

Per creare un nuovo progetto, l’ordine approvato è:

1. definire nome, perimetro e non-obiettivi;
2. scegliere fase iniziale;
3. creare `README.md`;
4. creare `AGENTS.md`;
5. creare `docs/ROADMAP.md`, `docs/INDEX.md`, `docs/BACKLOG.md` e `docs/TOOLCHAIN.md`;
6. registrare la prima decisione stabile;
7. definire verifiche minime;
8. definire toolchain e versioni minime;
9. definire GitHub baseline;
10. definire publish/deploy/release, anche come “non applicabile per ora”;
11. dichiarare dati, privacy, provider e segreti;
12. popolare il primo backlog;
13. fare il primo controllo di coerenza.

### Definizione di pronto per nuova repo

Una nuova repo è pronta per il lavoro operativo quando:

- una nuova chat può leggerla senza contesto orale;
- il prossimo passo è scritto;
- le cose da non fare sono chiare;
- il comando di verifica minimo esiste o è dichiarato non applicabile;
- runtime, package manager e versioni minime sono dichiarati;
- GitHub è coerente con la fase;
- publish, deploy e release non sono ambigui;
- i dati sensibili sono riconosciuti;
- Codex sa dove lasciare o leggere commenti operativi;
- la roadmap non è vuota o generica.

## Definizione di pronto per intervenire su una repo esistente

Prima di modificare una repo esistente, l’intervento è pronto solo se sono chiari:

- stato Git locale;
- eventuali modifiche non proprie;
- branch/worktree da usare;
- `AGENTS.md` e documenti che indica;
- source of truth della repo;
- roadmap/backlog rilevanti;
- toolchain e versioni minime;
- commenti Codex o PR review pendenti;
- comandi minimi di verifica;
- impatto su changelog, versioning, release o deploy;
- dati sensibili o provider coinvolti;
- criterio di completamento;
- prossimo passo se i controlli falliscono.

Checklist minima:

1. eseguire `git status --short`;
2. leggere `AGENTS.md`;
3. leggere i documenti canonici indicati dalla source of truth;
4. censire funzioni, documenti, runbook, workflow, policy e comportamenti repo-specifici non previsti dal piano Atlas;
5. classificare gli extra: mantenere specifici, promuovere ad Atlas, sostituire con pattern più maturo, mettere in backlog o rimuovere solo se duplicati/superati;
6. cercare commenti Codex/PR review actionable;
7. identificare test/verifiche proporzionati;
8. dichiarare se publish, deploy o release sono fuori scope;
9. non toccare modifiche non proprie;
10. chiudere con riepilogo, verifiche e rischi residui.

Se uno di questi punti è ambiguo e l’ambiguità può cambiare scope, rischio o pubblicazione, bisogna chiedere chiarimento prima di procedere.

## Coordinamento operativo nella fase repo-per-repo

Il piano centrale decide lo standard comune. Gli interventi sulle repo coordinate
devono applicarlo senza ridefinirlo durante la scrittura.

Uso approvato:

- un coordinamento centrale mantiene piano, decisioni e coerenza;
- si lavora in scrittura su una sola repo per volta;
- la prima fase resta read-only: ricognizione, gap, rischi e proposta;
- la scrittura parte solo dopo standard approvati e repo assegnata;
- ogni intervento deve rispettare `AGENTS.md` della repo e la source of truth del piano;
- ogni intervento chiude con file toccati, contenuti migrati, eventuali contenuti rimossi, verifiche eseguite, rischi residui e prossimi passi.

Output standard richiesto:

1. repo o area analizzata;
2. documenti letti;
3. gap rispetto al piano;
4. modifiche proposte;
5. file da toccare;
6. contenuti da preservare;
7. contenuti eventualmente da rimuovere solo se approvati;
8. rischi o eccezioni;
9. verifiche da eseguire;
10. eventuale patch o piano patch;
11. stato finale e handoff.

Limiti:

- non cambiare lo standard comune durante la fase applicativa;
- non normalizzare vincoli repo-specifici motivati;
- non eliminare contenuti per uniformità senza decisione esplicita;
- non introdurre deploy, release o workflow non previsti dalla repo;
- non risolvere conflitti di governance senza tornare al piano centrale;
- non usare output intermedi come fonte primaria se contraddicono `AGENTS.md`, documenti canonici o decisioni approvate.

## Registro vincoli repo-specifici

I vincoli repo-specifici non mettono una repo fuori standard. Servono a dichiarare cosa va rispettato mentre si applica lo standard comune.

| Repo | Vincolo | Motivo | Cosa non fare |
| --- | --- | --- | --- |
| Pratix | SaaS Vercel/Supabase con UI italiana e glossary rigoroso | Prodotto gestionale leggero per avvocati freelance | non spostare verso VPS, Telegram o Cloudflare |
| DocMolder | Telegram-first con release repo-specifica e VPS | Utility documentale operativa, non dashboard web | non trasformare in web app o in un processo release manuale generico scollegato dal runbook DocMolder |
| FiscalBay | Dati fiscali solo se presenti nelle API eBay; Python `3.13` come baseline unica; deploy/release via script locali/VPS | Rischio di dedurre informazioni non disponibili o usare canali operativi sbagliati | non inventare tax data, non abbassare la baseline Python senza decisione, non introdurre workflow GitHub Actions non previsto |
| GLM | Cloudflare Pages e dati gara allegati | Simulatore web legato a gara/documenti specifici | non usare Vercel/Supabase come default |
| SendChimp | Runtime Next.js/Vercel/Neon per MVP manuale | Perimetro operativo ancora manuale e vincolo free-tier | non introdurre invii reali, non usare Supabase nel primo scaffold, non creare risorse a pagamento |
| SyncBay | Shopify app con eBay come sorgente catalogo | Perimetro prodotto specifico | non allargarla a marketplace generico bidirezionale |
| TRAM | Evidence-first e AI governata/free-first | Documenti gara e output sensibili | non anticipare V2/V3 o inviare dati a provider senza policy |
| Atlas | Meta-progetto docs-first su GitHub privata | Coordinamento, non prodotto applicativo | non trasformarlo in runtime o dashboard senza decisione |
| Sentinel | Monitor siti pubblici con primo profilo Ortix | Output applicativi committabili dal workflow; credenziali email via secret; HTML completo vietato | non trattare output `data/`, `snapshots/`, `reports/` come rumore da ignorare o segreti da copiare |

## Vincoli specifici per repo

### Pratix

Non va spostata verso VPS, Cloudflare o Telegram.

Standard specifico:

- TanStack Start;
- Vercel;
- Supabase;
- UI italiana;
- token semantici;
- glossary rigoroso;
- smoke a11y proporzionato;
- React Doctor obbligatorio dopo ogni release minor `X.Y.Z`.

### DocMolder

Non va trasformata in web app o dashboard-first.

Standard specifico:

- Telegram-first;
- VPS;
- release manuale repo-specifica;
- webhook privato GitHub -> VPS;
- documenti utente trattati come sensibili;
- branch/worktree separati quando ci sono filoni paralleli.

### FiscalBay

Non dedurre dati fiscali eBay non presenti.

Standard specifico:

- Telegram/eBay-first;
- runtime VPS documentato a Python `3.13`;
- Python `3.13` come baseline unica per manifest, ruff, mypy, CI e VPS;
- non abbassare il supporto a minor version precedenti senza decisione esplicita;
- VPS FiscalBay specifica;
- deploy fuori da GitHub Actions;
- `scripts/deploy_now.sh`;
- `scripts/release_now.sh`;
- GitHub Actions solo controlli conservativi.

### GLM

Non usare Vercel o Supabase.

Standard specifico:

- Cloudflare Pages;
- dati e fonti gara tracciabili;
- allegati Git LFS non modificati senza richiesta;
- changelog mostrato nel frontend;
- deploy solo con `npm run deploy:cloudflare`.

### SendChimp

Non introdurre invio produttivo prima di decisione esplicita.

Standard specifico:

- runtime Next.js/React iniziale;
- Vercel con Functions Frankfurt;
- Neon Free/Postgres 17 in Frankfurt;
- Neon Auth per protezione route/API;
- nessun Supabase nel primo scaffold;
- vincolo free-tier;
- MVP ultimo miglio manuale;
- nessun invio WhatsApp reale;
- nessuna integrazione produttiva Meta/Mailchimp/Shopify senza piano.

### Atlas

Non trasformarlo in prodotto applicativo senza decisione esplicita.

Standard specifico:

- meta-progetto docs-first;
- repository GitHub privata;
- nessun runtime;
- nessuna release o deploy;
- baseline GitHub leggera.

### Sentinel

Standard specifico:

- repo GitHub privata `max23468/Sentinel` su `main`;
- runtime Node.js/TypeScript tracciato;
- CLI `sentinel`, configurazione YAML e test Vitest;
- monitor Ortix e San Carlo Sviluppo;
- output `data/`, `snapshots/` e `reports/` applicativi e committabili dal workflow;
- consolidamento Atlas completato con PR `max23468/Sentinel#1`;
- ultimo stato verificato: output commit `4b9d151 chore: update sentinel outputs`;
- ultimo run manuale visto: `26369906474`, verde dopo test, build, scan, commit output e controllo finale;
- report `reports/ortix-20260524T185555Z.md`: 0 cambiamenti, 33 avvisi 404, nessuna email richiesta;
- report `reports/sancarlo-sviluppo-20260524T185745Z.md`: 0 cambiamenti, 0 problemi, nessuna email richiesta;
- rispettare `robots.txt`;
- non committare segreti o password email;
- non salvare HTML completo;
- prossima azione: osservare il prossimo run schedulato e promuovere solo problemi reali da report/log.

### SyncBay

Non trasformarla in marketplace bidirezionale generico.

Standard specifico:

- Shopify app;
- eBay sorgente catalogo;
- Vercel/Supabase previsti ma production non attiva;
- release locale senza tag/deploy;
- App Store solo dopo decisione.

### TRAM

Non anticipare V2/V3 e non inviare documenti sensibili a provider esterni senza policy.

Standard specifico:

- evidence-first;
- AI free-first e governata;
- documenti gara sensibili;
- no release/deploy finché policy non esiste;
- documenti governanti centrali.

## Rischi da evitare

### Uniformare troppo

Rischio: trasformare progetti diversi in copie dello stesso stack tecnico.

Correzione: semantica e protocollo di publish/deploy/release sono comuni; provider, runtime, target e comandi restano repo-specifici.

### Uniformare troppo poco

Rischio: ogni repo continua a richiedere un ricordo mentale diverso, con spreco di tempo e maggiore probabilità di errori.

Correzione: ogni repo deve avere gli stessi punti di orientamento: `AGENTS.md`, catalogo documentazione, roadmap/backlog, regole di pubblicazione, verifiche e handoff.

### Confondere roadmap e backlog

Rischio: ogni idea diventa implicitamente scope aperto.

Correzione: `docs/ROADMAP.md` dice dove si sta andando; `docs/BACKLOG.md` raccoglie possibilità, debiti, bug e idee non ancora scelte.

### Confondere publish, deploy e release

Rischio: chiudere un lavoro come “pubblicato” senza che sia davvero arrivato nel canale previsto dalla repo.

Correzione: il piano definisce significato e protocollo comuni; ogni repo dichiara solo target, comandi e condizioni di applicabilità.

### Appesantire repo mature

Rischio: peggiorare Pratix, DocMolder o FiscalBay aggiungendo burocrazia inutile.

Correzione: sulle repo mature si rifinisce, non si ricostruisce.

### Normalizzare repo immature come se fossero production

Rischio: creare processi di release/deploy artificiali su progetti che non sono ancora pronti.

Correzione: su GLM, TRAM, SyncBay, SendChimp e Sentinel va dichiarata la maturità operativa senza trattare nessuna repo come fuori perimetro. SendChimp ha già runtime iniziale; Sentinel va consolidata come baseline runtime operativa, non più censita come scaffold senza remote.

## Criteri di completamento del piano

Il piano può considerarsi pronto quando:

- ogni repo ha una classificazione chiara di maturità;
- ogni differenza tecnica importante è dichiarata come vincolo repo-specifico motivato;
- i punti comuni sono abbastanza precisi da diventare patch documentali;
- le migrazioni hanno una regola anti-perdita contenuto;
- le decisioni approvate sono separate dalle azioni operative da eseguire;
- la roadmap è riconosciuta come elemento centrale del coordinamento;
- publish, deploy e release non sono usati come sinonimi;
- Codex inbox e commenti PR hanno una regola comune;
- test e verifiche sono proporzionati alla repo;
- gli interventi sono ordinati per priorità e rischio;
- il piano non obbliga a modificare codice applicativo;
- esiste una baseline riusabile per aprire nuovi progetti già coordinati;
- esiste una checklist di pronto intervento per le repo esistenti;
- esiste una mappa source of truth per orientarsi senza memoria orale;
- è definito come coordinare gli interventi senza perdere contenuti o coerenza centrale.

## Sequenza operativa di intervento

### Fase 1 - Standard base

Obiettivo: definire il modello comune senza modificare flussi tecnici.

Azioni:

1. definire contenuti sostanziali comuni per `AGENTS.md`, da integrare in modo
   granulare nelle sezioni esistenti delle repo;
2. creare checklist comune documentazione;
3. definire semantica comune di `pubblica/deploya/rilascia`;
4. definire standard roadmap/backlog/ADR;
5. definire baseline per nuovi progetti;
6. definire standard risposta finale e prossimi passi.

### Fase 2 - Repo meno allineate

Priorità:

1. GLM: completato primo allineamento Atlas; scegliere solo debiti prodotto/tecnici reali.
2. TRAM: completato primo allineamento Atlas; scegliere solo debiti prodotto/tecnici reali.
3. SyncBay: completato primo allineamento Atlas, chiusa inbox e pubblicata release locale 0.6.0; prossimo solo debito reale, per esempio keyset/OAuth eBay.
4. SendChimp: completato primo allineamento Atlas, chiusa inbox e preservati runtime iniziale, decisioni MVP manuale e vincolo free-tier; prossimo solo debito reale, per esempio import campagna Mailchimp o UI anteprima/copia.
5. Sentinel: completata con PR `max23468/Sentinel#1`; documenti canonici, baseline GitHub minima e workflow manuale verde.

### Fase 3 - Repo mature

Priorità:

1. Pratix: completata con PR `max23468/Pratix#156`; prossimo solo debito reale, senza appesantire.
2. DocMolder: completata con PR `max23468/DocMolder#166`; mantenere flusso manuale/VPS.
3. FiscalBay: completata con PR `max23468/FiscalBay#78`; mantenere deploy locale/VPS e baseline Python `3.13` allineata.

### Fase 4 - Qualità e manutenzione

Azioni:

1. introdurre matrice di conformità periodica;
2. applicare `pr-title.yml` o controllo equivalente dove manca;
3. applicare `CODEOWNERS` solo dove aggiunge controllo reale;
4. introdurre React Doctor come gate nelle app React prima della prima release minor applicabile;
5. creare check periodico “project health” per tutte le repo.

## Matrice operativa repo-per-repo

Questa matrice traduce il piano in interventi applicabili. Non sostituisce `AGENTS.md` delle singole repo: prima di ogni patch va comunque letto il contesto reale della repo e verificato `git status --short`.

Regole comuni per ogni intervento:

1. leggere `AGENTS.md`;
2. controllare stato Git e modifiche non proprie;
3. aggiornare link da `README.md` e `AGENTS.md` verso i documenti canonici;
4. fare discovery degli extra repo-specifici già maturi: funzioni, documenti, runbook, workflow, policy e comportamenti;
5. classificare gli extra prima di normalizzare: mantenere, promuovere ad Atlas, sostituire, mettere in backlog o rimuovere solo se duplicati/superati;
6. fare inventario dei contenuti da migrare prima di spostare o fondere documenti;
7. evitare duplicati con stesso ruolo;
8. non eliminare contenuti salvo decisione esplicita o assorbimento verificato;
9. mantenere rinvii temporanei quando serve preservare tracciabilità;
10. controllare `Codex feedback inbox`;
11. eseguire verifiche proporzionate;
12. chiudere con riepilogo, verifiche, contenuti migrati/rimossi e rischi residui.

### Prima ondata

| Repo | Priorità | File e documenti | GitHub/processo | Verifiche | Vincoli |
| --- | --- | --- | --- | --- | --- |
| GLM | completata | Primo allineamento completato con `docs/INDEX.md`, `docs/ROADMAP.md`, `docs/BACKLOG.md`, `docs/CONTEXT.md`, `docs/TOOLCHAIN.md`, indice decisioni e `docs/decisions/template.md`; da riallineare alla regola Atlas 0004 sui basename Markdown | PR template, issue template minima e `pr-title.yml` aggiunti; repo GitHub corrente `max23468/GLM`; Codex inbox verificata senza thread actionable | Per il pilot documentale: `git diff --check` e CI GitHub passata; test/build/smoke restano per cambi runtime | Cloudflare Pages; non introdurre Vercel/Supabase; non perdere pattern GLM maturi come logica simulatore, changelog frontend e runbook Cloudflare |
| TRAM | completata | Roadmap migrata in `docs/ROADMAP.md`; creati `docs/BACKLOG.md`, `docs/TOOLCHAIN.md`, template ADR con basename unico; mantenuto `docs/DECISIONS.md` come registro | Baseline GitHub già presente; PR `max23468/TRAM#7` mergiata | `npm run verify`; Quality, Repo Hygiene, PR Title e Codex sync passati | Evidence-first; release SemVer `0.x` attiva; nessun deploy finché manca target approvato; React Doctor prima della prima release minor applicabile |
| SyncBay | completata | Roadmap migrata in `docs/ROADMAP.md`; creati `docs/INDEX.md`, `docs/BACKLOG.md`, `docs/TOOLCHAIN.md`; `docs/CONTEXT.md` canonico; `ROADMAP.md` e `docs/README.md` restano rinvii | PR `max23468/SyncBay#27`, `#28` e `#29` mergiate; Codex inbox senza thread actionable; Docker Node allineato a engine; release locale 0.6.0 pubblicata | PR #27: `npm run typecheck`, `npm run lint`, `npm run build`, `npm run quality:react-doctor` 100/100, `npm run release:dry-run`, `git diff --check`; PR #28: `git diff --check`, `npm run release:dry-run`, Vercel pass; PR #29: typecheck, lint, build, React Doctor 100/100, audit, smoke UI, Prisma validate, release dry-run, Vercel pass | Shopify app; no marketplace generico; no tag/GitHub Release/App Store production finché non deciso; prossimo debito possibile: keyset/OAuth eBay |
| SendChimp | completata | Roadmap migrata in `docs/ROADMAP.md`; creati `docs/INDEX.md`, `docs/BACKLOG.md`, `docs/TOOLCHAIN.md`; `docs/context.md` mantenuto come handoff canonico; `ROADMAP.md` e `docs/README.md` restano rinvii | PR `max23468/SendChimp#20` mergiata; Codex inbox senza thread actionable; chiuso P1 su fallback `DATABASE_URL_UNPOOLED`; Vercel automatico passato | `npm run verify`, `git diff --check`, `npm run release:dry-run`; Docs hygiene su main passato | Runtime Next.js/MVP manuale; nessun invio reale; nessun Supabase nel primo scaffold; nessun tag/GitHub Release, deploy manuale o provider/billing nuovo |
| Sentinel | completata | Creati `docs/ROADMAP.md`, `docs/INDEX.md`, `docs/BACKLOG.md`, `docs/TOOLCHAIN.md`, `docs/CONTEXT.md`, indice decisioni, template ADR e ADR su GitHub Actions runtime operativo MVP; da riallineare alla regola Atlas 0004 sui basename Markdown | PR `max23468/Sentinel#1` mergiata; aggiunti PR template, issue template e `pr-title.yml`; Codex inbox lasciata in backlog | `git diff --check`, YAML parse, `npm test`, `npm run build`, PR title check, workflow manuale `26369906474` verde con output commit `4b9d151` | Non committare segreti/email; rispettare `robots.txt`; non salvare HTML completo; preservare output applicativi tracciabili |

### Seconda ondata

| Repo | Priorità | File e documenti | GitHub/processo | Verifiche | Vincoli |
| --- | --- | --- | --- | --- | --- |
| Pratix | completata | `ROADMAP.md` rinvia a `docs/ROADMAP.md`; `docs/README.md` rinvia a `docs/INDEX.md`; creati `docs/BACKLOG.md`, `docs/TOOLCHAIN.md` e `docs/CONTEXT.md`; release patch `1.11.15` | PR `max23468/Pratix#156` mergiata; workflow maturo preservato | Test mirato, prepush guard completo, GitHub checks e `publish:finish` production su `/` e `/novita` | SaaS Vercel/Supabase; UI italiana; glossary rigoroso; non appesantire |
| DocMolder | completata | Creati `docs/BACKLOG.md`, `docs/TOOLCHAIN.md`, indice decisioni e template ADR; documenti storici preservati; da riallineare alla regola Atlas 0004 sui basename Markdown | PR `max23468/DocMolder#166` mergiata; release/deploy saltati perché docs-only | Manutenzione GitHub, preflight publish, test hygiene, check Codex inbox e CI GitHub docs-only | Telegram-first; VPS; Python `3.13` preferito ma manifest `>=3.11`; documenti utente sensibili; non trasformare in web app |
| FiscalBay | completata | Creati `docs/BACKLOG.md`, `docs/TOOLCHAIN.md`, indice decisioni e template ADR; backlog condizionato estratto dalla roadmap; da riallineare alla regola Atlas 0004 sui basename Markdown | PR `max23468/FiscalBay#78` mergiata; thread Codex P1 risolto; deploy/release saltati perché non impliciti | `bash -n deploy/linux-setup.sh`, `git diff --check`, workflow allowlist, `bash scripts/ci_verify.sh`, GitHub checks | Telegram/eBay/VPS; non dedurre dati fiscali; Python `3.13` baseline unica dopo il riallineamento toolchain |

### Artefatti comuni da produrre

| Artefatto | Scopo | Dove vive |
| --- | --- | --- |
| `README.md` di Atlas | guida d’uso dei template e del piano | `/Users/Matteo/Progetti/Atlas` |
| Piano principale | decisioni approvate, matrice repo e ordine operativo | `/Users/Matteo/Progetti/Atlas/piano-coordinamento-progetti.md` |
| Template `AGENTS.md` | struttura comune adattabile per ogni repo | `AGENTS.template.md` |
| Checklist implementazione | controllo dei file canonici, link, GitHub e verifiche | `CHECKLIST-IMPLEMENTAZIONE.md` |
| Template `docs/INDEX.md` | catalogo documenti uniforme | repo |
| Template `docs/ROADMAP.md` | priorità e stato operativo | repo |
| Template `docs/BACKLOG.md` | idee/debiti non ancora promossi | repo |
| Template `docs/CONTEXT.md` | handoff e contesto operativo | repo |
| Template `docs/TOOLCHAIN.md` | runtime, versioni, lockfile, tool | repo |
| Indice decisioni | catalogo ADR e decisioni stabili | `docs/DECISIONS.template.md` |
| Template ADR | decisioni stabili | `docs/decisions/template.md` |
| Checklist manutenzione | check mensile e pre-publish/deploy/release | `CHECKLIST-MANUTENZIONE.md` |

## Matrice delle priorità

| Area | Priorità | Motivo |
| --- | --- | --- |
| AGENTS.md | Alta | È la fonte primaria operativa per Codex |
| Roadmap/backlog | Alta | Evita dispersione e scope implicito |
| Pubblicazione/release/deploy | Alta | Riduce errori operativi e false chiusure |
| GitHub/Codex inbox | Alta | Già quasi uniforme, va reso obbligo operativo |
| Catalogo docs | Alta | Serve a orientare ogni nuova chat |
| Test/verifiche | Alta | Deve restare proporzionato ma prevedibile |
| Handoff/context | Media/alta | Fondamentale per lavori lunghi |
| ADR lifecycle | Media | Utile soprattutto su progetti in evoluzione |
| React Doctor | Alta per app React | Obbligatorio dopo ogni release minor `X.Y.Z` |
| Manutenzione periodica | Media | Mensile e obbligatoria prima di publish/deploy/release |
| Brand/glossario | Media | Importante ma repo-specifico |
| Produzione/health/rollback | Alta solo per runtime attivi | Non applicabile a docs-first |

## Output della fase documentale

Prima di passare agli interventi repository per repository, l’output approvato è:

- un template `AGENTS.md` comune ma adattabile;
- una checklist documentale comune;
- una matrice repo aggiornata con stato, gap e priorità;
- una mappa source of truth per repo;
- una convenzione roadmap/backlog/ADR;
- una semantica condivisa per comandi operativi;
- una regola comune per Codex inbox e commenti PR;
- un elenco dei vincoli repo-specifici da non normalizzare;
- una baseline per nuovi progetti;
- una checklist di pronto intervento su repo esistenti;
- una regola operativa per il coordinamento degli interventi;
- una lista di azioni operative da eseguire nella Fase 2;
- un ordine di intervento confermato.

Il passaggio alla fase operativa avviene dopo questa approvazione. Senza questa base, il rischio sarebbe iniziare patch corrette localmente ma incoerenti come sistema complessivo.

## Regola finale

La coerenza desiderata non è “stesso processo ovunque”.

La coerenza desiderata è:

- stesso modo di ragionare;
- stessa chiarezza su cosa è deciso e cosa no;
- stessa disciplina su Git, docs, test e pubblicazione;
- stessa attenzione a dati, privacy e fonti;
- stessa qualità di handoff e prossimi passi;
- differenze tecniche dichiarate, documentate e rispettate.
