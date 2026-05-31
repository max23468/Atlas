# Decisioni Atlas

Questo indice raccoglie le decisioni stabili di Atlas.

## Decisioni attive

- [0001 - Atlas come meta-progetto leggero](decisions/0001-atlas-meta-progetto-leggero.md): Accettata.
- [0002 - Struttura canonica root e docs](decisions/0002-struttura-canonica-root-docs.md): Accettata.
- [0004 - Basename Markdown univoci](decisions/0004-basename-markdown-univoci.md): Accettata.
- [0005 - Repository GitHub pubbliche nel perimetro Atlas](decisions/0005-repository-github-pubbliche.md): Accettata.

## Decisioni da valutare come ADR

- Semantica comune di `pubblica`, `deploya` e `rilascia`.
- Baseline per nuovi progetti.

## Decisioni sostituite o superate

- [0003 - Repository GitHub privata per Atlas](decisions/0003-repository-github-privata.md): Superata da `0005`.

## Regole

- Ogni decisione stabile autonoma vive in `docs/decisions/`.
- Il naming standard è `NNNN-slug-breve.md`.
- Gli stati standard sono `Proposta`, `Accettata`, `Superata`, `Sospesa`, `Respinta`.
- `docs/decisions/template.md` è il template da copiare per nuove ADR.
- L'indice decisionale vive in `docs/DECISIONS.md`, non in `docs/decisions/README.md`.
- Decisioni non ancora approvate stanno in backlog o nel piano, ma devono essere linkate da `docs/INDEX.md` quando diventano operative.
- Non duplicare decisioni con lo stesso titolo o lo stesso scopo.
- Quando una decisione sostituisce documentazione precedente, migrare o collegare il contenuto utile prima di rimuovere il vecchio documento.
