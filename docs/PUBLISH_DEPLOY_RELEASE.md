# Matrice publish, deploy e release

Data ultimo aggiornamento: 2026-05-26.

Questa matrice evita ambiguità operative tra `pubblica`, `deploya` e
`rilascia`. Le policy delle singole repo prevalgono sempre su questa sintesi.

Legenda:

- `publish`: portare il lavoro nel canale canonico, di solito GitHub/main o PR.
- `release`: creare o chiudere una versione secondo policy.
- `deploy`: aggiornare un runtime o ambiente operativo.

## Regole comuni

- `Pubblica` non significa automaticamente deploy o release.
- `Rilascia` richiede una policy versioning/release della repo.
- Dove esiste una release reale, la policy deve chiarire source of truth,
  formato tag, GitHub Release e changelog; il solo versioning locale è
  transitorio.
- `Deploya` richiede target, comando e verifica post-deploy dichiarati.
- Fino al `2026-06-01` compreso, Atlas non deve usare GitHub Actions come gate
  nelle repo coordinate: usare verifiche locali e canali diretti repo-specifici;
  non rilanciare o aggiungere workflow. Questo vincolo di governance non
  equivale a zero run remoti: al `2026-05-26` restano ancora esempi di run
  falliti o cancellati su più repo.
- Non inventare deploy/release dove non esistono.

## Matrice repo

| Repo | Publish | Release | Deploy | Canale/comando canonico | Note |
| --- | --- | --- | --- | --- | --- |
| Atlas | Push/PR su GitHub privata | N/A | N/A | `git push origin main` o PR se non banale | Docs-first; nessun runtime |
| Pratix | PR/merge GitHub secondo policy repo | Sì, patch/minor secondo guide repo | Sì, Vercel/Supabase quando il diff lo richiede | Guide Pratix `versioning-e-release` e `deploy`, `publish:finish` quando previsto | React Doctor dopo release minor |
| DocMolder | PR/merge GitHub | Sì, Release Please/policy repo | Sì, VPS solo quando richiesto dal runbook | `AGENTS.md`, `docs/RELEASE_PROCESS.md`, `docs/VPS_RUNBOOK.md` | Telegram-first; documenti sensibili |
| FiscalBay | PR/merge GitHub o commit diretto naturale su `main` | Sì, esplicita via script locale/VPS | Sì, VPS fuori da GitHub Actions | `scripts/release_now.sh`, `scripts/deploy_now.sh` | VPS corretta solo `opc@79.72.45.89`; Actions non sono canale deploy |
| GLM | PR/merge GitHub | Locale dichiarata; tag/GitHub Release `vX.Y.Z` solo per release prodotto reale | Sì, Cloudflare Pages quando richiesto | Guide GLM `versioning-e-release` e `cloudflare-pages`, ADR tag/GitHub Release | Non usare Vercel/Supabase; non retro-taggare lo storico |
| SendChimp | PR/merge GitHub | Locale dichiarata; tag/GitHub Release `vX.Y.Z` solo per release prodotto reale | Vercel production esiste; deploy separato da release e invii reali | `npm run release`, Vercel CLI solo se policy lo richiede, ADR tag/GitHub Release | MVP manuale; niente invii reali o provider nuovi |
| SyncBay | PR/merge GitHub | Locale dichiarata; tag/GitHub Release `vX.Y.Z` solo per release prodotto reale; App Store production separato | Vercel automatico; App Store production non attivo | Guide SyncBay `git-e-pubblicazione`, `versioning-e-release`, `provisioning-runtime`, ADR tag/GitHub Release | Shopify/eBay, no marketplace generico |
| TRAM | PR/merge GitHub o commit diretto docs-only sicuro | Sì, SemVer `0.x` con `package.json` come fonte | No target approvato | `docs/decisions/0003-versioning-release-policy.md` | Release non deploya; usa `docs/DECISIONS.md` per basename |
| Sentinel | PR/merge GitHub | Tag/GitHub Release solo per release tool/dashboard, non per scan/report | Sì, ma runtime attuale è GitHub Actions schedulato | Workflow `Sentinel` non prima del `2026-06-02`, salvo nuova decisione; ADR tag/GitHub Release | Workflow runtime sospeso fino al `2026-06-01` compreso |

## Quando fare deploy diretto

Fare deploy diretto solo se tutte queste condizioni sono vere:

- il diff cambia comportamento runtime o operatività reale;
- la repo dichiara un target deploy e un comando fuori GitHub Actions;
- le verifiche locali proporzionate sono passate;
- il deploy è richiesto esplicitamente o necessario per rendere effettiva la
  modifica;
- esiste una verifica post-deploy concreta.

Se una sola condizione manca, dichiarare il deploy fuori scope o sospeso.

## Quando non fare release

Non fare release quando:

- il cambiamento è solo documentale o governance Atlas;
- la repo non ha policy release;
- il changelog contiene solo voci non versionate;
- la release creerebbe tag/GitHub Release non previsti;
- mancano verifiche locali sufficienti.

## Azioni sospese per finestra GitHub Actions

- Fino al `2026-06-01` compreso, Atlas non deve riattivare o aggiungere
  workflow GitHub Actions e non deve usarli come gate.
- Lo stato remoto non è ancora congelato: l'audit read-only
  `docs/ACTIONS_FAILURE_AUDIT_2026-05-26.md` classifica come non gate i failure
  storici su DocMolder `Release Please`/`VPS Check`, GLM `CI`, TRAM
  `Repo Hygiene`, SyncBay `PR Title` e Sentinel `PR Title`/runtime.
- In DocMolder, `Release Please` e `VPS Check` sono disabilitati manualmente
  durante la finestra Actions; vanno rivalutati dal `2026-06-02`.
- In SyncBay, il commit `dc5ba72` è pubblicato su `main` e Vercel production è
  `READY`; i workflow `PR Title` e `Codex PR comments` restano disabilitati
  manualmente durante la finestra Actions.
- `Codex PR comments` resta disabilitato manualmente sulle repo coordinate dove
  era già stato spento.
- `Sentinel` runtime schedulato resta disabilitato manualmente.
- Dependabot resta standard Atlas pieno; eventuali sospensioni locali o run
  cancellati non cambiano la regola e vanno trattati come stato transitorio.
