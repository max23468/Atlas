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
| Atlas | Meta-progetto docs-first stabile dopo primo giro, seconda ondata, consolidamento Sentinel, matrice health e primo ciclo manutenzione | Nessun runtime applicativo | Checkout attivo: `/Users/Matteo/Progetti/Atlas`; `main`; GitHub privata `max23468/Atlas` | `AGENTS.md`, `README.md`, `piano-coordinamento-progetti.md`, `docs/INDEX.md`, questo registro, `docs/HEALTH.md`, `docs/MAINTENANCE.md`, `docs/STANDARDS.md`, `docs/STANDARD_CANDIDATES.md`, `docs/PUBLISH_DEPLOY_RELEASE.md`, `docs/APPLYING_ATLAS.md`, `docs/NEXT_STEPS.md`, `docs/ROADMAP.md`, `docs/BACKLOG.md`, `docs/CONTEXT.md`, `docs/TOOLCHAIN.md`, `docs/decisions/`, `CHECKLIST-NUOVA-REPO.md` | Non è un prodotto applicativo; niente release/deploy; non applica piani ad altre repo senza richiesta; non trasforma debiti prodotto repo in prossimi passi Atlas | Scegliere solo manutenzione governance, audit read-only, cleanup o aggiornamenti Atlas salvo nuova richiesta esplicita su una repo | Alcune note storiche indicano `/Users/Matteo/Documents/Atlas`; in questo ambiente il checkout reale è `/Users/Matteo/Progetti/Atlas` |
| Pratix | Seconda ondata completata; produzione SaaS matura pubblicata con release patch `1.11.15` | TanStack Start, Node/npm, Vercel, Supabase | PR `max23468/Pratix#156` mergiata; Vercel production verificata con `publish:finish` | `AGENTS.md`; `docs/ROADMAP.md`; `docs/INDEX.md`; `docs/BACKLOG.md`; `docs/CONTEXT.md`; `docs/TOOLCHAIN.md`; `docs/memory/`; `docs/decisions/`; `docs/guides/versioning-e-release.md`; `docs/guides/deploy.md` | UI italiana, glossary rigoroso, token semantici; non spostare verso VPS, Telegram o Cloudflare | Nessuna azione prodotto Atlas; solo audit read-only o aggiornamento stato con nuova conferma | Rischio di appesantire una repo già matura; React Doctor obbligatorio dopo release minor |
| DocMolder | Seconda ondata completata; produzione operativa Telegram/VPS pubblicata come docs-only | Python `>=3.11`; CI anche `3.13`; runtime operativo/VPS preferito `3.13` | PR `max23468/DocMolder#166` mergiata; release/deploy non eseguiti perché docs-only | `AGENTS.md`; `docs/ROADMAP.md`; `docs/BACKLOG.md`; `docs/TOOLCHAIN.md`; `docs/decisions/`; `docs/MILESTONE_BOARD.md`; `docs/INDEX.md`; `docs/CONTEXT.md`; `docs/CODEX_TASK_PACKET.md`; `docs/RELEASE_PROCESS.md`; `docs/VERSIONING.md`; `docs/VPS_RUNBOOK.md` | Telegram-first; documenti utente sensibili; non trasformare in web app o processo release manuale | Nessuna azione prodotto Atlas; solo audit read-only o aggiornamento stato con nuova conferma | Non toccare file ignorati di ambiente locale senza scope; mantenere Release Please/VPS come policy repo-specifica |
| FiscalBay | Seconda ondata completata; operativo Telegram/eBay/VPS con fix deploy pubblicato | Supporto Python dichiarato `>=3.10`; VPS operativa `3.13` come compatibilità runtime controllata | PR `max23468/FiscalBay#78` mergiata; thread Codex P1 risolto; inbox `#69` senza actionable; deploy/release non eseguiti in questo ciclo | `AGENTS.md`; `docs/ROADMAP.md`; `docs/BACKLOG.md`; `docs/TOOLCHAIN.md`; `docs/decisions/`; `docs/MILESTONE_BOARD.md`; `docs/INDEX.md`; `docs/CONTEXT.md`; `docs/RELEASE_POLICY.md`; `docs/OPERATIONS.md`; `docs/RUNBOOK.md`; `docs/DECISIONS_PENDING.md` | Non dedurre dati fiscali eBay assenti; non usare sintassi o dipendenze `>3.10` finché manifest/CI non cambiano | Nessuna azione prodotto Atlas; upgrade Python solo se richiesto come scope FiscalBay | Non confondere compatibilità runtime VPS `3.13` con obbligo di rompere supporto `>=3.10` |
| GLM | Primo allineamento Atlas completato e mergiato su `main` | React/Vite/TypeScript; Cloudflare Pages; Git LFS per allegati gara | CI + Codex inbox; PR template, issue template minima e `pr-title.yml` presenti dopo PR `max23468/Gare-Lotti-Milanesi#7` | `AGENTS.md`; `README.md`; `docs/INDEX.md`; `docs/ROADMAP.md`; `docs/BACKLOG.md`; `docs/CONTEXT.md`; `docs/TOOLCHAIN.md`; `docs/LOGICA_SIMULATORE.md`; `docs/guides/versioning-e-release.md`; `docs/guides/cloudflare-pages.md`; `docs/decisions/` | Non usare Vercel/Supabase; non modificare allegati gara o Git LFS senza richiesta; deploy solo con procedura Cloudflare esplicita | Nessuna azione prodotto Atlas; solo preservare/classificare pattern GLM con nuova conferma | Pattern maturi GLM da non perdere: logica simulatore, changelog frontend, runbook Cloudflare, separazione nome/URL, allegati Git LFS come fonti |
| SendChimp | Primo allineamento Atlas e correzione governance completati e mergiati su `main` | Next.js/React, Vercel Functions Frankfurt, Neon Free/Postgres 17 Frankfurt, Neon Auth | GitHub + Vercel; PR `max23468/SendChimp#20` e `#21` mergiate; Codex inbox pulita; Vercel production `Ready`, `/api/health` OK | `AGENTS.md`; `README.md`; `docs/INDEX.md`; `docs/ROADMAP.md`; `docs/BACKLOG.md`; `docs/TOOLCHAIN.md`; `docs/CONTEXT.md`; `docs/decisions/`; `docs/decisions-pending.md`; `docs/guides/git-e-pubblicazione.md`; `docs/guides/versioning-e-release.md` | Vincolo free-tier; nessun invio WhatsApp reale; nessuna integrazione produttiva Meta/Mailchimp/Shopify senza piano; nessun Supabase nel primo scaffold | Nessuna azione prodotto Atlas; verifiche provider solo se richieste come scope SendChimp | Verificare capienza residua dei piani gratuiti prima di confermare o modificare provider; nessun tag/GitHub Release, billing, provider nuovo o invio reale creato |
| SyncBay | Primo allineamento Atlas completato e release locale 0.6.0 pubblicata su `main` | Shopify app; eBay sorgente catalogo; Vercel/Supabase; Vercel automatico presente ma no tag/GitHub Release/App Store production | GitHub + Vercel; Codex inbox; Dependabot; PR `max23468/SyncBay#27`, `#28` e `#29` mergiate | `AGENTS.md`; `README.md`; `docs/INDEX.md`; `docs/ROADMAP.md`; `docs/BACKLOG.md`; `docs/CONTEXT.md`; `docs/TOOLCHAIN.md`; `docs/decisions/`; `docs/decisions-pending.md`; `docs/guides/git-e-pubblicazione.md`; `docs/guides/versioning-e-release.md`; `docs/guides/provisioning-runtime.md` | Non trasformare in marketplace generico bidirezionale; App Store solo dopo decisione; niente tag/GitHub Release finché la policy non cambia | Nessuna azione prodotto Atlas; keyset/OAuth o import live solo se richiesti come scope SyncBay | `docs/context.md` rinominato in `docs/CONTEXT.md`; su macOS non mantenere doppione per sola differenza di maiuscole |
| TRAM | Allineamento Atlas, React Doctor e policy release completati su `main` | Next.js 16, React 19, TypeScript, npm, Vitest, Python documentale `3.12` locale | GitHub privata `max23468/TRAM`; Quality, Repo Hygiene, PR Title, Codex inbox; PR `#6` e `#7` mergiate; commit release policy `783b783` `[skip ci]` | `AGENTS.md`; `README.md`; `docs/INDEX.md`; `docs/ROADMAP.md`; `docs/BACKLOG.md`; `docs/CONTEXT.md`; `docs/TOOLCHAIN.md`; `docs/OPERATIONS.md`; `docs/DECISIONS.md`; `docs/decisions/` | Evidence-first; AI free-first e governata; basename Markdown univoci; non anticipare V2/V3; non inviare documenti sensibili a provider senza policy; release distinta da deploy | Nessuna azione prodotto Atlas; pilot/provider/hardening solo se richiesti come scope TRAM | Nessun target deploy approvato: non deployare TRAM finché manca runbook/target |
| Sentinel | Consolidamento Atlas completato; monitor GitHub Actions sospeso per budget | Node.js/TypeScript, CLI `sentinel`, config YAML, Vitest; output `data/`, `snapshots/`, `reports/` | `/Users/Matteo/Progetti/Sentinel`; `main`; GitHub privata `max23468/Sentinel`; PR `max23468/Sentinel#1` e `#2` mergiate; workflow runtime `Sentinel` disabilitato manualmente; ultimo output commit `4b9d151` | `AGENTS.md`; `README.md`; `docs/INDEX.md`; `docs/ROADMAP.md`; `docs/BACKLOG.md`; `docs/CONTEXT.md`; `docs/TOOLCHAIN.md`; `docs/decisions/`; `package.json`; `sentinel.config.yml`; `.github/workflows/sentinel.yml`; `src/` | Rispettare `robots.txt`; non committare segreti/email; non salvare HTML completo; output applicativi committabili dal workflow | Riabilitare il workflow `Sentinel` solo quando i minuti Actions tornano disponibili o quando esiste runtime alternativo | Ortix ha 33 avvisi 404 ma 0 cambiamenti; monitor schedulato sospeso per non consumare Actions |

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
