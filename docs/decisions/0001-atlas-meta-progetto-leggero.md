# 0001 - Atlas come meta-progetto leggero

Data: 2026-05-24

Stato: Accettata

## Contesto

La ricognizione trasversale dei progetti locali ha prodotto un piano comune per governance, documentazione, GitHub, versioning, publish/deploy/release, test, Codex inbox, React Doctor e handoff.

Senza un progetto dedicato, il piano resterebbe una nota lunga e fragile. Allo stesso tempo, trasformarlo in un'applicazione o in un sistema operativo pesante creerebbe burocrazia e sposterebbe attenzione dai progetti reali.

## Decisione

Atlas è il meta-progetto docs-first di coordinamento dei progetti locali.

Atlas contiene:

- piano principale;
- documenti canonici di governo;
- template riusabili;
- checklist operative;
- ADR e decisioni stabili;
- stato, roadmap, backlog e handoff trasversali.

Atlas non è un prodotto applicativo, non ha runtime, non ha deploy e non sostituisce gli `AGENTS.md` delle singole repo.

Il piano di Atlas non viene applicato automaticamente a Pratix, DocMolder, FiscalBay, GLM, SendChimp, SyncBay o TRAM. Ogni intervento repo-per-repo richiede lettura dell'`AGENTS.md` della repo bersaglio, controllo dello stato reale e scope esplicito.

## Alternative considerate

- Lasciare il piano come cartella di template: respinta, perché mancherebbero source of truth, handoff e stato operativo.
- Trasformare Atlas in una dashboard o app runtime: respinta, perché il valore attuale è coordinamento leggero, non prodotto.
- Distribuire subito tutte le regole nelle repo: respinta, perché prima va stabilizzato lo standard centrale e vanno rispettati i vincoli repo-specifici.

## Impatti

- Prodotto: Atlas resta cabina di regia, non prodotto per utenti finali.
- Tecnico: nessun runtime obbligatorio; Git locale inizializzato per versionare la base documentale.
- Dati/privacy: non devono essere copiati dati reali o segreti dalle repo coordinate.
- Deploy/release: non applicabili finché Atlas resta docs-first.
- Documentazione: `README.md`, `AGENTS.md`, `docs/INDEX.md`, `docs/ROADMAP.md`, `docs/BACKLOG.md`, `docs/CONTEXT.md`, `docs/TOOLCHAIN.md` e `docs/decisions/` sono i punti canonici.

## Conseguenze operative

- Prima di modifiche non banali in Atlas si legge `AGENTS.md`.
- Prima di interventi su altre repo si legge l'`AGENTS.md` della repo interessata.
- I template restano riusabili e separati dai documenti canonici reali.
- Publish, deploy e release di altre repo non sono impliciti in modifiche ad Atlas.

## Verifiche

- `git status --short`
- `rg --files`
- controllo manuale dei documenti canonici e dei link interni

## Collegamenti

- Roadmap: `../ROADMAP.md`
- Backlog: `../BACKLOG.md`
- PR/issue: non applicabile
- Documenti collegati: `../../README.md`, `../../AGENTS.md`, `../../piano-coordinamento-progetti.md`
