# Registro progetti Atlas

Data ultimo aggiornamento: 2026-05-30

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
| Atlas | Meta-progetto docs-first stabile dopo primo giro, seconda ondata, consolidamento Sentinel, matrice health e primo ciclo manutenzione | Nessun runtime applicativo | Checkout reale: `/Users/Matteo/Progetti/Atlas`; branch principale `main`; GitHub privata `max23468/Atlas`; nessuna PR aperta; Codex inbox issue `#10` marcata `codex-feedback-inbox` | `AGENTS.md`, `README.md`, `piano-coordinamento-progetti.md`, `docs/INDEX.md`, questo registro, `docs/HEALTH.md`, `docs/MAINTENANCE.md`, `docs/STANDARDS.md`, `docs/SEMANTIC_CHECKLIST.md`, `docs/STANDARD_CANDIDATES.md`, `docs/PUBLISH_DEPLOY_RELEASE.md`, `docs/APPLYING_ATLAS.md`, `docs/NEXT_STEPS.md`, `docs/ROADMAP.md`, `docs/BACKLOG.md`, `docs/CONTEXT.md`, `docs/TOOLCHAIN.md`, `docs/DECISIONS.md`, `docs/decisions/`, `CHECKLIST-NUOVA-REPO.md` | Non è un prodotto applicativo; niente release/deploy; non applica piani ad altre repo senza richiesta; non trasforma debiti prodotto repo in prossimi passi Atlas | Scegliere solo manutenzione governance, audit read-only, cleanup o aggiornamenti Atlas salvo nuova richiesta esplicita su una repo | Alcune note storiche indicano `/Users/Matteo/Documents/Atlas`; in questo ambiente il checkout reale è `/Users/Matteo/Progetti/Atlas`; i workflow sono stati riavviati; la inbox manuale `#3` è chiusa come duplicata di `#10` |
| Pratix | Hardening operativo bloccante in corso: obiettivo P0/P1 prima di aperture funzionali successive | TanStack Start, Node/npm, Vercel, Supabase | Nessuna PR aperta; inbox Codex `#163` marcata `codex-feedback-inbox`; PR `#159` chiusa; `SECURITY.md` + `docs/ROADMAP.md` + `docs/SECURITY_HARDENING.md` aggiornati il `2026-05-27`; Vercel production `READY` con commit `59fbb05`, `/` e `/novita` `200`; nessuna release SemVer richiesta dal dry-run | `AGENTS.md`; `docs/ROADMAP.md`; `docs/INDEX.md`; `docs/BACKLOG.md`; `docs/CONTEXT.md`; `docs/TOOLCHAIN.md`; `docs/DECISIONS.md`; `docs/DECISIONS_PENDING.md`; `docs/memory/`; `docs/decisions/`; `docs/guides/versioning-e-release.md`; `docs/guides/deploy.md`; `SECURITY.md`; `docs/SECURITY_HARDENING.md` | UI italiana, glossary rigoroso, token semantici; non spostare verso VPS, Telegram o Cloudflare | Bloccata apertura feature prima del completamento P0/P1; verifiche pre-merge su segreti e `.env` e aggiornamento roadmap | Rischi prioritari: esposizione `.env` storici, integrazioni esterne e controlli di sicurezza minimi; nessuna rotazione segreti prevista nel piano corrente |
| DocMolder | Hardening tecnico-operativo in corso; primo allineamento operativo riformulato per runbook | Python `>=3.11`; CI anche `3.13`; runtime operativo/VPS preferito `3.13` | Nessuna PR aperta; PR `#168` mergiata con commit `c3aeb05`; `docs/OPERATIONS_SECURITY.md` + `docs/SECURITY_HARDENING.md` aggiornati il `2026-05-27`; branch remota rimossa; inbox Codex `#149` senza commenti aperti; run `Dependency Graph` cancellata nella finestra Actions | `AGENTS.md`; `docs/ROADMAP.md`; `docs/BACKLOG.md`; `docs/TOOLCHAIN.md`; `docs/decisions/`; `docs/MILESTONE_BOARD.md`; `docs/INDEX.md`; `docs/CONTEXT.md`; `docs/CODEX_TASK_PACKET.md`; `docs/RELEASE_PROCESS.md`; `docs/VERSIONING.md`; `docs/VPS_RUNBOOK.md`; `docs/OPERATIONS_SECURITY.md`; `docs/SECURITY_HARDENING.md` | Telegram-first; documenti utente sensibili; non trasformare in web app o in un processo release manuale generico scollegato da `docs/RELEASE_PROCESS.md` e `docs/VPS_RUNBOOK.md` | Hardening checklist P0/P1 su pipeline/secret manager e dry-run prima di nuovo deploy | Workflow legacy di rilascio deprecato; mantenere policy release repo-specifica e `VPS Check` da runbook |
| FiscalBay | Hardening operativo P0/P1 avviato: separazione ambienti e runbook di incidente in corso | Python `3.13` come baseline unica; VPS operativa `fiscalbay-bot` | Nessuna PR aperta; PR di riallineamento Python `3.13` pubblicate; inbox Codex `#86` marcata `codex-feedback-inbox` senza thread actionable al controllo del ciclo toolchain | `AGENTS.md`; `docs/ROADMAP.md`; `docs/BACKLOG.md`; `docs/TOOLCHAIN.md`; `docs/decisions/`; `docs/MILESTONE_BOARD.md`; `docs/INDEX.md`; `docs/CONTEXT.md`; `docs/RELEASE_POLICY.md`; `docs/OPERATIONS.md`; `docs/RUNBOOK.md`; `docs/DECISIONS_PENDING.md`; `docs/SECURITY_HARDENING.md`; `docs/SECURITY_OPERATIONS.md` | Non dedurre dati fiscali eBay assenti; non aggiungere workflow Actions fuori allowlist; deploy/release passano da script locali/VPS | Hardening P0/P1 su segreti runtime, webhook/API e runbook di incidente prima di nuove modifiche operative sensibili | Tenere separati publish GitHub, deploy VPS e release versionata; non usare Actions come canale deploy |
| GLM | Primo allineamento Atlas completato; rischio basso e governance docs-first operativa | React/Vite/TypeScript; Cloudflare Pages; Git LFS per allegati gara | GitHub reale `max23468/GLM`; nessuna PR aperta; release GitHub `v1.8.4` presente; deploy Cloudflare Pages tramite progetto `gare-lotti-milanesi` quando richiesto | `AGENTS.md`; `README.md`; `docs/INDEX.md`; `docs/ROADMAP.md`; `docs/BACKLOG.md`; `docs/CONTEXT.md`; `docs/TOOLCHAIN.md`; `docs/DECISIONS.md`; `docs/DECISIONS_PENDING.md`; `docs/LOGICA_SIMULATORE.md`; `docs/guides/versioning-e-release.md`; `docs/guides/cloudflare-pages.md`; `docs/decisions/`; `docs/SECURITY_HARDENING.md` | Non usare Vercel/Supabase; non modificare allegati gara o Git LFS senza richiesta; deploy solo con procedura Cloudflare esplicita; tag `vX.Y.Z` solo per release prodotto reale | Audit read-only e controllo Actions storico post-riavvio; mantenere anti-deriva docs-first | Pattern maturi GLM da non perdere: logica simulatore, changelog frontend, runbook Cloudflare, separazione nome/URL, allegati Git LFS come fonti |
| SendChimp | Primo allineamento Atlas completato con hardening operativo aggiornato | Next.js/React, Vercel Functions Frankfurt, Neon Free/Postgres 17 Frankfurt, Neon Auth | Nessuna PR aperta; PR `#24` mergiata; `docs/SECURITY_HARDENING.md` aggiornato il `2026-05-27`; Vercel production `READY`; `/api/health` `200`; `/` redirige a `/auth/sign-in` con esito `200`; nessuna release SemVer richiesta dal dry-run | `AGENTS.md`; `README.md`; `docs/INDEX.md`; `docs/ROADMAP.md`; `docs/BACKLOG.md`; `docs/TOOLCHAIN.md`; `docs/CONTEXT.md`; `docs/DECISIONS.md`; `docs/DECISIONS_PENDING.md`; `docs/decisions/`; `docs/guides/git-e-pubblicazione.md`; `docs/guides/versioning-e-release.md`; `docs/SECURITY_HARDENING.md` | Vincolo free-tier; nessun invio WhatsApp reale; nessuna integrazione produttiva Meta/Mailchimp/Shopify senza piano; nessun Supabase nel primo scaffold; tag/GitHub Release solo per release prodotto reale | Nessuna azione prodotto Atlas; verifiche provider solo se richieste come scope SendChimp | Verificare capienza residua dei piani gratuiti prima di confermare o modificare provider; deploy Vercel, release prodotto e invii reali restano separati |
| SyncBay | Hardening tecnico-operativo P0/P1 in corso: credenziali/OAuth e webhook con verifica manuale | Shopify app; eBay sorgente catalogo; Vercel/Supabase; Vercel production pilota; tag/GitHub Release solo per release prodotto reale; App Store production non attivo | Nessuna PR aperta; Vercel production pilota `READY`; inbox Codex `#2` marcata `codex-feedback-inbox` senza commenti al controllo del ciclo toolchain | `AGENTS.md`; `README.md`; `docs/INDEX.md`; `docs/ROADMAP.md`; `docs/BACKLOG.md`; `docs/CONTEXT.md`; `docs/TOOLCHAIN.md`; `docs/DECISIONS.md`; `docs/DECISIONS_PENDING.md`; `docs/decisions/`; `docs/guides/git-e-pubblicazione.md`; `docs/guides/versioning-e-release.md`; `docs/guides/provisioning-runtime.md`; `docs/SECURITY_HARDENING.md`; `SECURITY.md` | Non trasformare in marketplace generico bidirezionale; App Store solo dopo decisione; tag/GitHub Release non implicano App Store, billing o integrazioni produttive | P0/P1: validare keyset separato, signature endpoint, checklist manuale per credenziali; nessuna apertura rapida fuori gate | Vercel production non equivale a Shopify App Store production; App Store/billing/support policy solo con decisione SyncBay |
| TRAM | Hardening tecnico-operativo in corso per P1/P2 su visibilità pubblica e artefatti | Next.js 16, React 19, TypeScript, npm, Vitest, Python documentale `3.12` locale | Nessuna PR aperta; tag/GitHub Release `v0.2.0`; nessun target deploy approvato | `AGENTS.md`; `README.md`; `docs/INDEX.md`; `docs/ROADMAP.md`; `docs/BACKLOG.md`; `docs/CONTEXT.md`; `docs/TOOLCHAIN.md`; `docs/OPERATIONS.md`; `docs/DECISIONS.md`; `docs/DECISIONS_PENDING.md`; `docs/decisions/`; `docs/SECURITY_HARDENING.md` | Evidence-first; AI free-first e governata; basename Markdown univoci; non anticipare V2/V3; non inviare documenti sensibili a provider senza policy; release distinta da deploy | Nessuna azione prodotto Atlas; pilot/provider/hardening solo se richiesti come scope TRAM | Release SemVer esiste ma non abilita deploy/hosting/provider; target deploy futuro tracciato in `docs/DECISIONS_PENDING.md` |
| Sentinel | Hardening P1/P2 in corso su runtime schedulato, env locali e retention | Node.js/TypeScript, CLI `sentinel`, config YAML, Vitest; output `data/`, `snapshots/`, `reports`; dashboard Next.js/Vercel/Blob | GitHub privata `max23468/Sentinel`; nessuna PR aperta; runtime GitHub Actions e dashboard Vercel/Blob documentati come canali separati | `AGENTS.md`; `README.md`; `docs/INDEX.md`; `docs/ROADMAP.md`; `docs/BACKLOG.md`; `docs/CONTEXT.md`; `docs/TOOLCHAIN.md`; `docs/DECISIONS.md`; `docs/DECISIONS_PENDING.md`; `docs/decisions/`; `package.json`; `sentinel.config.yml`; `.github/workflows/sentinel.yml`; `docs/SECURITY_HARDENING.md`; `src/` | Rispettare `robots.txt`; non committare segreti/email; non salvare HTML completo; output applicativi committabili dal workflow; tag/GitHub Release solo per tool/dashboard, non per scan/report | Workflow `Sentinel` schedulato/manuale e dashboard Vercel da CLI restano da controllare secondo il canale toccato | Non confondere scan/report con release tool/dashboard; non confondere runtime Actions con aggiornamento payload/dashboard Vercel |

