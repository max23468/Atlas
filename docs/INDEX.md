# Indice documentazione Atlas

Questo è l'indice documentale unico di Atlas.

Atlas usa la root per ingresso, istruzioni operative, template e checklist. Usa `docs/` per governance, roadmap, backlog, contesto, toolchain e decisioni.

## Ingresso

- `README.md`: introduzione al progetto, struttura e regole d'uso.
- `AGENTS.md`: regole operative specifiche per lavorare in Atlas.
- `piano-coordinamento-progetti.md`: piano principale con decisioni approvate, matrice repo, vincoli e ordine operativo.

## Stato e lavoro

- `docs/ROADMAP.md`: direzione, priorità e prossimi passi di Atlas.
- `docs/COORDINATION_HISTORY.md`: archivio storico dei cicli di coordinamento già chiusi.
- `docs/PROJECTS.md`: registro vivo dei progetti coordinati, con stato, stack/runtime, Git/GitHub, source of truth, vincoli, prossime azioni e blocchi.
- `docs/HEALTH.md`: matrice health sintetica per decidere dove guardare prima.
- `docs/MAINTENANCE.md`: ciclo di manutenzione periodica e criteri di intervento.
- `docs/STANDARDS.md`: matrice degli standard Atlas e del loro stato repo per repo.
- `docs/STANDARD_CANDIDATES.md`: registro dei pattern maturi candidati a standard.
- `docs/SEMANTIC_CHECKLIST.md`: checklist dei contenuti minimi richiesti per la compliance semantica.
- `docs/SEMANTIC_COMPLIANCE_GAPS.md`: checklist dei gap di compliance semantica da normalizzare.
- `docs/ACTIONS_FAILURE_AUDIT_2026-05-26.md`: audit read-only dei failure GitHub Actions storici durante la sospensione Actions.
- `docs/PUBLISH_DEPLOY_RELEASE.md`: matrice per distinguere publish, release e deploy repo per repo.
- `docs/APPLYING_ATLAS.md`: guida operativa per applicare Atlas a una repo.
- `docs/NEXT_STEPS.md`: procedura per scegliere prossimi passi Atlas senza confonderli con sviluppo prodotto delle repo.
- `docs/BACKLOG.md`: idee, debiti, bug e attività non ancora promosse.
- `docs/CONTEXT.md`: handoff per nuove chat e lavoro continuativo.
- `docs/TOOLCHAIN.md`: tool, runtime, versioni e verifiche applicabili ad Atlas.
- `docs/doppler-setup.md`: integrazione Doppler, variabili GitHub e verifica segreti CI.

## Decisioni

- `docs/decisions/`: ADR e decisioni stabili.
- `docs/DECISIONS.md`: indice delle decisioni.
- `docs/decisions/template.md`: template ADR da copiare per nuove decisioni.
- `docs/decisions/0001-atlas-meta-progetto-leggero.md`: identità e perimetro di Atlas.
- `docs/decisions/0002-struttura-canonica-root-docs.md`: struttura canonica root/docs.
- `docs/decisions/0003-repository-github-privata.md`: decisione storica superata sulla pubblicazione GitHub privata.
- `docs/decisions/0004-basename-markdown-univoci.md`: regola sui basename Markdown univoci.
- `docs/decisions/0005-repository-github-pubbliche.md`: repository GitHub pubbliche nel perimetro Atlas.

Le decisioni fondative restanti sono raccolte nel piano principale. Quando una decisione deve diventare autonoma, crearla in `docs/decisions/` e collegarla qui.

## GitHub

- Repository pubblica: `https://github.com/max23468/Atlas`
- Branch principale: `main`
- Baseline: PR template, issue template minima, PR title check e Codex
  feedback inbox nella issue GitHub `#10`.

## Template riusabili

- `AGENTS.template.md`: base per creare o uniformare `AGENTS.md` nelle repo coordinate.
- `docs/INDEX.template.md`: template di indice documentale unico.
- `docs/ROADMAP.template.md`: template di roadmap canonica.
- `docs/BACKLOG.template.md`: template di backlog separato dalla roadmap.
- `docs/TOOLCHAIN.template.md`: template per runtime, package manager, lockfile e tool esterni.
- `docs/CONTEXT.template.md`: template di contesto operativo e handoff.
- `docs/DECISIONS.template.md`: template per indice decisioni.
- `docs/decisions/template.md`: template ADR.

I file `*.template.md` restano template e non devono essere confusi con lo stato reale di Atlas.

## Checklist operative

- `CHECKLIST-IMPLEMENTAZIONE.md`: checklist per applicare il piano a una repo.
- `CHECKLIST-MANUTENZIONE.md`: checklist mensile e pre-publish/pre-deploy/pre-release.
- `CHECKLIST-NUOVA-REPO.md`: checklist per inserire una nuova repo nel perimetro Atlas.

## Repo coordinate

La matrice operativa dettagliata vive in `docs/PROJECTS.md`; lo snapshot health
sintetico vive in `docs/HEALTH.md`.

Atlas coordina, senza modificare automaticamente:

- Atlas
- Pratix
- DocMolder
- FiscalBay
- GLM
- SendChimp
- SyncBay
- TRAM
- Sentinel: monitor operativo in `/Users/Matteo/Progetti/Sentinel`, repo GitHub pubblica `max23468/Sentinel`, workflow schedulato/dispatch, documenti canonici Atlas e output applicativi tracciati.

Prima di intervenire su una di queste repo, leggere il suo `AGENTS.md`, controllare `git status --short` e applicare le regole specifiche della repo.

## Note di manutenzione

Non creare un secondo documento con lo stesso titolo, lo stesso scopo o lo stesso basename Markdown di uno già indicato qui.

Se un documento viene migrato o sostituito, aggiornare questo indice e lasciare un rinvio temporaneo quando serve preservare tracciabilità.

Prima di rimuovere un documento, verificare che il contenuto utile sia stato migrato, collegato o dichiarato superato.
