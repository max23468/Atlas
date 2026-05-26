# Checklist semantica Atlas

Data ultimo aggiornamento: 2026-05-26.

Questa checklist definisce cosa deve essere verificabile nei documenti canonici
di una repo coordinata da Atlas. Non impone testi identici: impone contenuti
minimi, source of truth chiare ed eccezioni motivate.

## Regola generale

Una repo è semanticamente allineata quando chi apre una nuova chat può capire:

- cosa è il progetto e cosa non è;
- quali documenti leggere prima;
- qual è lo stato corrente;
- quali sono runtime, toolchain, comandi e verifiche;
- come funzionano publish, release e deploy;
- dove stanno decisioni stabili, decisioni pending e ADR;
- quali eccezioni sono repo-specifiche, sospese, equivalenti o non applicabili.

## `AGENTS.md`

Contenuto minimo:

- priorità delle istruzioni;
- identità, perimetro e non-obiettivi del progetto;
- documenti da leggere prima di modifiche non banali;
- regole Git, branch, worktree e protezione modifiche non proprie;
- regole su test, build, lint, smoke e verifiche proporzionate;
- policy publish, release e deploy della repo;
- gestione Codex feedback inbox se la repo la usa;
- sicurezza, privacy, segreti e dati sensibili;
- definizione di done o aspettative di chiusura.

## `docs/INDEX.md`

Contenuto minimo:

- ingresso operativo root: `README.md` e `AGENTS.md`;
- documenti canonici in `docs/`;
- distinzione tra roadmap, backlog, context, toolchain e decisioni;
- guide operative, runbook, piani e documenti specialistici;
- decisioni stabili, pending e ADR puntuali;
- note su documenti migrati o rinominati, senza duplicare basename Markdown.

## `docs/CONTEXT.md`

Contenuto minimo:

- stato progetto e fase corrente;
- versione o source of truth della versione, se esiste;
- deploy/runtime corrente o indicazione esplicita `non applicabile`;
- fonti primarie e documenti da leggere;
- vincoli e non-obiettivi da ricordare;
- eccezioni repo-specifiche marcate;
- rischi o debiti aperti rilevanti;
- handoff pratico e prossimo controllo.

Se la versione applicativa cambia spesso, il contesto deve puntare alla source
of truth (`package.json`, file versione, tag o release) invece di riportare una
versione statica soggetta a drift.

## `docs/TOOLCHAIN.md`

Contenuto minimo:

- runtime e versioni supportate;
- package manager, lockfile e manifest autoritativi;
- comandi locali per sviluppo, verifica e build;
- gate proporzionati per docs-only, runtime, UI, deploy e release;
- tool esterni, provider e target operativi;
- stato GitHub Actions quando è sospeso o non deve essere usato come gate;
- React Doctor quando applicabile;
- Dependabot quando la repo ha manifest compatibili.

## `docs/ROADMAP.md`

Contenuto minimo:

- direzione approvata;
- fasi o priorità correnti;
- criteri per promuovere lavoro dal backlog;
- distinzione tra lavoro prodotto, lavoro tecnico e governance;
- assenza di autorizzazione implicita a deploy/release se la roadmap lo cita.

## `docs/BACKLOG.md`

Contenuto minimo:

- frase esplicita: `Una voce nel backlog non è scope approvato.`;
- idee, debiti e ipotesi non promosse;
- criterio per promuovere una voce in roadmap o decisione;
- nessuna voce formulata come autorizzazione automatica a implementare,
  rilasciare o deployare.

## Decisioni

Contenuto minimo:

- `docs/DECISIONS.md` come registro o indice stabile;
- `docs/DECISIONS_PENDING.md` o equivalente con basename univoco per scelte non
  ancora approvate;
- ADR puntuali in `docs/decisions/NNNN-slug.md`;
- nessun `docs/decisions/README.md`;
- link aggiornati quando un indice decisionale viene migrato.

## Pubblicazione proporzionata

Ogni repo deve dichiarare almeno questi casi:

- docs-only/governance-only: review documentale, link/coerenza e `git diff --check`;
- runtime/config: check locali pertinenti;
- UI/React: build, lint o React Doctor quando previsto dalla policy locale;
- release: solo se la repo ha policy release reale;
- deploy: solo se esiste target deploy approvato e il diff lo richiede.

Smoke test, deploy, release, App Store, VPS o workflow runtime non vanno eseguiti
per un diff solo documentale o di governance.

## Eccezioni

Le eccezioni devono essere marcate con una delle seguenti etichette:

- `OK equivalente`: risultato semantico equivalente con forma locale diversa;
- `repo-specifico`: differenza motivata dalla natura della repo;
- `sospeso`: standard valido ma temporaneamente non attivo;
- `N/A`: standard non applicabile;
- `da riallineare`: gap reale da correggere.

Un'eccezione non marcata non è considerata verificata.
