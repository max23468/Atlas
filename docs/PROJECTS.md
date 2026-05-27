# Registro progetti Atlas

Data ultimo aggiornamento: 2026-05-26

Questo registro è la matrice viva dettagliata dei progetti coordinati da Atlas.
Serve a orientare lo stato operativo, non a sostituire l'`AGENTS.md` o i
documenti canonici delle singole repo. Per il colpo d'occhio health usare anche
`docs/HEALTH.md`.

Prima di intervenire su una repo:

1. leggere l'`AGENTS.md` della repo bersaglio;
2. controllare `git status --short`;
3. leggere le fonti di verità indicate qui;
4. verificare lo stato reale del checkout;
5. censire funzioni, documenti, runbook, workflow e regole repo-specifiche già mature;
6. classificare gli extra prima di normalizzare: mantenere, promuovere ad Atlas, sostituire, mettere in backlog o rimuovere solo se duplicati/superati;
7. non applicare standard Atlas a repo esterne senza scope esplicito.

## Stato sintetico

| Progetto | Stato aggiornato | Stack/runtime | Git/GitHub | Source of truth | Vincoli forti | Prossima azione | Blocchi/rischi |
| --- | --- | --- | --- | --- | --- | --- | --- |
| Atlas | Meta-progetto docs-first stabile dopo primo giro, seconda ondata, consolidamento Sentinel, matrice health e primo ciclo manutenzione | Nessun runtime applicativo | Checkout attivo: `/Users/Matteo/Progetti/Atlas`; `main`; GitHub privata `max23468/Atlas`; nessuna PR aperta; Codex inbox issue `#3` | `AGENTS.md`, `README.md`, `piano-coordinamento-progetti.md`, `docs/INDEX.md`, questo registro, `docs/HEALTH.md`, `docs/MAINTENANCE.md`, `docs/STANDARDS.md`, `docs/SEMANTIC_CHECKLIST.md`, `docs/STANDARD_CANDIDATES.md`, `docs/PUBLISH_DEPLOY_RELEASE.md`, `docs/APPLYING_ATLAS.md`, `docs/NEXT_STEPS.md`, `docs/ROADMAP.md`, `docs/BACKLOG.md`, `docs/CONTEXT.md`, `docs/TOOLCHAIN.md`, `docs/DECISIONS.md`, `docs/decisions/`, `CHECKLIST-NUOVA-REPO.md` | Non è un prodotto applicativo; niente release/deploy; non applica piani ad altre repo senza richiesta; non trasforma debiti prodotto repo in prossimi passi Atlas | Scegliere solo manutenzione governance, audit read-only, cleanup o aggiornamenti Atlas salvo nuova richiesta esplicita su una repo | Alcune note storiche indicano `/Users/Matteo/Documents/Atlas`; in questo ambiente il checkout reale è `/Users/Matteo/Progetti/Atlas`; i workflow sono stati riavviati |
| Pratix | Seconda ondata completata; produzione SaaS matura pubblicata e verificata post dependency maintenance | TanStack Start, Node/npm, Vercel, Supabase | Nessuna PR aperta; inbox Codex `#34`; PR `#159` mergiata; Vercel production `READY` su commit `59fbb05`, `/` e `/novita` `200`; nessuna release SemVer richiesta dal dry-run | `AGENTS.md`; `docs/ROADMAP.md`; `docs/INDEX.md`; `docs/BACKLOG.md`; `docs/CONTEXT.md`; `docs/TOOLCHAIN.md`; `docs/DECISIONS.md`; `docs/DECISIONS_PENDING.md`; `docs/memory/`; `docs/decisions/`; `docs/guides/versioning-e-release.md`; `docs/guides/deploy.md` | UI italiana, glossary rigoroso, token semantici; non spostare verso VPS, Telegram o Cloudflare | Nessuna azione prodotto Atlas; solo audit read-only o aggiornamento stato con nuova conferma | Repo già matura; React Doctor dopo release minor; basename Markdown e modello decisionale riallineati |
| DocMolder | Seconda ondata completata; manutenzione tooling pubblicata su `main` senza release/deploy | Python `>=3.11`; CI anche `3.13`; runtime operativo/VPS preferito `3.13` | Nessuna PR aperta; PR `#168` mergiata con commit `c3aeb05`; branch remota rimossa; inbox Codex `#149` senza commenti aperti; run `Dependency Graph` cancellata nella finestra Actions | `AGENTS.md`; `docs/ROADMAP.md`; `docs/BACKLOG.md`; `docs/TOOLCHAIN.md`; `docs/decisions/`; `docs/MILESTONE_BOARD.md`; `docs/INDEX.md`; `docs/CONTEXT.md`; `docs/CODEX_TASK_PACKET.md`; `docs/RELEASE_PROCESS.md`; `docs/VERSIONING.md`; `docs/VPS_RUNBOOK.md` | Telegram-first; documenti utente sensibili; non trasformare in web app o processo release manuale | Audit read-only e ricontrollo dello stato GitHub prima del prossimo lavoro DocMolder | `Release Please` e `VPS Check` riavviati; mantenere Release Please/VPS come policy repo-specifica |
| FiscalBay | Seconda ondata completata; manutenzione tooling pubblicata su `main` senza release/deploy VPS | Supporto Python dichiarato `>=3.10`; VPS operativa `3.13` come compatibilità runtime controllata | Nessuna PR aperta; PR `#80` mergiata con commit `d67c912`; branch remota rimossa; inbox Codex `#69` senza thread actionable; run `Dependency Graph` cancellata nella finestra Actions | `AGENTS.md`; `docs/ROADMAP.md`; `docs/BACKLOG.md`; `docs/TOOLCHAIN.md`; `docs/decisions/`; `docs/MILESTONE_BOARD.md`; `docs/INDEX.md`; `docs/CONTEXT.md`; `docs/RELEASE_POLICY.md`; `docs/OPERATIONS.md`; `docs/RUNBOOK.md`; `docs/DECISIONS_PENDING.md` | Non dedurre dati fiscali eBay assenti; non usare sintassi o dipendenze `>3.10` finché manifest/CI non cambiano | Nessuna azione prodotto Atlas; upgrade Python o deploy VPS solo con scope FiscalBay esplicito | Non confondere compatibilità runtime VPS `3.13` con obbligo di rompere supporto `>=3.10` |
| GLM | Primo allineamento Atlas completato; dependency maintenance pubblicata e deploy Cloudflare completato | React/Vite/TypeScript; Cloudflare Pages; Git LFS per allegati gara | Nessuna PR aperta; PR `#12` mergiata; deploy Cloudflare Pages production su commit `0ad6a6a`; home e `/api/version` `200`; nessuna release SemVer richiesta dal dry-run | `AGENTS.md`; `README.md`; `docs/INDEX.md`; `docs/ROADMAP.md`; `docs/BACKLOG.md`; `docs/CONTEXT.md`; `docs/TOOLCHAIN.md`; `docs/DECISIONS.md`; `docs/DECISIONS_PENDING.md`; `docs/LOGICA_SIMULATORE.md`; `docs/guides/versioning-e-release.md`; `docs/guides/cloudflare-pages.md`; `docs/decisions/` | Non usare Vercel/Supabase; non modificare allegati gara o Git LFS senza richiesta; deploy solo con procedura Cloudflare esplicita; tag `vX.Y.Z` solo per release prodotto reale | Audit read-only e controllo Actions storico post-riavvio | Pattern maturi GLM da non perdere: logica simulatore, changelog frontend, runbook Cloudflare, separazione nome/URL, allegati Git LFS come fonti |
| SendChimp | Primo allineamento Atlas completato; dependency maintenance pubblicata e produzione Vercel verificata | Next.js/React, Vercel Functions Frankfurt, Neon Free/Postgres 17 Frankfurt, Neon Auth | Nessuna PR aperta; PR `#24` mergiata; Vercel production `READY`; `/api/health` `200`; `/` redirige a `/auth/sign-in` con esito `200`; nessuna release SemVer richiesta dal dry-run | `AGENTS.md`; `README.md`; `docs/INDEX.md`; `docs/ROADMAP.md`; `docs/BACKLOG.md`; `docs/TOOLCHAIN.md`; `docs/CONTEXT.md`; `docs/DECISIONS.md`; `docs/DECISIONS_PENDING.md`; `docs/decisions/`; `docs/guides/git-e-pubblicazione.md`; `docs/guides/versioning-e-release.md` | Vincolo free-tier; nessun invio WhatsApp reale; nessuna integrazione produttiva Meta/Mailchimp/Shopify senza piano; nessun Supabase nel primo scaffold; tag/GitHub Release solo per release prodotto reale | Nessuna azione prodotto Atlas; verifiche provider solo se richieste come scope SendChimp | Verificare capienza residua dei piani gratuiti prima di confermare o modificare provider; deploy Vercel, release prodotto e invii reali restano separati |
| SyncBay | Primo allineamento Atlas completato; release locale `0.17.2` e deployment pilota Vercel pubblicati | Shopify app; eBay sorgente catalogo; Vercel/Supabase; Vercel automatico presente; tag/GitHub Release solo per release prodotto reale; App Store production non attivo | Nessuna PR aperta; PR `#48` mergiata; release PR `#50` mergiata con commit `b28ef47`; Vercel production `READY`; home/about/privacy `200`; inbox Codex `#2` senza commenti | `AGENTS.md`; `README.md`; `docs/INDEX.md`; `docs/ROADMAP.md`; `docs/BACKLOG.md`; `docs/CONTEXT.md`; `docs/TOOLCHAIN.md`; `docs/DECISIONS.md`; `docs/DECISIONS_PENDING.md`; `docs/decisions/`; `docs/guides/git-e-pubblicazione.md`; `docs/guides/versioning-e-release.md`; `docs/guides/provisioning-runtime.md` | Non trasformare in marketplace generico bidirezionale; App Store solo dopo decisione; tag/GitHub Release non implicano App Store, billing o integrazioni produttive | Nessuna azione prodotto Atlas; keyset/OAuth, import live o App Store solo se richiesti come scope SyncBay | React Doctor resta con warning diagnostici preesistenti; App Store/billing/support policy solo con decisione SyncBay |
| TRAM | Allineamento Atlas, React Doctor e dependency maintenance completati su `main` | Next.js 16, React 19, TypeScript, npm, Vitest, Python documentale `3.12` locale | Nessuna PR aperta; PR `#9` mergiata con commit `581dd43`; tag storico `v0.2.0`; nessun target deploy approvato; release non eseguita perché richiede richiesta esplicita | `AGENTS.md`; `README.md`; `docs/INDEX.md`; `docs/ROADMAP.md`; `docs/BACKLOG.md`; `docs/CONTEXT.md`; `docs/TOOLCHAIN.md`; `docs/OPERATIONS.md`; `docs/DECISIONS.md`; `docs/DECISIONS_PENDING.md`; `docs/decisions/` | Evidence-first; AI free-first e governata; basename Markdown univoci; non anticipare V2/V3; non inviare documenti sensibili a provider senza policy; release distinta da deploy | Nessuna azione prodotto Atlas; pilot/provider/hardening solo se richiesti come scope TRAM | `npm run verify` passa localmente; target deploy futuro tracciato in `docs/DECISIONS_PENDING.md`; verificata `Repo Hygiene` dopo riavvio |
| Sentinel | Consolidamento Atlas completato; dependency maintenance pubblicata, dashboard Vercel redeployata, runtime attivo | Node.js/TypeScript, CLI `sentinel`, config YAML, Vitest; output `data/`, `snapshots/`, `reports/` | GitHub privata `max23468/Sentinel`; nessuna PR aperta; PR `#8` mergiata con commit `fc41ca9`; dashboard Vercel production `READY`; Basic Auth `401` senza credenziali; runtime post-Actions attivo | `AGENTS.md`; `README.md`; `docs/INDEX.md`; `docs/ROADMAP.md`; `docs/BACKLOG.md`; `docs/CONTEXT.md`; `docs/TOOLCHAIN.md`; `docs/DECISIONS.md`; `docs/DECISIONS_PENDING.md`; `docs/decisions/`; `package.json`; `sentinel.config.yml`; `.github/workflows/sentinel.yml`; `src/` | Rispettare `robots.txt`; non committare segreti/email; non salvare HTML completo; output applicativi committabili dal workflow; tag/GitHub Release solo per tool/dashboard, non per scan/report | Workflow `Sentinel` riavviato e verificato; Monitor schedulato attivo; runtime post-Actions resta in `docs/DECISIONS_PENDING.md` |

