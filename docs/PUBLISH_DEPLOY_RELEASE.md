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
- `Deploya` richiede target, comando e verifica post-deploy dichiarati.
- Se GitHub Actions è senza budget, usare verifiche locali e canali diretti
  repo-specifici; non rilanciare o aggiungere workflow.
- Non inventare deploy/release dove non esistono.

## Matrice repo

| Repo | Publish | Release | Deploy | Canale/comando canonico | Note |
| --- | --- | --- | --- | --- | --- |
| Atlas | Push/PR su GitHub privata | N/A | N/A | `git push origin main` o PR se non banale | Docs-first; nessun runtime |
| Pratix | PR/merge GitHub secondo policy repo | Sì, patch/minor secondo guide repo | Sì, Vercel/Supabase quando il diff lo richiede | Guide Pratix `versioning-e-release` e `deploy`, `publish:finish` quando previsto | React Doctor dopo release minor |
| DocMolder | PR/merge GitHub | Sì, Release Please/policy repo | Sì, VPS solo quando richiesto dal runbook | `AGENTS.md`, `docs/RELEASE_PROCESS.md`, `docs/VPS_RUNBOOK.md` | Telegram-first; documenti sensibili |
| FiscalBay | PR/merge GitHub o commit diretto naturale su `main` | Sì, esplicita via script locale/VPS | Sì, VPS fuori da GitHub Actions | `scripts/release_now.sh`, `scripts/deploy_now.sh` | VPS corretta solo `opc@79.72.45.89`; Actions non sono canale deploy |
| GLM | PR/merge GitHub | Sì, policy locale dichiarata | Sì, Cloudflare Pages quando richiesto | Guide GLM `versioning-e-release` e `cloudflare-pages` | Non usare Vercel/Supabase |
| SendChimp | PR/merge GitHub | Locale, solo se changelog contiene voci versionate | Vercel production esiste, ma deploy runtime non va attivato senza decisione | `npm run release`, Vercel CLI solo se policy lo richiede | MVP manuale; niente invii reali o provider nuovi |
| SyncBay | PR/merge GitHub | Locale `0.x`, niente tag/GitHub Release finché policy non cambia | Vercel automatico; App Store production non attivo | Guide SyncBay `git-e-pubblicazione`, `versioning-e-release`, `provisioning-runtime` | Shopify/eBay, no marketplace generico |
| TRAM | PR/merge GitHub o commit diretto docs-only sicuro | Sì, SemVer `0.x` con `package.json` come fonte | No target approvato | `docs/decisions/0003-versioning-release-policy.md` | Release non deploya; niente `docs/decisions/README.md` per basename |
| Sentinel | PR/merge GitHub | Parziale/N/A | Sì, ma runtime attuale è GitHub Actions schedulato | Workflow `Sentinel` quando budget Actions disponibile | Workflow runtime sospeso finché Actions è senza budget |

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

## Azioni sospese per budget Actions

- `Codex PR comments` resta disabilitato manualmente sulle repo coordinate.
- `Sentinel` runtime schedulato resta disabilitato manualmente.
- Dependabot su GLM e Sentinel resta sospeso o da non riattivare finché non torna
  un budget sostenibile.
