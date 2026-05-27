# Atlas

Atlas è il meta-progetto di coordinamento dei progetti locali.

Contiene il piano generale, i template e le checklist da usare per uniformare governance, documentazione, versioning, GitHub, verifiche, release, deploy e handoff tra le repo.

Atlas non è un prodotto applicativo e non sostituisce gli `AGENTS.md` delle singole repository. È la cabina di regia leggera per decidere standard comuni, preservare i vincoli repo-specifici e preparare interventi ordinati.

## Documento principale

- `piano-coordinamento-progetti.md`: piano completo, decisioni approvate, matrice repo e ordine operativo.

## Documenti canonici di Atlas

- `AGENTS.md`: regole operative specifiche di Atlas.
- `docs/INDEX.md`: indice documentale unico.
- `docs/ROADMAP.md`: direzione, priorità e prossimi passi di Atlas.
- `docs/PROJECTS.md`: registro vivo dei progetti coordinati, con stato, stack, fonti, vincoli, prossime azioni e rischi.
- `docs/HEALTH.md`: matrice health sintetica dei progetti coordinati.
- `docs/MAINTENANCE.md`: ciclo di manutenzione periodica Atlas.
- `docs/STANDARDS.md`: stato di uniformazione degli standard Atlas.
- `docs/STANDARD_CANDIDATES.md`: pattern emersi dalle repo e candidati a standard.
- `docs/PUBLISH_DEPLOY_RELEASE.md`: matrice operativa per publish, release e deploy.
- `docs/APPLYING_ATLAS.md`: guida breve per applicare Atlas a una repo.
- `docs/NEXT_STEPS.md`: procedura per rispondere a "e ora?" senza trasformare Atlas in sviluppo prodotto.
- `docs/BACKLOG.md`: idee, debiti e attività non ancora promosse.
- `docs/CONTEXT.md`: handoff e contesto operativo per riprendere il lavoro.
- `docs/TOOLCHAIN.md`: tool, runtime e verifiche applicabili ad Atlas.
- `docs/DECISIONS.md`: indice delle decisioni stabili.
- `docs/decisions/template.md`: template ADR per nuove decisioni.

## Template e checklist

- `AGENTS.template.md`: base per le regole operative di ogni repo.
- `CHECKLIST-IMPLEMENTAZIONE.md`: checklist da usare quando si applica il piano a una repo.
- `CHECKLIST-MANUTENZIONE.md`: checklist mensile e pre-publish/pre-deploy/pre-release.
- `CHECKLIST-NUOVA-REPO.md`: checklist rapida per portare una nuova repo nel perimetro Atlas.
- `docs/INDEX.template.md`: indice documentale unico.
- `docs/ROADMAP.template.md`: roadmap canonica.
- `docs/BACKLOG.template.md`: backlog separato dalla roadmap.
- `docs/TOOLCHAIN.template.md`: runtime, versioni, package manager, lockfile e tool esterni.
- `docs/CONTEXT.template.md`: contesto operativo e handoff.
- `docs/DECISIONS.template.md`: indice decisioni.
- `docs/decisions/template.md`: template ADR.

## Regole d'uso

1. Prima di applicare i template a una repo, leggere il suo `AGENTS.md`.
2. Non sovrascrivere documenti esistenti senza inventario dei contenuti.
3. Censire funzioni, documenti, runbook, workflow e regole repo-specifiche già mature prima di applicare uno standard Atlas.
4. Migrare, collegare o dichiarare superato ogni contenuto utile.
5. Non creare documenti doppi con stesso titolo, stesso scopo o stesso basename Markdown.
6. Adattare comandi, release, deploy e verifiche alla repo reale.
7. Applicare React Doctor solo alle app React, obbligatorio dopo ogni release minor `X.Y.Z`.
8. Non proporre sviluppo prodotto delle repo coordinate come prossimo passo Atlas senza repo target e scope espliciti.
9. Pulire `.DS_Store` se compare nel working tree o risulta tracciato per errore; mantenerlo ignorato.

## Stato operativo

- Fase: docs-first / coordinamento operativo.
- Git: repository locale inizializzata su branch `main`.
- GitHub: repository privata `https://github.com/max23468/Atlas`.
- Release e deploy: non applicabili finché Atlas resta solo meta-progetto documentale.
- Prossimo passo: standard Atlas censiti e uniformazioni sicure pubblicate;
  sospensione globale GitHub Actions superata; workflow riavviati dopo verifica del `2026-05-27`
