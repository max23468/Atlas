# AGENTS.md

## Scopo

Questo file definisce le regole operative di Atlas per Codex e agenti.

Atlas è il meta-progetto di coordinamento dei progetti locali. Serve a mantenere standard, template, governance, roadmap trasversale, regole GitHub, versioning, publish/deploy/release, test, Codex inbox, React Doctor, documentazione e handoff.

Prima di modifiche non banali, leggere questo file e i documenti canonici indicati sotto.

## Priorità delle istruzioni

Ordine di priorità:

1. istruzioni di sistema/developer;
2. questo `AGENTS.md`;
3. documenti canonici di Atlas;
4. richiesta utente corrente;
5. convenzioni dedotte dai file esistenti.

Se una richiesta contraddice vincoli tecnici, sicurezza, dati, policy delle repo collegate o decisioni approvate in Atlas, segnalarlo prima di procedere.

## Identità del progetto

- Nome: Atlas.
- Tipo: docs-first / meta-progetto di coordinamento operativo.
- Scopo: rendere coerenti governance, template, documentazione, GitHub, verifiche, release, deploy e handoff dei progetti locali senza cancellare le differenze tecniche motivate.
- Non-obiettivi:
  - non è un prodotto applicativo;
  - non è una dashboard runtime;
  - non sostituisce gli `AGENTS.md` delle singole repo;
  - non applica automaticamente il piano a Pratix, DocMolder, FiscalBay, GLM, SendChimp, SyncBay, TRAM o Sentinel;
  - non introduce release, deploy o workflow GitHub dove non sono stati decisi.

## Fonti primarie

Leggere in questo ordine:

1. `README.md`
2. `piano-coordinamento-progetti.md`
3. `docs/INDEX.md`
4. `docs/CONTEXT.md`
5. `docs/PROJECTS.md`
6. `docs/HEALTH.md`
7. `docs/STANDARDS.md`
8. `docs/STANDARD_CANDIDATES.md`
9. `docs/PUBLISH_DEPLOY_RELEASE.md`
10. `docs/APPLYING_ATLAS.md`
11. `docs/NEXT_STEPS.md`
12. `docs/ROADMAP.md`
13. `docs/BACKLOG.md`
14. `docs/TOOLCHAIN.md`
15. `docs/decisions/README.md`
16. template e checklist collegati al task

Quando si lavora su una repo diversa da Atlas, leggere sempre l'`AGENTS.md` di quella repo prima di proporre o applicare cambiamenti.

## Workflow operativo

Prima di lavorare in Atlas:

1. eseguire `git status --short` se Atlas è una repo Git; se non lo è, dichiararlo;
2. leggere i file vicini al cambiamento;
3. verificare che il task non stia applicando modifiche alle altre repo senza richiesta esplicita;
4. identificare verifiche proporzionate, di solito documentali;
5. non toccare modifiche non proprie;
6. dichiarare se publish, deploy o release sono fuori scope.

Prima di lavorare su una repo coordinata da Atlas:

1. leggere l'`AGENTS.md` della repo;
2. controllare `git status --short`;
3. creare o usare una branch dedicata prima di qualunque modifica;
4. usare un worktree separato quando la repo non è pulita, quando l'intervento è lungo, quando si lavora su più repo in parallelo o quando serve preservare lo stato operativo corrente;
5. leggere i documenti canonici della repo;
6. fare una ricognizione read-only degli elementi repo-specifici già maturi: funzioni, documenti, runbook, checklist, workflow, regole, policy e comportamenti non previsti dal piano Atlas;
7. classificare questi elementi prima di applicare template o standard: mantenere specifico, promuovere come possibile standard Atlas, sostituire con pattern più maturo, parcheggiare in backlog o rimuovere solo se duplicato/superato e assorbito senza perdita;
8. controllare Codex feedback inbox se la repo ha GitHub configurato;
9. applicare il piano solo dentro lo scope autorizzato.

