# 0002 - Struttura canonica root e docs

Data: 2026-05-24

Stato: Accettata

## Contesto

Atlas deve essere leggibile in pochi secondi e, allo stesso tempo, conservare decisioni, roadmap, backlog, contesto e template senza creare duplicati.

La ricognizione ha approvato una separazione chiara: root per ingresso, configurazione e strumenti operativi; `docs/` per governance, contesto e decisioni.

## Decisione

Atlas usa questa struttura canonica:

- root: `README.md`, `AGENTS.md`, `piano-coordinamento-progetti.md`, template principali, checklist operative e configurazioni;
- `docs/`: indice, roadmap, backlog, contesto, toolchain e decisioni;
- `docs/DECISIONS.md`: indice decisionale;
- `docs/decisions/`: ADR puntuali e decisioni stabili autonome;
- file `*.template.md`: template riusabili, non documenti canonici dello stato di Atlas.

L'indice unico è `docs/INDEX.md`. La roadmap unica è `docs/ROADMAP.md`. Il backlog unico è `docs/BACKLOG.md`. L'indice decisionale è `docs/DECISIONS.md`; le decisioni stabili autonome vivono in `docs/decisions/`.

Durante migrazioni o uniformazioni vale la regola anti-perdita: nessun contenuto utile va eliminato senza essere migrato, collegato o dichiarato superato.

## Alternative considerate

- Tenere tutti i documenti in root: respinta, perché renderebbe la root un archivio e non un ingresso operativo.
- Usare `docs/README.md` come indice: respinta, perché la decisione approvata è avere `docs/INDEX.md` come indice unico.
- Spostare subito tutti i template in una sottocartella dedicata: sospesa, perché l'attuale struttura è già chiara e non serve una migrazione cosmetica.

## Impatti

- Prodotto: Atlas resta più facile da riprendere in nuove chat.
- Tecnico: la root resta corta e orientata a ingresso, template e checklist.
- Dati/privacy: la separazione riduce il rischio di copiare contenuti sensibili dalle repo coordinate dentro documenti sbagliati.
- Deploy/release: non applicabili.
- Documentazione: ogni nuovo documento deve avere un ruolo diverso dai documenti canonici già esistenti.

## Conseguenze operative

- Aggiornare `docs/INDEX.md` quando si aggiunge, sostituisce o migra un documento.
- Non creare doppioni di roadmap, backlog, indice o decisioni.
- Non creare due file Markdown con lo stesso basename nella stessa repo.
- Lasciare i template con suffisso `.template.md`.
- Usare `.gitignore` per escludere `.DS_Store` e rumore locale.

## Verifiche

- `rg --files`
- `find . -name .DS_Store -print`
- controllo manuale di `README.md`, `docs/INDEX.md` e `docs/DECISIONS.md`

## Collegamenti

- Roadmap: `../ROADMAP.md`
- Backlog: `../BACKLOG.md`
- PR/issue: non applicabile
- Documenti collegati: `../../README.md`, `../../AGENTS.md`, `../INDEX.md`, `../../piano-coordinamento-progetti.md`
