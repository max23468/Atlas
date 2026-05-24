# Registro progetti Atlas

Data ultimo aggiornamento: 2026-05-24

Questo registro è la matrice viva dei progetti coordinati da Atlas. Serve a orientare lo stato operativo, non a sostituire l'`AGENTS.md` o i documenti canonici delle singole repo.

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
| Atlas | Meta-progetto docs-first stabile dopo pilot GLM | Nessun runtime applicativo | Checkout attivo: `/Users/Matteo/Progetti/Atlas`; `main`; GitHub privata `max23468/Atlas` | `AGENTS.md`, `README.md`, `piano-coordinamento-progetti.md`, `docs/INDEX.md`, questo registro, `docs/ROADMAP.md`, `docs/BACKLOG.md`, `docs/CONTEXT.md`, `docs/TOOLCHAIN.md`, `docs/decisions/` | Non è un prodotto applicativo; niente release/deploy; non applica piani ad altre repo senza richiesta | Scegliere esplicitamente la prossima repo dopo GLM, se il maintainer conferma | Alcune note storiche indicano `/Users/Matteo/Documents/Atlas`; in questo ambiente il checkout reale è `/Users/Matteo/Progetti/Atlas` |
| Pratix | Produzione SaaS matura | TanStack Start, Node/npm, Vercel, Supabase | GitHub + Vercel production; policy repo-specifica da verificare nel checkout | `AGENTS.md`; `docs/memory/roadmap.md`; `docs/memory/README.md`; `docs/decisions/`; `docs/guides/versioning-e-release.md`; `docs/guides/deploy.md` | UI italiana, glossary rigoroso, token semantici; non spostare verso VPS, Telegram o Cloudflare | Seconda ondata: rifinire solo gap reali e migrare roadmap/indice/backlog/toolchain se confermato | Rischio di appesantire una repo già matura; React Doctor obbligatorio dopo release minor |
| DocMolder | Produzione operativa Telegram/VPS | Python `>=3.11`; CI anche `3.13`; runtime operativo/VPS preferito `3.13` | Release Please, GitHub Release, VPS/webhook | `AGENTS.md`; `docs/ROADMAP.md`; `docs/MILESTONE_BOARD.md`; `docs/INDEX.md`; `docs/CONTEXT.md`; `docs/CODEX_TASK_PACKET.md`; `docs/RELEASE_PROCESS.md`; `docs/VERSIONING.md`; `docs/VPS_RUNBOOK.md` | Telegram-first; documenti utente sensibili; non trasformare in web app o processo release manuale | Seconda ondata: creare `docs/BACKLOG.md`, `docs/TOOLCHAIN.md` e migrare decisioni con cautela | Checkout Git pulito; non toccare file ignorati di ambiente locale senza scope |
| FiscalBay | Operativo Telegram/eBay/VPS con upgrade Python incompleto | Runtime VPS documentato `3.13`; manifest, ruff, mypy e GitHub Actions ancora `3.10` | Deploy/release scriptati, fuori da GitHub Actions generiche | `AGENTS.md`; `docs/ROADMAP.md`; `docs/MILESTONE_BOARD.md`; `docs/INDEX.md`; `docs/CONTEXT.md`; `docs/RELEASE_POLICY.md`; `docs/OPERATIONS.md`; `docs/RUNBOOK.md`; `docs/DECISIONS_PENDING.md` | Non dedurre dati fiscali eBay assenti; non usare sintassi o dipendenze `>3.10` finché manifest/CI non cambiano | Seconda ondata: creare `docs/BACKLOG.md`, `docs/TOOLCHAIN.md`, `docs/decisions/README.md` e template | Stato Python misto: non considerare l'upgrade completato |
| GLM | Primo allineamento Atlas completato e mergiato su `main` | React/Vite/TypeScript; Cloudflare Pages; Git LFS per allegati gara | CI + Codex inbox; PR template, issue template minima e `pr-title.yml` presenti dopo PR `max23468/Gare-Lotti-Milanesi#7` | `AGENTS.md`; `README.md`; `docs/INDEX.md`; `docs/ROADMAP.md`; `docs/BACKLOG.md`; `docs/CONTEXT.md`; `docs/TOOLCHAIN.md`; `docs/LOGICA_SIMULATORE.md`; `docs/guides/versioning-e-release.md`; `docs/guides/cloudflare-pages.md`; `docs/decisions/` | Non usare Vercel/Supabase; non modificare allegati gara o Git LFS senza richiesta; deploy solo con procedura Cloudflare esplicita | Scegliere un debito prodotto/tecnico reale solo con nuova conferma: fonti pubbliche, import/export o ADR Cloudflare-only | Pattern maturi GLM da non perdere: logica simulatore, changelog frontend, runbook Cloudflare, separazione nome/URL, allegati Git LFS come fonti |
| SendChimp | Runtime Next.js iniziale / MVP manuale | Next.js/React, Vercel Functions Frankfurt, Neon Free/Postgres 17 Frankfurt, Neon Auth | GitHub + Vercel previsto/protetto; PR template, issue template, `pr-title.yml` e workflow Codex presenti nel checkout | `AGENTS.md`; `docs/context.md`; `docs/decisions/`; `docs/decisions-pending.md`; `docs/guides/git-e-pubblicazione.md`; `docs/guides/versioning-e-release.md` | Vincolo free-tier; nessun invio WhatsApp reale; nessuna integrazione produttiva Meta/Mailchimp/Shopify senza piano; nessun Supabase nel primo scaffold | Prima ondata, priorità 4: migrare roadmap/indice/backlog/toolchain senza perdere decisioni runtime | Checkout Git pulito; verificare capienza residua dei piani gratuiti prima di confermare provider |
| SyncBay | Scaffold runtime / MVP Shopify | Shopify app; eBay sorgente catalogo; Vercel/Supabase previsti ma production non attiva | GitHub/CI minima e publish policy da completare | `AGENTS.md`; `docs/context.md`; `docs/decisions/`; `docs/decisions-pending.md`; `docs/guides/git-e-pubblicazione.md`; `docs/guides/versioning-e-release.md`; `docs/guides/provisioning-runtime.md` | Non trasformare in marketplace generico bidirezionale; App Store solo dopo decisione | Prima ondata, priorità 3: roadmap/indice/backlog/toolchain e policy publish | Production deploy non deciso |
| TRAM | MVP iniziale interno | JavaScript/npm; AI/documenti gara con policy da confermare | GitHub al massimo; release/deploy policy assente | `AGENTS.md`; `docs/INDEX.md`; `docs/CONTEXT.md`; `docs/OPERATIONS.md`; decisioni da consolidare in `docs/decisions/` | Evidence-first; AI free-first e governata; non anticipare V2/V3; non inviare documenti sensibili a provider senza policy | Prima ondata, priorità 2: migrare roadmap, creare backlog/toolchain e chiarire versioning futuro | Policy release/deploy non ancora definita |
| Sentinel | Progetto nascente, repo Git locale senza commit | Node.js/TypeScript, CLI `sentinel`, config YAML, Vitest; primo monitor Ortix | `/Users/Matteo/Progetti/Sentinel`; branch `main`; nessun commit; nessun remote; scaffold non tracciato | `AGENTS.md` e `package.json` locali non tracciati; `sentinel.config.yml`; `src/`; nessun documento canonico `docs/` | Rispettare `robots.txt`; non committare segreti/email; non salvare HTML completo; `data/`, `snapshots/`, `reports/` sono output applicativi | Decidere separatamente se trasformare lo scaffold non tracciato in baseline iniziale con commit, GitHub e GitHub Actions | Non è un normale intervento di allineamento su repo esistente: prima va confermato cosa tracciare e dove pubblicare |

## Ordine operativo corrente

Non partire da una repo applicativa senza nuova conferma esplicita sul target e senza usare questo registro come orientamento iniziale.

GLM ha completato il primo pilot di allineamento. Per applicare Atlas alla prossima repo esistente già pulita, l'ordine candidato diventa:

1. TRAM;
2. SyncBay;
3. SendChimp.

Sentinel è separata dall'ordine ordinario: è una baseline iniziale di nuovo progetto, da decidere prima di qualunque commit o GitHub setup.

La seconda ondata proposta resta:

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