## Branch e worktree nelle repo coordinate

Atlas non deve lavorare direttamente su `main`/`master` delle repo coordinate
quando applica baseline, policy, documenti, workflow o standard.

Regole:

- usare sempre una branch dedicata con prefisso `codex/`, salvo policy locale più
  specifica;
- non iniziare modifiche se la repo ha cambiamenti non propri non compresi nello
  scope;
- usare un worktree separato quando il working tree principale non è pulito,
  quando esistono modifiche dell'utente da preservare, quando l'intervento dura
  più turni o quando Atlas coordina più repo nello stesso ciclo;
- lasciare il checkout principale della repo nella condizione trovata, salvo
  richiesta esplicita;
- dichiarare nel riepilogo branch, worktree, PR e branch residue.

Il worktree non è obbligatorio per ogni modifica piccola e isolata su checkout
pulito; la branch dedicata invece è obbligatoria per gli interventi Atlas sulle
repo coordinate.

## Prossimi passi e scope Atlas

Quando l'utente chiede "e ora?", "prossimi passi?" o formule simili senza
indicare una repo target e uno scope operativo esplicito, Atlas deve proporre
solo lavoro Atlas-first:

- manutenzione governance e documentale;
- audit read-only;
- controllo branch, PR, run, workflow e pubblicazioni residue;
- aggiornamento di matrici, policy, template, checklist e handoff;
- classificazione di pattern o debiti senza trasformarli in sviluppo prodotto.

Atlas non deve proporre sviluppo prodotto delle repo coordinate come prossimo
passo generico. Debiti, pilot, hardening, import/export, provider, UI, OAuth,
deploy o release di una repo diventano attività esecutive solo dopo richiesta
esplicita sulla repo e applicazione della policy locale.

## Documentazione

Documenti canonici di Atlas:

- piano principale: `piano-coordinamento-progetti.md`
- indice: `docs/INDEX.md`
- registro progetti: `docs/PROJECTS.md`
- matrice health: `docs/HEALTH.md`
- manutenzione: `docs/MAINTENANCE.md`
- standard: `docs/STANDARDS.md`
- pattern candidati a standard: `docs/STANDARD_CANDIDATES.md`
- matrice publish/deploy/release: `docs/PUBLISH_DEPLOY_RELEASE.md`
- guida applicazione Atlas: `docs/APPLYING_ATLAS.md`
- prossimi passi Atlas: `docs/NEXT_STEPS.md`
- roadmap: `docs/ROADMAP.md`
- backlog: `docs/BACKLOG.md`
- contesto: `docs/CONTEXT.md`
- toolchain: `docs/TOOLCHAIN.md`
- decisioni: `docs/decisions/`
- checklist implementazione: `CHECKLIST-IMPLEMENTAZIONE.md`
- checklist manutenzione: `CHECKLIST-MANUTENZIONE.md`
- checklist nuova repo: `CHECKLIST-NUOVA-REPO.md`

I file `*.template.md` sono template riusabili, non documenti canonici di stato di Atlas.

Non creare documenti doppi con stesso titolo o stesso scopo. Se un documento viene migrato o trasformato, preservare i contenuti utili e aggiornare `docs/INDEX.md`.

## Regola anti-perdita

Durante migrazioni, merge documentali o rinomini non perdere contenuti.

Prima di eliminare o sostituire un documento, verificare che ogni informazione utile sia stata migrata, collegata o dichiarata superata. Se un contenuto viene rimosso per uniformità, dichiararlo nel riepilogo.

I tool e i subagent non devono comprimere, riassumere o scartare contenuti utili durante una migrazione salvo decisione esplicita.

## Versioning

Policy attuale: non applicabile.

Atlas non ha ancora package, changelog o release policy. Finché resta docs-first, le modifiche documentali non richiedono bump di versione.

