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
- Roadmap: `docs/ROADMAP.md`
- Backlog: `docs/BACKLOG.md`
- Toolchain: `docs/TOOLCHAIN.md`
- Decisioni: `docs/decisions/`
- ADR fondative: `docs/decisions/0001-atlas-meta-progetto-leggero.md`, `docs/decisions/0002-struttura-canonica-root-docs.md`, `docs/decisions/0003-repository-github-privata.md`
- Regole operative: `AGENTS.md`
- Template: file `*.template.md`
- Checklist implementazione: `CHECKLIST-IMPLEMENTAZIONE.md`
- Checklist manutenzione: `CHECKLIST-MANUTENZIONE.md`

## Ultimo contesto utile

Atlas nasce dalla ricognizione trasversale dei progetti locali e dal piano approvato in `piano-coordinamento-progetti.md`.

Obiettivo corrente: usare Atlas come progetto stabile prima di applicare il piano a Pratix, DocMolder, FiscalBay, GLM, SendChimp, SyncBay, TRAM o Sentinel.

## Snapshot aggiornato 2026-05-24

- Atlas: repository GitHub privata `https://github.com/max23468/Atlas`, branch `main`, baseline GitHub leggera.
- DocMolder: repo Git su `main`; `pyproject.toml` richiede Python `>=3.11`, CI testa `3.11`, `3.12` e `3.13`, documentazione runtime preferisce Python `3.13`. Al controllo esisteva un file locale non tracciato `deploy/install-python313 2.sh`, da non toccare senza scope.
- FiscalBay: repo Git su `main`; runtime VPS documentato a Python `3.13`, ma `pyproject.toml`, `ruff`, `mypy` e GitHub Actions restano su Python `3.10`. Trattare l'upgrade come stato misto: non usare sintassi o dipendenze `>3.10` finché manifest, CI e policy non sono aggiornati.
- SendChimp: non è più solo documentazione; ha scaffold runtime Next.js/React su Vercel, Neon Free/Postgres 17 e Neon Auth. Resta MVP manuale, senza invii WhatsApp automatici e con vincolo free-tier.
- Sentinel: cartella locale presente, ma non è una repo Git locale e non risulta repository GitHub `max23468/Sentinel`; contiene solo cache `.wrangler`. Va censita o inizializzata prima di entrare nella matrice operativa.

## Vincoli specifici

- Non applicare il piano alle altre repo finché Atlas non è stabile.
- Non trattare Atlas come prodotto applicativo.
- Non introdurre release o deploy finché non c'è decisione esplicita.
- Non confondere i template con i documenti canonici reali.
- Non perdere contenuti durante migrazioni o uniformazioni.
- Rispettare sempre l'`AGENTS.md` della repo bersaglio prima di qualunque intervento fuori da Atlas.
- Se la repo bersaglio non ha ancora `AGENTS.md` o non è una repo Git, fermarsi alla ricognizione e creare prima una baseline.
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
5. leggere `docs/INDEX.md`, `docs/ROADMAP.md`, `docs/BACKLOG.md`, `docs/CONTEXT.md` e `docs/TOOLCHAIN.md`;
6. verificare che la richiesta riguardi Atlas e non applichi implicitamente cambiamenti ad altre repo;
7. identificare verifiche proporzionate.

Durante handoff e migrazioni, non perdere contenuti: se una nota viene spostata, indicare nuova posizione o motivo della rimozione.

## Rischi aperti

- Iniziare interventi repo-per-repo prima di chiudere il riallineamento dello snapshot 2026-05-24.
- Creare documenti doppi con stesso scopo.
- Rendere Atlas troppo pesante rispetto al suo ruolo di cabina di regia.
- Trasformare vincoli repo-specifici in standard generici sbagliati.
- Confondere publish, deploy e release nelle repo coordinate.

## Prossimo passo

- Chiudere e pubblicare il riallineamento dello snapshot 2026-05-24.
- Poi preparare la prima applicazione controllata del piano a una repo coordinata.
- Valutare se creare una Codex feedback inbox per Atlas quando iniziano PR o commenti operativi ricorrenti.
