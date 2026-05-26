# 0004 - Basename Markdown univoci

Data: 2026-05-26

Stato: Accettata

## Contesto

Durante la verifica delle eccezioni Atlas è emerso che la regola TRAM sui
basename Markdown univoci è più solida del template Atlas precedente, che
prevedeva `README.md` in root e `docs/decisions/README.md` come indice ADR.

Avere più file Markdown con lo stesso nome in cartelle diverse rende più
fragile ricerca, handoff, riferimenti rapidi e migrazioni documentali.

## Decisione

Atlas promuove a standard trasversale la regola: non creare due file Markdown
con lo stesso nome base nella stessa repository.

Il caso base diventa:

- `README.md` solo come ingresso root;
- `docs/INDEX.md` come indice documentale unico;
- `docs/DECISIONS.md` come indice decisionale;
- `docs/decisions/` per ADR puntuali con naming `NNNN-slug-breve.md`;
- nessun nuovo `docs/README.md`, `docs/decisions/README.md`, `notes.md`,
  `plan.md`, `roadmap.md`, `index.md` o altro basename generico duplicabile.

## Alternative considerate

- Mantenere `docs/decisions/README.md` come caso base Atlas: respinta perché
  contraddice la regola dei basename univoci e crea un secondo `README.md`.
- Lasciare la regola solo a TRAM: respinta perché il principio è utile a tutte
  le repo coordinate.

## Impatti

- Prodotto: nessun impatto applicativo.
- Tecnico: migrazioni documentali più chiare e meno ambigue.
- Documentazione: Atlas e le repo coordinate devono usare un indice decisionale
  con basename univoco.
- Deploy/release: non applicabili.

## Conseguenze operative

- Aggiornare template e checklist Atlas.
- Trattare `docs/decisions/README.md` esistenti nelle repo coordinate come gap
  da valutare e riallineare, preservando ogni contenuto.
- Non rimuovere documenti storici senza migrazione o rinvio esplicito.

## Verifiche

- `rg --files`
- controllo manuale dei basename Markdown duplicati
- `git diff --check`

## Collegamenti

- Indice: `../INDEX.md`
- Standard: `../STANDARDS.md`
- Candidati: `../STANDARD_CANDIDATES.md`
