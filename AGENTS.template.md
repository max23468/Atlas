# AGENTS.md

## Scopo

Questo file definisce le regole operative della repository per Codex e agenti.

Prima di modifiche non banali, leggere questo file e i documenti canonici indicati sotto.

## Priorità delle istruzioni

Ordine di priorità:

1. istruzioni di sistema/developer;
2. questo `AGENTS.md` e gli eventuali `AGENTS.md` più profondi;
3. documenti canonici della repo;
4. richiesta utente corrente;
5. convenzioni dedotte da codice, test, configurazione e documenti vicini;
6. assunzioni operative, solo se marginali e dichiarate quando rilevanti.

Se una richiesta contraddice vincoli tecnici, sicurezza, dati, policy della repo o decisioni approvate, segnalarlo prima di procedere.

## Identità del progetto

- Nome: `[NOME_PROGETTO]`
- Tipo/fase: `[docs-first | MVP locale | runtime attivo | produzione | operativo con release | manutenzione]`
- Scopo: `[problema risolto]`
- Perimetro: `[cosa rientra nel progetto]`
- Non-obiettivi: `[cosa non deve diventare]`

Proposte fuori perimetro vanno respinte, parcheggiate in backlog o trasformate in decisione esplicita prima di diventare scope operativo.

## Fonti primarie

Leggere in questo ordine:

1. `README.md`
2. `docs/INDEX.md`
3. `docs/CONTEXT.md`
4. `docs/ROADMAP.md`
5. `docs/BACKLOG.md`
6. `docs/TOOLCHAIN.md`
7. `docs/DECISIONS.md`
8. `docs/DECISIONS_PENDING.md`, se presente
9. `docs/decisions/`
10. guide, runbook, checklist, codice, test e configurazioni collegati al task

Le fonti repo-specifiche estendono lo standard comune senza creare eccezioni implicite.

## Workflow operativo

Prima di lavorare:

1. eseguire `git status --short`;
2. leggere i file vicini al cambiamento e la documentazione collegata;
3. controllare la `Codex feedback inbox`;
4. identificare verifiche proporzionate;
5. valutare impatto su docs, roadmap, changelog, versioning, release e deploy;
6. non toccare modifiche non proprie;
7. dichiarare se publish, deploy o release sono fuori scope.

Se scope, comportamento atteso, rischio, deploy o release sono ambigui, chiedere conferma prima di procedere. Le assunzioni sono ammesse solo per dettagli marginali.

## Branch, worktree e modifiche non proprie

- Usare una branch dedicata `codex/<tema>` per ogni lavoro non banale.
- Il commit diretto su `main` è ammesso solo per micro-modifiche docs-only a basso rischio e solo se la policy locale lo consente.
- Usare un worktree separato quando il checkout non è pulito, l'intervento è lungo, si lavora su più repo o vanno preservate modifiche dell'utente.
- Non mescolare modifiche non proprie nello stesso commit.
- Prima di dichiarare un lavoro pubblicato o chiuso, controllare `git branch -vv` e `git worktree list` quando branch/worktree sono coinvolti.
- Dopo publish/merge, pulire branch e worktree locali o dichiarare cosa resta aperto intenzionalmente.

## Documentazione

Documenti canonici:

- roadmap: `docs/ROADMAP.md`
- indice: `docs/INDEX.md`
- backlog: `docs/BACKLOG.md`
- contesto: `docs/CONTEXT.md`
- toolchain: `docs/TOOLCHAIN.md`
- decisioni: `docs/DECISIONS.md` e `docs/decisions/`
- decisioni pending: `docs/DECISIONS_PENDING.md`, se presente

Non creare documenti doppi con stesso titolo, stesso scopo o stesso basename Markdown. Migrare, collegare o trasformare in rinvio temporaneo i documenti non canonici.

## Regola anti-perdita

Durante migrazioni, merge documentali o rinomini non perdere contenuti.

Prima di eliminare o sostituire un documento, verificare che ogni informazione utile sia stata migrata, collegata o dichiarata superata. Se un contenuto viene rimosso per uniformità, dichiararlo nel riepilogo.

Strumenti, automazioni e riscritture non devono comprimere, riassumere o scartare contenuti utili durante una migrazione salvo decisione esplicita.

## Versioning, changelog e release

Policy: `[non applicabile | locale | SemVer | manuale | GitHub Release | altro]`

Prima di chiudere un lavoro, valutare impatto su:

- versione;
- changelog;
- release;
- documentazione collegata.

Le modifiche docs interne o di governance possono essere `Non versionato` solo se la policy della repo lo prevede o se l'impatto reale non richiede release. Non delegare changelog o release a bot automatici come fonte primaria senza decisione esplicita della repo.

Usare Conventional Commit coerente con l'impatto: `feat`, `fix`, `docs`, `test`, `chore`, `refactor` o categoria equivalente prevista localmente.

## Publish, deploy e release

Semantica comune:

- `pubblica`: porta il lavoro nel canale canonico previsto nel modo più completo possibile e proporzionato al diff: PR/merge o flusso equivalente su `main`, verifiche previste, controllo inbox, valutazione release/deploy, verifica finale e cleanup di branch/worktree quando applicabile;
- `rilascia`: chiude o crea una versione secondo policy;
- `deploya`: aggiorna runtime o ambiente operativo dichiarato;
- `pubblica tutto`: publish, eventuale release, eventuale deploy, verifica e cleanup.

Release e deploy vanno valutati insieme quando entrambi sono applicabili. Non chiudere una release o un deploy senza dichiarare lo stato dell'altro lato.

Target repo:

- publish: `[target]`
- release: `[target o non applicabile]`
- deploy: `[target o non applicabile]`

Se release o deploy non servono per lo specifico diff, dichiararli come non applicabili o fuori scope con motivo.

