# Contesto operativo Atlas

## Stato progetto

- Fase: docs-first / coordinamento operativo.
- Ultima versione/release: non applicabile.
- Ultimo deploy: non applicabile.
- Git: repository locale inizializzata su branch `main` il 2026-05-24.
- GitHub: repository privata `https://github.com/max23468/Atlas`.

## Fonte di verità

- Piano principale: `piano-coordinamento-progetti.md`
- Indice documentale: `docs/INDEX.md`
- Registro progetti: `docs/PROJECTS.md`
- Matrice health: `docs/HEALTH.md`
- Manutenzione: `docs/MAINTENANCE.md`
- Standard Atlas: `docs/STANDARDS.md`
- Pattern candidati: `docs/STANDARD_CANDIDATES.md`
- Publish/deploy/release: `docs/PUBLISH_DEPLOY_RELEASE.md`
- Applicazione Atlas: `docs/APPLYING_ATLAS.md`
- Roadmap: `docs/ROADMAP.md`
- Backlog: `docs/BACKLOG.md`
- Toolchain: `docs/TOOLCHAIN.md`
- Decisioni: `docs/decisions/`
- ADR fondative: `docs/decisions/0001-atlas-meta-progetto-leggero.md`, `docs/decisions/0002-struttura-canonica-root-docs.md`, `docs/decisions/0003-repository-github-privata.md`
- Regole operative: `AGENTS.md`
- Template: file `*.template.md`
- Checklist implementazione: `CHECKLIST-IMPLEMENTAZIONE.md`
- Checklist manutenzione: `CHECKLIST-MANUTENZIONE.md`
- Checklist nuova repo: `CHECKLIST-NUOVA-REPO.md`

## Ultimo contesto utile

Atlas nasce dalla ricognizione trasversale dei progetti locali e dal piano approvato in `piano-coordinamento-progetti.md`.

Obiettivo corrente: usare Atlas come cabina di regia dopo il primo giro GLM/TRAM/SyncBay/SendChimp, la seconda ondata Pratix/DocMolder/FiscalBay, il consolidamento Sentinel e la prima matrice health, scegliendo una sola prossima repo o fase alla volta e verificando sempre gli extra repo-specifici prima di normalizzare.

Il registro vivo dei progetti coordinati è `docs/PROJECTS.md`; lo snapshot
health sintetico è `docs/HEALTH.md`.

## Snapshot aggiornato 2026-05-26

- Atlas: repository GitHub privata `https://github.com/max23468/Atlas`, branch `main`, baseline GitHub leggera. Aggiunti `CHECKLIST-NUOVA-REPO.md`, `docs/APPLYING_ATLAS.md`, `docs/PUBLISH_DEPLOY_RELEASE.md` e `docs/STANDARD_CANDIDATES.md` per rendere più operativo il metodo Atlas.
- Pratix: seconda ondata completata con PR `max23468/Pratix#156`, release patch `1.11.15`, fix Codex P2 su `/novita`, documenti canonici Atlas e verifica Vercel production con `publish:finish`.
- DocMolder: seconda ondata completata con PR `max23468/DocMolder#166`; creati `docs/BACKLOG.md`, `docs/TOOLCHAIN.md`, `docs/decisions/README.md` e template ADR. Runtime dichiarato: Python `>=3.11`, CI anche `3.13`, runtime operativo/VPS preferito `3.13`. Release/deploy non eseguiti perché docs-only.
- FiscalBay: seconda ondata completata con PR `max23468/FiscalBay#78`; creati `docs/BACKLOG.md`, `docs/TOOLCHAIN.md`, `docs/decisions/README.md` e template ADR, risolto P1 Codex su `deploy/linux-setup.sh`. La policy repo-specifica dichiara supporto Python `>=3.10`, con VPS `3.13` come compatibilità runtime controllata; non forzare upgrade oltre `3.10` senza decisione repo-specifica.
- GLM: primo allineamento Atlas completato e mergiato su `main` con PR `max23468/Gare-Lotti-Milanesi#7`; aggiunti documenti canonici, baseline GitHub, roadmap/backlog maturi e discovery dei pattern specifici GLM. Nessun deploy produzione eseguito.
- TRAM: allineamento Atlas completato e mergiato su `main` con PR `max23468/TRAM#7`; fix React Doctor completato e mergiato con PR `max23468/TRAM#6`; policy SemVer/release definita con commit `783b783` `[skip ci]`. Roadmap migrata in `docs/ROADMAP.md`, aggiunti `docs/BACKLOG.md`, `docs/TOOLCHAIN.md` e template ADR `docs/decisions/0000-template.md`. Quality, hygiene, PR title, Codex sync e React Doctor `100 / 100` passati; nessun deploy perché manca target deploy approvato.
- SyncBay: allineamento Atlas completato e mergiato su `main` con PR `max23468/SyncBay#27`, `#28` e `#29`; aggiunti documenti canonici, backlog, toolchain, context uppercase, fix Docker Node 24, inbox Codex pulita e release locale 0.6.0 pubblicata. Vercel automatico passato; nessun tag, GitHub Release o App Store production.
- SendChimp: primo allineamento Atlas completato e mergiato su `main` con PR `max23468/SendChimp#20`; correzione governance completata con PR `#21`; roadmap migrata in `docs/ROADMAP.md`, indice in `docs/INDEX.md`, creati `docs/BACKLOG.md` e `docs/TOOLCHAIN.md`, rinvii compatibili da root `ROADMAP.md` e `docs/README.md`; chiuso il P1 Codex su `DATABASE_URL_UNPOOLED` vuota; Codex inbox pulita; Vercel production `Ready` e `/api/health` OK. Resta MVP manuale, senza invii WhatsApp automatici e con vincolo free-tier.
- Sentinel: consolidamento Atlas completato con PR `max23468/Sentinel#1` e Codex inbox con PR `#2`; commit documentale `40f1fac`, workflow manuale `26369906474` verde e output commit `4b9d151`. Creati `docs/INDEX.md`, `docs/ROADMAP.md`, `docs/BACKLOG.md`, `docs/CONTEXT.md`, `docs/TOOLCHAIN.md`, `docs/decisions/`, PR template, issue template e PR title check. Il run operativo su `main` ha scansionato Ortix e San Carlo Sviluppo: nessun cambiamento rilevato; Ortix mantiene 33 avvisi 404, San Carlo 0 problemi. Workflow runtime `Sentinel` disabilitato manualmente finché i minuti Actions sono esauriti.
- Health Atlas: creata e aggiornata `docs/HEALTH.md` come snapshot sintetico. Stato: verdi Atlas, Pratix, DocMolder, FiscalBay, GLM, SyncBay e TRAM; in attenzione SendChimp e Sentinel; nessun progetto bloccato.
- Primo ciclo manutenzione: audit read-only completato su FiscalBay, SendChimp, TRAM e Sentinel. Inboxes Codex pulite dove presenti, workflow recenti verdi, TRAM PR `#6` pubblicata e mergiata; nessun deploy/release eseguito.
- Ciclo correttivo standard Atlas: creata `docs/STANDARDS.md`; pubblicate uniformazioni sicure su SendChimp `#21`, Pratix `#157`, SyncBay `#30`, Sentinel `#2` e GLM commit `[skip ci]`. GitHub Actions non usate come gate dopo segnalazione budget esaurito; workflow `Codex PR comments` disabilitati manualmente su Pratix, DocMolder, FiscalBay, GLM, SendChimp, SyncBay, TRAM e Sentinel; workflow runtime `Sentinel` disabilitato manualmente; Dependabot su GLM/Sentinel resta sospeso.
- Chiusura gap senza Actions: TRAM ha policy release/versioning; FiscalBay è classificata come compatibilità Python intenzionale, non come mismatch da forzare.

