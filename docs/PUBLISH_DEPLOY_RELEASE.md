# Matrice publish, deploy e release

Data ultimo aggiornamento: 2026-05-26.

Questa matrice evita ambiguità operative tra `pubblica`, `deploya` e
`rilascia`. Le policy delle singole repo prevalgono sempre su questa sintesi.

Legenda:

- `publish`: portare il lavoro nel canale canonico, di solito GitHub/main o PR.
- `release`: creare o chiudere una versione secondo policy.
- `deploy`: aggiornare un runtime o ambiente operativo.

## Regole comuni

- `Pubblica` include la chiusura completa prevista dal flusso corrente e non va interpretata come mero push/PR.
  Nel significato operativo richiesto, `pubblica` include comunque: portare il
  lavoro nel canale canonico (tipicamente PR/merge su `main` o workflow equivalente),
  verificare i check previsti e chiudere il checkout quando l'assorbimento è
  completo (branch/worktree locali e remoti non più necessari), includendo release,
  deploy o attivazioni solo se previste dal contesto o richieste esplicitamente.
- `Rilascia` richiede una policy versioning/release della repo.
- Dove esiste una release reale, la policy deve chiarire source of truth,
  formato tag, GitHub Release e changelog; il solo versioning locale è
  transitorio.
- `Deploya` richiede target, comando e verifica post-deploy dichiarati.
- Atlas ha ripreso i workflow GitHub Actions; continuare a usare verifiche locali e canali repo-specifici con priorità.
  Le verifiche remote preesistenti restano storiche; gli errori o cancellazioni
  storiche su più repo rimangono contesto per audit, non blocco operativo.
- Non inventare deploy/release dove non esistono.

## Matrice repo

| Repo | Publish | Release | Deploy | Canale/comando canonico | Note |
| --- | --- | --- | --- | --- | --- |
| Atlas | Push/PR su GitHub privata | N/A | N/A | `git push origin main` o PR se non banale | Docs-first; nessun runtime |
| Pratix | PR/merge GitHub secondo policy repo | Sì, patch/minor secondo guide repo | Sì, Vercel/Supabase quando il diff lo richiede | Guide Pratix `versioning-e-release` e `deploy`, `publish:finish` quando previsto | React Doctor dopo release minor |
| DocMolder | PR/merge GitHub | Sì, policy release manuale repo-specifica | Sì, VPS solo quando richiesto dal runbook | `AGENTS.md`, `docs/RELEASE_PROCESS.md`, `docs/VERSIONING.md`, `docs/VPS_RUNBOOK.md` | Telegram-first; documenti sensibili |
| FiscalBay | PR/merge GitHub o commit diretto naturale su `main` | Sì, esplicita via script locale/VPS | Sì, VPS fuori da GitHub Actions | `scripts/release_now.sh`, `scripts/deploy_now.sh` | VPS corretta solo `opc@79.72.45.89`; Actions non sono canale deploy |
| GLM | PR/merge GitHub | Locale dichiarata; tag/GitHub Release `vX.Y.Z` solo per release prodotto reale | Sì, Cloudflare Pages quando richiesto | Guide GLM `versioning-e-release` e `cloudflare-pages`, ADR tag/GitHub Release | Non usare Vercel/Supabase; non retro-taggare lo storico |
| SendChimp | PR/merge GitHub | Locale dichiarata; tag/GitHub Release `vX.Y.Z` solo per release prodotto reale | Vercel production esiste; deploy separato da release e invii reali | `npm run release`, Vercel CLI solo se policy lo richiede, ADR tag/GitHub Release | MVP manuale; niente invii reali o provider nuovi |
| SyncBay | PR/merge GitHub | Locale dichiarata; tag/GitHub Release `vX.Y.Z` solo per release prodotto reale; App Store production separato | Vercel automatico; App Store production non attivo | Guide SyncBay `git-e-pubblicazione`, `versioning-e-release`, `provisioning-runtime`, ADR tag/GitHub Release | Shopify/eBay, no marketplace generico |
| TRAM | PR/merge GitHub o commit diretto docs-only sicuro | Sì, SemVer `0.x` con `package.json` come fonte | No target approvato | `docs/decisions/0003-versioning-release-policy.md` | Il lavoro viene considerato pubblicato solo a PR/merge completato (o commit doc-only previsto dalla policy); pulizia branch/worktree locali e remoti inclusa |
| Sentinel | PR/merge GitHub | Tag/GitHub Release solo per release tool/dashboard, non per scan/report | Sì, runtime GitHub Actions schedulato | Workflow `Sentinel` attivo dopo riavvio; ADR tag/GitHub Release | Workflow runtime ora attivo |

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

## Stato Actions post-riavvio

- Atlas ha riattivato i workflow GitHub Actions per i casi previsti da policy.
- Lo stato remoto non è ancora congelato: l'audit read-only
  `docs/ACTIONS_FAILURE_AUDIT_2026-05-26.md` classifica come non gate i failure
  storici su DocMolder `VPS Check`/workflow legacy, GLM `CI`, TRAM
  `Repo Hygiene`, SyncBay `PR Title` e Sentinel `PR Title`/runtime.
- In DocMolder, il workflow di rilascio precedente è terminato e il flusso
  corrente segue la policy manuale indicata nei documenti release della repo.
- In SyncBay, il commit `dc5ba72` è pubblicato su `main` e Vercel production è
  `READY`; i workflow `PR Title` e `Codex PR comments` sono stati riavviati.
- `Codex PR comments` viene gestito attivamente nelle repo coordinate secondo
  policy.
- `Sentinel` runtime schedulato è stato riattivato.
- Dependabot resta standard Atlas pieno; eventuali sospensioni locali o run
  cancellati non cambiano la regola e vanno trattati come stato transitorio.
