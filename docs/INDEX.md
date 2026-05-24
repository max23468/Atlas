# Indice documentazione Atlas

Questo è l'indice documentale unico di Atlas.

Atlas usa la root per ingresso, istruzioni operative, template e checklist. Usa `docs/` per governance, roadmap, backlog, contesto, toolchain e decisioni.

## Ingresso

- `README.md`: introduzione al progetto, struttura e regole d'uso.
- `AGENTS.md`: regole operative specifiche per lavorare in Atlas.
- `piano-coordinamento-progetti.md`: piano principale con decisioni approvate, matrice repo, vincoli e ordine operativo.

## Stato e lavoro

- `docs/ROADMAP.md`: direzione, priorità e prossimi passi di Atlas.
- `docs/PROJECTS.md`: registro vivo dei progetti coordinati, con stato, stack/runtime, Git/GitHub, source of truth, vincoli, prossime azioni e blocchi.
- `docs/BACKLOG.md`: idee, debiti, bug e attività non ancora promosse.
- `docs/CONTEXT.md`: handoff per nuove chat e lavoro continuativo.
- `docs/TOOLCHAIN.md`: tool, runtime, versioni e verifiche applicabili ad Atlas.

## Decisioni

- `docs/decisions/`: ADR e decisioni stabili.
- `docs/decisions/README.md`: indice delle decisioni.
- `docs/decisions/template.md`: template ADR da copiare per nuove decisioni.
- `docs/decisions/0001-atlas-meta-progetto-leggero.md`: identità e perimetro di Atlas.
- `docs/decisions/0002-struttura-canonica-root-docs.md`: struttura canonica root/docs.
- `docs/decisions/0003-repository-github-privata.md`: pubblicazione GitHub privata.

Le decisioni fondative restanti sono raccolte nel piano principale. Quando una decisione deve diventare autonoma, crearla in `docs/decisions/` e collegarla qui.

## GitHub

- Repository privata: `https://github.com/max23468/Atlas`
- Branch principale: `main`
- Baseline: PR template, issue template minima, PR title check.

## Template riusabili

- `AGENTS.template.md`: base per creare o uniformare `AGENTS.md` nelle repo coordinate.
- `docs/INDEX.template.md`: template di indice documentale unico.
- `docs/ROADMAP.template.md`: template di roadmap canonica.
- `docs/BACKLOG.template.md`: template di backlog separato dalla roadmap.
- `docs/TOOLCHAIN.template.md`: template per runtime, package manager, lockfile e tool esterni.
- `docs/CONTEXT.template.md`: template di contesto operativo e handoff.
- `docs/decisions/README.template.md`: template per indice decisioni.
- `docs/decisions/template.md`: template ADR.

I file `*.template.md` restano template e non devono essere confusi con lo stato reale di Atlas.

## Checklist operative

- `CHECKLIST-IMPLEMENTAZIONE.md`: checklist per applicare il piano a una repo.
- `CHECKLIST-MANUTENZIONE.md`: checklist mensile e pre-publish/pre-deploy/pre-release.

## Repo coordinate

La matrice operativa aggiornata vive in `docs/PROJECTS.md`.

Atlas coordina, senza modificare automaticamente:

- Atlas
- Pratix
- DocMolder
- FiscalBay
- GLM
- SendChimp
- SyncBay
- TRAM
- Sentinel: monitor operativo in `/Users/Matteo/Progetti/Sentinel`, repo GitHub privata `max23468/Sentinel`, workflow schedulato/dispatch e output applicativi tracciati; resta l'ultimo target da consolidare con discovery runtime dedicata.

Prima di intervenire su una di queste repo, leggere il suo `AGENTS.md`, controllare `git status --short` e applicare le regole specifiche della repo.

## Note di manutenzione

Non creare un secondo documento con lo stesso titolo o lo stesso scopo di uno già indicato qui.

Se un documento viene migrato o sostituito, aggiornare questo indice e lasciare un rinvio temporaneo quando serve preservare tracciabilità.

Prima di rimuovere un documento, verificare che il contenuto utile sia stato migrato, collegato o dichiarato superato.
