# AGENTS.md

## Scopo

Questo file definisce le regole operative della repository per Codex e agenti.

Prima di modifiche non banali, leggere questo file e i documenti canonici indicati sotto.

## Priorità delle istruzioni

Ordine di priorità:

1. istruzioni di sistema/developer;
2. questo `AGENTS.md`;
3. documenti canonici della repo;
4. richiesta utente corrente;
5. convenzioni dedotte dal codice.

Se una richiesta contraddice vincoli tecnici, sicurezza, dati o policy della repo, segnalarlo prima di procedere.

## Identità del progetto

- Nome: `[NOME_PROGETTO]`
- Tipo: `[docs-first | MVP locale | runtime attivo | produzione | operativo con release | manutenzione]`
- Scopo: `[problema risolto]`
- Non-obiettivi: `[cosa non deve diventare]`

## Fonti primarie

Leggere in questo ordine:

1. `README.md`
2. `docs/INDEX.md`
3. `docs/CONTEXT.md`
4. `docs/ROADMAP.md`
5. `docs/BACKLOG.md`
6. `docs/TOOLCHAIN.md`
7. `docs/decisions/`
8. guide specifiche collegate al task

## Workflow operativo

Prima di lavorare:

1. eseguire `git status --short`;
2. leggere i file vicini al cambiamento;
3. controllare la `Codex feedback inbox`;
4. identificare verifiche proporzionate;
5. non toccare modifiche non proprie;
6. dichiarare se publish, deploy o release sono fuori scope.

## Documentazione

Documenti canonici:

- roadmap: `docs/ROADMAP.md`
- indice: `docs/INDEX.md`
- backlog: `docs/BACKLOG.md`
- contesto: `docs/CONTEXT.md`
- toolchain: `docs/TOOLCHAIN.md`
- decisioni: `docs/decisions/`

Non creare documenti doppi con stesso titolo o stesso scopo. Migrare o trasformare in rinvio temporaneo i documenti non canonici.

## Regola anti-perdita

Durante migrazioni, merge documentali o rinomini non perdere contenuti.

Prima di eliminare o sostituire un documento, verificare che ogni informazione utile sia stata migrata, collegata o dichiarata superata. Se un contenuto viene rimosso per uniformità, dichiararlo nel riepilogo.

I tool e i subagent non devono comprimere, riassumere o scartare contenuti utili durante una migrazione salvo decisione esplicita.

## Versioning

Policy: `[non applicabile | locale | SemVer | manuale | GitHub Release | altro]`

Prima di chiudere un lavoro, valutare impatto su:

- versione;
- changelog;
- release;
- documentazione collegata.

## Publish, deploy e release

Semantica comune:

- `pubblica`: porta il lavoro nel canale canonico della repo;
- `rilascia`: chiude o crea una versione secondo policy;
- `deploya`: aggiorna runtime o ambiente operativo dichiarato;
- `pubblica tutto`: publish, eventuale release, eventuale deploy, verifica e cleanup.

Target repo:

- publish: `[target]`
- release: `[target o non applicabile]`
- deploy: `[target o non applicabile]`

## GitHub e Codex

Baseline:

- PR template;
- issue template minima;
- `Codex feedback inbox`;
- workflow `Codex PR comments`;
- PR title check;
- Dependabot solo con dipendenze runtime reali;
- branch protection solo se progetto operativo/condiviso.

Controllare la `Codex feedback inbox` prima di PR ready, merge, pubblicazione, deploy o release.

## Subagent

Usare subagent solo quando aiutano a ricognire o applicare il piano senza perdere contesto.

Regole:

- coordinamento centrale nel piano approvato e nella chat/issue di coordinamento;
- fase iniziale read-only;
- una sola repo per volta in scrittura;
- nessuna rimozione di contenuti senza decisione esplicita;
- riepilogo finale con file toccati, contenuti migrati e verifiche.

## Test e verifiche

Comandi minimi:

- install/setup: `[comando]`
- lint/typecheck: `[comando o non applicabile]`
- test: `[comando o non applicabile]`
- build: `[comando o non applicabile]`
- smoke: `[comando o non applicabile]`

Non dichiarare verifiche non eseguite.

## React Doctor

Se la repo contiene un'app React, React Doctor è obbligatorio dopo ogni release minor `X.Y.Z`, cioè quando cambia `Y`.

Comando: `[comando o non applicabile]`

## Sicurezza, privacy e dati

Dati trattati:

- `[dato]`

Provider/API:

- `[provider]`

Regole:

- non inventare dati assenti dalle API;
- non committare segreti;
- rispettare runbook e policy della repo;
- non inviare documenti sensibili a provider esterni senza policy.

## Pulizia repository

`.DS_Store` e file equivalenti di sistema vanno puliti dal working tree o dal tracciamento se compaiono per errore, mantenendoli ignorati per il futuro.

Non trattare `.DS_Store` come contenuto progettuale da eliminare o discutere repo per repo.

## Risposta finale

Chiudere ogni intervento con:

- cosa è stato cambiato;
- file principali;
- verifiche eseguite;
- contenuti migrati o rimossi;
- rischi residui;
- prossimo passo operativo.

## Definizione di completamento

Un lavoro è completo quando:

- scope richiesto chiuso;
- documenti canonici aggiornati se necessario;
- verifiche proporzionate eseguite;
- Codex inbox controllata;
- publish/deploy/release gestiti o dichiarati fuori scope;
- nessun contenuto perso nelle migrazioni.