## Ordine operativo corrente

Non partire da una repo applicativa senza nuova conferma esplicita sul target e senza usare questo registro come orientamento iniziale.

Ordine operativo hardening proposto (per prossimi passi espliciti): Pratix, FiscalBay, SyncBay, DocMolder, TRAM, Sentinel, SendChimp, GLM, Atlas.

Pratix resta bloccante finché non chiude P0/P1.

FiscalBay, SyncBay e DocMolder seguono a seconda di chiusura degli step P0/P1 e disponibilità di scope.

TRAM e Sentinel sono in consolidamento tecnico-operativo con rischio ridotto.

GLM e Atlas mantengono percorso docs-first senza rischio runtime diretto.

Le prossime direzioni possibili, da confermare esplicitamente, sono:

1. manutenzione governance Atlas o audit read-only quando emerge un nuovo segnale;
2. preparare un pacchetto di lavoro per una repo solo dopo richiesta esplicita su target e scope.
3. Pratix: in esecuzione hardening operativo, quindi si attende il completamento checklist prima di aprire altre repo.
4. FiscalBay, DocMolder, SyncBay, TRAM, Sentinel, SendChimp: in sequenza hardening P1/P2 con verifica esplicita prima di riattivare scope operativi.

Nessuna ondata può essere considerata definitivamente "chiusa" finché i check P0/P1 non sono completati nel repository target.

Questo ordine non è autorizzazione automatica a modificare quelle repo: serve una nuova conferma esplicita sul target.

## Regole di manutenzione

- Aggiornare questo registro quando cambia stato operativo, stack/runtime, Git/GitHub, source of truth, vincolo forte, prossimo passo o blocco.
- Separare sempre dato verificato, snapshot storico e inferenza.
- Se un'informazione dipende da provider, piani free-tier, API, prezzi o limiti, verificarla prima di usarla come base decisionale.
- Se una repo ha file locali non tracciati o copie accidentali, non toccarli senza scope.
- Non copiare segreti, cache, dati applicativi reali o documenti sensibili dentro Atlas.