## Ordine operativo corrente

Non partire da una repo applicativa senza nuova conferma esplicita sul target e senza usare questo registro come orientamento iniziale.

GLM, TRAM, SyncBay e SendChimp hanno completato il primo allineamento Atlas.
Pratix, DocMolder e FiscalBay hanno completato la seconda ondata.
Sentinel è stata tenuta alla fine e ha completato il consolidamento baseline runtime.

Le prossime direzioni possibili, da confermare esplicitamente, sono:

1. manutenzione governance Atlas o audit read-only quando emerge un nuovo segnale;
2. preparare un pacchetto di lavoro per una repo solo dopo richiesta esplicita su target e scope.

La seconda ondata completata è stata:

1. Pratix;
2. DocMolder;
3. FiscalBay.

Questo ordine non è autorizzazione automatica a modificare quelle repo: serve una nuova conferma esplicita sul target.

## Regole di manutenzione

- Aggiornare questo registro quando cambia stato operativo, stack/runtime, Git/GitHub, source of truth, vincolo forte, prossimo passo o blocco.
- Separare sempre dato verificato, snapshot storico e inferenza.
- Se un'informazione dipende da provider, piani free-tier, API, prezzi o limiti, verificarla prima di usarla come base decisionale.
- Se una repo ha file locali non tracciati o copie accidentali, non toccarli senza scope.
- Non copiare segreti, cache, dati applicativi reali o documenti sensibili dentro Atlas.
