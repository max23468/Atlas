# Contesto operativo Atlas

## Stato progetto

- Fase: docs-first / coordinamento operativo.
- Ultima versione/release: non applicabile.
- Ultimo deploy: non applicabile.
- Git: repository locale su branch `main`.
- GitHub: repository pubblica `https://github.com/max23468/Atlas`.

Atlas è la cabina di regia dei progetti locali. Coordina standard,
governance, template, matrici, publish/deploy/release, verifiche,
documentazione, handoff e policy trasversali senza sostituire gli `AGENTS.md`
repo-specifici.

## Fonte di verità

- Piano principale: `piano-coordinamento-progetti.md`.
- Indice documentale: `docs/INDEX.md`.
- Registro progetti: `docs/PROJECTS.md`.
- Matrice health: `docs/HEALTH.md`.
- Manutenzione: `docs/MAINTENANCE.md`.
- Standard Atlas: `docs/STANDARDS.md`.
- Pattern candidati: `docs/STANDARD_CANDIDATES.md`.
- Checklist semantica: `docs/SEMANTIC_CHECKLIST.md`.
- Publish/deploy/release: `docs/PUBLISH_DEPLOY_RELEASE.md`.
- Applicazione Atlas: `docs/APPLYING_ATLAS.md`.
- Prossimi passi Atlas: `docs/NEXT_STEPS.md`.
- Roadmap e backlog: `docs/ROADMAP.md`, `docs/BACKLOG.md`.
- Toolchain: `docs/TOOLCHAIN.md`.
- Decisioni: `docs/DECISIONS.md` e `docs/decisions/`.
- Regole operative: `AGENTS.md`.
- Template e checklist: file `*.template.md`,
  `CHECKLIST-IMPLEMENTAZIONE.md`, `CHECKLIST-MANUTENZIONE.md`,
  `CHECKLIST-NUOVA-REPO.md`.

## Stato del rollout trasversale

Il rollout corrente normalizza progressivamente governance e documentazione
delle repo coordinate con audit read-only, decisioni esplicite, modifiche
granulari, PR/merge e cleanup prima di passare alla sezione successiva.

Sezioni già pubblicate:

- regole operative generali e `AGENTS.md`;
- catalogo documentazione;
- roadmap;
- backlog;
- ADR e lifecycle decisionale.

Sezione corrente:

- handoff e contesto persistente.

Le repo coordinate sono: Atlas, Pratix, DocMolder, FiscalBay, GLM, SendChimp,
SyncBay, TRAM e Sentinel.

## Snapshot corrente

- Atlas: governance docs-first; release e deploy non applicabili.
- Pratix: SaaS operativo su Vercel/Supabase; versione da `src/lib/version.ts`.
- DocMolder: bot Telegram-first stabile `1.x`, release manuale e deploy VPS via
  webhook privato; contesto da mantenere sintetico.
- FiscalBay: servizio Telegram-first pubblico con accesso approvato, VPS
  `fiscalbay-bot`, release/deploy tramite script locali/VPS.
- GLM: app React/Vite su Cloudflare Pages; repository reale `max23468/GLM`;
  progetto Pages `gare-lotti-milanesi`; deploy con Wrangler quando richiesto.
- SendChimp: MVP manuale Next.js/Vercel con vincolo free-tier e ultimo miglio
  WhatsApp manuale.
- SyncBay: Shopify app su Vercel/Supabase; Vercel production pilota distinta da
  release pubblica Shopify App Store.
- TRAM: MVP iniziale Next.js/docs-governance; release SemVer `0.x` attiva con
  `v0.2.0`; nessun target deploy approvato.
- Sentinel: runtime MVP con GitHub Actions e dashboard Next.js/Vercel/Blob come
  canali distinti; React Doctor usa il comando di toolchain.

Per dettagli vivi leggere sempre i documenti della repo target, non questo
snapshot.