Se Atlas viene inizializzato come repo GitHub con release proprie, creare prima una decisione in `docs/decisions/` o aggiornare la roadmap/backlog.

## Publish, deploy e release

Semantica comune:

- `pubblica`: porta il lavoro nel canale canonico previsto;
- `rilascia`: chiude o crea una versione secondo policy;
- `deploya`: aggiorna runtime o ambiente operativo dichiarato;
- `pubblica tutto`: publish, eventuale release, eventuale deploy, verifica e cleanup.

Target Atlas:

- publish: push/PR verso `https://github.com/max23468/Atlas`;
- release: non applicabile;
- deploy: non applicabile.

Non interpretare richieste su Atlas come autorizzazione a pubblicare, rilasciare o deployare altre repo.

## GitHub e Codex

Atlas è inizializzato come repository Git locale su branch `main` e pubblicato nella repository privata `https://github.com/max23468/Atlas`.

Baseline leggera:

- PR template;
- issue template minima;
- PR title check;
- Dependabot solo se compariranno dipendenze runtime reali.

La Codex inbox resta obbligatoria prima di publish, merge, deploy o release nelle repo che la usano già.

## Subagent

Usare subagent solo nella fase implementativa, non per ridecidere lo standard comune.

Regole:

- coordinamento centrale in Atlas;
- prima passata read-only;
- discovery esplicita di contenuti e comportamenti extra rispetto al piano Atlas;
- una sola repo per volta in scrittura;
- nessuna rimozione di contenuti senza decisione esplicita;
- riepilogo finale con file toccati, contenuti migrati e verifiche;
- rispetto dell'`AGENTS.md` della repo assegnata.

## Test e verifiche

Atlas è docs-first e non ha runtime applicativo.

Comandi minimi:

- install/setup: non applicabile;
- lint/typecheck: non applicabile;
- test: non applicabile;
- build: non applicabile;
- smoke: controllo manuale dei documenti e dei link interni;
- Git: `git status --short`;
- file: `rg --files`;
- pulizia sistema: verificare che `.DS_Store` non sia contenuto progettuale.

Non dichiarare verifiche non eseguite.

## React Doctor

Non applicabile ad Atlas.

React Doctor resta obbligatorio solo per app React dopo ogni release minor `X.Y.Z`, cioè quando cambia `Y`, secondo il piano approvato. SendChimp oggi ha runtime React/Next.js, quindi rientra nel criterio quando avrà una release minor applicabile.

## Sicurezza, privacy e dati

Dati trattati:

- nomi e vincoli dei progetti locali;
- regole operative;
- riferimenti a provider, repository e processi;
- nessun dato applicativo reale dovrebbe essere archiviato in Atlas.

Regole:

- non committare segreti;
- non copiare credenziali o dati sensibili dalle repo coordinate;
- non inviare documenti sensibili a provider esterni senza policy della repo interessata;
- non inventare dati fiscali, API, prezzi, limiti o provider variabili;
- quando si lavora su fonti aggiornabili, verificare fonti correnti.

## Pulizia repository

`.DS_Store` e file equivalenti di sistema vanno puliti dal working tree o dal tracciamento se compaiono per errore, mantenendoli ignorati per il futuro quando Atlas sarà una repo Git.

Non trattare `.DS_Store` come contenuto progettuale.

## Risposta finale

Chiudere ogni intervento con:

- cosa è stato cambiato;
- file principali;
- verifiche eseguite;
- contenuti migrati o rimossi;
- rischi residui;
- prossimo passo operativo.

## Definizione di completamento

Un lavoro su Atlas è completo quando:

- scope richiesto chiuso;
- documenti canonici aggiornati se necessario;
- template preservati;
- nessun piano è stato applicato ad altre repo senza richiesta esplicita;
- verifiche proporzionate eseguite o dichiarate non applicabili;
- publish/deploy/release gestiti o dichiarati fuori scope;
- nessun contenuto perso nelle migrazioni.