## Vincoli specifici

- Non applicare il piano alle altre repo finché Atlas non è stabile.
- Non trattare Atlas come prodotto applicativo.
- Non introdurre release o deploy finché non c'è decisione esplicita.
- Non confondere i template con i documenti canonici reali.
- Non perdere contenuti durante migrazioni o uniformazioni.
- Prima di applicare template Atlas a una repo, censire funzioni, documenti, runbook, workflow e regole già mature; classificare ogni extra prima di mantenerlo, promuoverlo, sostituirlo, metterlo in backlog o rimuoverlo.
- Rispettare sempre l'`AGENTS.md` della repo bersaglio prima di qualunque intervento fuori da Atlas.
- Se la repo bersaglio non ha ancora `AGENTS.md` o non è una repo Git, fermarsi alla ricognizione e creare prima una baseline.
- Per modifiche Atlas su repo coordinate, usare sempre una branch dedicata; usare
  un worktree separato quando il checkout non è pulito, il lavoro è lungo o ci
  sono più repo in parallelo.
- Usare i subagent solo nella fase implementativa, con coordinamento centrale, prima passata read-only e una sola repo per volta in scrittura.

## Verifiche da ricordare

- `git status --short`: se Atlas è una repo Git; se non lo è, dichiarare lo stato.
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
5. leggere `docs/INDEX.md`, `docs/PROJECTS.md`, `docs/HEALTH.md`, `docs/MAINTENANCE.md`, `docs/STANDARDS.md`, `docs/ROADMAP.md`, `docs/BACKLOG.md`, `docs/CONTEXT.md` e `docs/TOOLCHAIN.md`;
6. leggere `docs/APPLYING_ATLAS.md`, `docs/PUBLISH_DEPLOY_RELEASE.md` e `docs/STANDARD_CANDIDATES.md` quando la richiesta riguarda interventi repo-per-repo, publish, deploy, release o promozione di pattern;
7. verificare che la richiesta riguardi Atlas e non applichi implicitamente cambiamenti ad altre repo;
8. identificare verifiche proporzionate.

Durante handoff e migrazioni, non perdere contenuti: se una nota viene spostata, indicare nuova posizione o motivo della rimozione.

## Rischi aperti

- Iniziare interventi repo-per-repo senza conferma esplicita del target e senza usare `docs/PROJECTS.md`.
- Modificare repo coordinate direttamente su `main`/`master` invece di usare una
  branch dedicata o, quando necessario, un worktree separato.
- Creare documenti doppi con stesso scopo.
- Rendere Atlas troppo pesante rispetto al suo ruolo di cabina di regia.
- Trasformare vincoli repo-specifici in standard generici sbagliati.
- Perdere comportamenti o documenti maturi di una repo perché non erano previsti nel template minimo Atlas.
- Confondere publish, deploy e release nelle repo coordinate.

## Prossimo passo

- Riabilitare i workflow `Codex PR comments` disabilitati manualmente solo quando i minuti GitHub Actions tornano disponibili.
- Riabilitare il workflow runtime `Sentinel` solo quando i minuti GitHub Actions tornano disponibili o quando viene scelto un runtime alternativo.
- Valutare se creare una Codex feedback inbox per Atlas quando iniziano PR o commenti operativi ricorrenti.