## GitHub, PR e Codex

Baseline:

- PR template;
- issue template minima;
- `Codex feedback inbox`;
- workflow o procedura equivalente per commenti Codex, se prevista;
- PR title check o controllo equivalente;
- Dependabot quando esistono dipendenze o manifest compatibili;
- branch protection solo se progetto operativo/condiviso.

Per lavori non banali usare PR verso `main`. Prima di PR ready, merge, pubblicazione, deploy o release:

- controllare la `Codex feedback inbox`;
- risolvere i thread actionable o dichiararli fuori scope;
- fare self-review del diff;
- verificare title/commit secondo Conventional Commit o policy locale;
- controllare changelog/versioning/deploy quando applicabili.

Non introdurre nuovi workflow, bot, branch protection o automazioni release/deploy senza decisione documentata.

## Test e verifiche

Corsie comuni:

- `veloce`: docs-only, governance, refusi o micro-change a basso rischio;
- `standard`: cambi codice/config/runtime ordinari;
- `completa`: release, deploy, sicurezza, dati, auth, pagamenti, integrazioni esterne o refactor trasversali.

Comandi minimi:

- install/setup: `[comando o non applicabile]`
- lint/typecheck: `[comando o non applicabile]`
- test: `[comando o non applicabile]`
- build: `[comando o non applicabile]`
- smoke: `[comando o non applicabile]`
- release/deploy dry run: `[comando o non applicabile]`

Non dichiarare verifiche non eseguite. Se un controllo fallisce o non è eseguibile, dichiarare impatto e prossimo passo.

## UI, React e browser checks

Se la repo contiene UI React/Next/Vite o dashboard:

- mantenere UI nella lingua e nel glossario della repo;
- verificare responsive, overflow, sovrapposizioni, stati vuoti/errore/loading e accessibilità proporzionata;
- usare design system, componenti e icone già adottati dalla repo;
- evitare nuove librerie UI senza motivazione;
- per dashboard operative, privilegiare densità, scansione e chiarezza rispetto a layout marketing;
- mostrare fonte, stato e rischio quando l'utente deve prendere decisioni operative;
- eseguire browser check proporzionati quando il diff tocca flussi utente reali;
- eseguire React Doctor dopo release minor `X.Y.Z` o modifiche React trasversali, se previsto dalla policy locale.

Se la repo non ha UI, dichiarare `N/A`.

## Provider, API e dati variabili

Per fonti, provider e dati aggiornabili:

- usare fonti ufficiali o correnti quando il dato può cambiare;
- distinguere fatto, fonte, assunzione, inferenza e decisione interna;
- non dedurre dati assenti dalle API;
- documentare data e fonte quando il dato entra in prodotto, docs, codice o decisione;
- verificare free-tier, costi, billing e limiti prima di proporre o attivare provider;
- non inviare dati sensibili a provider esterni senza policy, minimizzazione e canale approvato.

## Deploy, produzione e verifica live

Ogni repo deve dichiarare se deploy è `N/A`, futuro, manuale, automatico o attivo.

Per deploy reali:

- usare solo target e procedure canoniche della repo;
- fare deploy solo se diff, policy o richiesta lo richiedono;
- verificare pre-deploy branch, worktree, check e versione;
- eseguire post-deploy concreto: stato, URL, health, versione, log, percorso minimo o output workflow;
- dichiarare rollback o runbook quando la produzione è sensibile.

Non attivare App Store, billing, campagne, provider produttivi, webhook produttivi o dati reali senza decisione esplicita.

## Sicurezza, privacy e dati

Dati trattati:

- `[dato]`

Provider/API:

- `[provider]`

Regole:

- non committare segreti, `.env`, dump o dati reali non necessari;
- non stampare segreti in chat, log, screenshot o report;
- usare controlli booleani per verificare la presenza di segreti, mai `echo` del valore;
- distinguere chiavi pubbliche, secret, token e credenziali operative;
- non inserire dati reali in test, fixture, screenshot, report o docs salvo policy esplicita;
- dichiarare rischio e mitigazione quando il lavoro tocca dati sensibili.

## File generati, temporanei e output applicativi

- Non committare build, cache, log, temp, export, dump, screenshot sensibili, `.DS_Store` o file equivalenti.
- Dichiarare gli output applicativi committabili per path e condizioni, se la repo ne prevede.
- Controllare il diff prima di commit o publish.
- Se cleanup, retention o output cambiano, dichiarare impatto e verifica.

## Pulizia repository

`.DS_Store` e file equivalenti di sistema vanno puliti dal working tree o dal tracciamento se compaiono per errore, mantenendoli ignorati per il futuro.

Non trattare `.DS_Store` come contenuto progettuale.

## Risposta finale

Chiudere ogni intervento con:

- cosa è stato cambiato o scoperto;
- file principali, se utili;
- verifiche eseguite, fallite o non eseguite con motivo;
- contenuti migrati, rimossi o preservati, se c'è migrazione;
- stato publish, release e deploy quando applicabile;
- branch/worktree quando applicabile;
- rischi residui;
- prossimo passo operativo o assenza di prossimo passo.

Evitare footer rituali e non inventare risultati di test o verifiche.

## Definizione di completamento

Un lavoro è completo quando:

- scope richiesto chiuso;
- perimetro, stack, docs e decisioni rispettati;
- docs, roadmap, changelog, ADR, versioning, release e deploy valutati;
- verifiche proporzionate eseguite o dichiarate non applicabili;
- Codex inbox controllata quando prevista;
- publish/deploy/release gestiti o dichiarati fuori scope;
- branch, worktree e modifiche non proprie sono puliti o dichiarati;
- nessun segreto, dato sensibile, file temporaneo o contenuto utile è stato perso.