Prima di proporre o avviare lavoro prodotto nelle repo coordinate, controllare
sempre `docs/HEALTH.md` e `docs/PROJECTS.md`: Pratix, DocMolder, FiscalBay,
SyncBay, TRAM e Sentinel hanno stati `Attenzione` o gate P0/P1/P2 da rispettare
prima di nuove aperture funzionali, deploy, release o integrazioni operative.
Questa sintesi non sostituisce quei gate.

## Vincoli specifici

- Non applicare il piano alle altre repo senza richiesta esplicita e scope
  operativo chiaro.
- Non trattare Atlas come prodotto applicativo.
- Non proporre sviluppo prodotto delle repo coordinate come prossimo passo Atlas
  se l'utente non indica repo target e scope.
- Non introdurre release o deploy Atlas finché non c'è decisione esplicita.
- Non confondere template con documenti canonici reali.
- Non perdere contenuti durante migrazioni o uniformazioni.
- Prima di applicare pattern Atlas a una repo, censire funzioni, documenti,
  runbook, workflow e regole già mature; classificare ogni extra prima di
  mantenerlo, promuoverlo, sostituirlo, metterlo in backlog o rimuoverlo.
- Rispettare sempre l'`AGENTS.md` della repo bersaglio prima di qualunque
  intervento fuori da Atlas.
- Per modifiche Atlas su repo coordinate, usare branch dedicata; usare worktree
  separato quando il checkout non è pulito, il lavoro è lungo o ci sono più repo
  in parallelo.

## Verifiche da ricordare

- `git status --short`: se Atlas è una repo Git; se non lo è, dichiararlo.
- `git branch --show-current`: confermare branch corrente.
- `git remote -v`: confermare remote GitHub.
- `rg --files`: inventario rapido file.
- Controllo manuale link e coerenza tra documenti canonici.
- Verifica che `.DS_Store` non sia trattato come contenuto progettuale.

## Handoff per nuova chat

Prima di procedere:

1. leggere `AGENTS.md`;
2. controllare `git status --short` e `git remote -v`;
3. leggere `README.md`;
4. leggere `piano-coordinamento-progetti.md`;
5. leggere `docs/INDEX.md`, `docs/PROJECTS.md`, `docs/HEALTH.md`,
   `docs/MAINTENANCE.md`, `docs/STANDARDS.md`, `docs/ROADMAP.md`,
   `docs/BACKLOG.md`, `docs/CONTEXT.md` e `docs/TOOLCHAIN.md`;
6. leggere `docs/APPLYING_ATLAS.md`, `docs/NEXT_STEPS.md`,
   `docs/PUBLISH_DEPLOY_RELEASE.md` e `docs/STANDARD_CANDIDATES.md` quando la
   richiesta riguarda interventi repo-per-repo, prossimi passi, publish,
   deploy, release o promozione di pattern;
7. verificare che la richiesta riguardi Atlas o che autorizzi esplicitamente le
   repo coordinate;
8. identificare verifiche proporzionate.

Durante handoff e migrazioni, non perdere contenuti: se una nota viene spostata,
indicare nuova posizione o motivo della rimozione.

## Rischi aperti

- Iniziare interventi repo-per-repo senza target e scope espliciti.
- Suggerire feature, pilot, hardening, provider o import/export di una repo come
  prossimo passo Atlas invece di classificarli come debiti repo.
- Modificare repo coordinate direttamente su `main`/`master` invece di usare una
  branch dedicata o, quando necessario, un worktree separato.
- Creare documenti doppi con stesso scopo.
- Rendere Atlas troppo pesante rispetto al ruolo di cabina di regia.
- Trasformare vincoli repo-specifici in standard generici sbagliati.
- Perdere comportamenti o documenti maturi di una repo perché non erano previsti
  nel template minimo Atlas.
- Confondere publish, deploy e release nelle repo coordinate.

## Prossimo passo

Completare la sezione handoff e contesto sulle repo dove il context non è ancora
un punto di ingresso sintetico, poi pubblicare/mergeare e pulire branch e
worktree prima di procedere alla sezione successiva.
