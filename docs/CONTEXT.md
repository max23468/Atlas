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

Obiettivo corrente: usare Atlas come cabina di regia dopo i pilot GLM e TRAM, scegliendo una sola prossima repo alla volta e verificando sempre gli extra repo-specifici prima di normalizzare.

Il registro vivo dei progetti coordinati è `docs/PROJECTS.md`.

## Snapshot aggiornato 2026-05-24

- Atlas: repository GitHub privata `https://github.com/max23468/Atlas`, branch `main`, baseline GitHub leggera.
- DocMolder: repo Git su `main`; `pyproject.toml` richiede Python `>=3.11`, CI testa `3.11`, `3.12` e `3.13`, documentazione runtime preferisce Python `3.13`. Nel checkout attivo non risulta il vecchio file locale non tracciato `deploy/install-python313 2.sh`; non toccare comunque ambienti o file ignorati senza scope.
- FiscalBay: repo Git su `main`; runtime VPS documentato a Python `3.13`, ma `pyproject.toml`, `ruff`, `mypy` e GitHub Actions restano su Python `3.10`. Trattare l'upgrade come stato misto: non usare sintassi o dipendenze `>3.10` finché manifest, CI e policy non sono aggiornati.
- GLM: primo allineamento Atlas completato e mergiato su `main` con PR `max23468/Gare-Lotti-Milanesi#7`; aggiunti documenti canonici, baseline GitHub, roadmap/backlog maturi e discovery dei pattern specifici GLM. Nessun deploy produzione eseguito.
- TRAM: allineamento Atlas completato e mergiato su `main` con PR `max23468/TRAM#7`; roadmap migrata in `docs/ROADMAP.md`, aggiunti `docs/BACKLOG.md`, `docs/TOOLCHAIN.md` e template ADR `docs/decisions/0000-template.md`. Quality, hygiene, PR title e Codex sync passati; nessun deploy o release.
- SyncBay: allineamento Atlas completato e mergiato su `main` con PR `max23468/SyncBay#27` e `#28`; aggiunti documenti canonici, backlog, toolchain, context uppercase, fix Docker Node 24 e inbox Codex pulita. Vercel automatico passato; nessuna release locale 0.6.0 eseguita.
- SendChimp: non è più solo documentazione; ha scaffold runtime Next.js/React su Vercel, Neon Free/Postgres 17 e Neon Auth. Resta MVP manuale, senza invii WhatsApp automatici e con vincolo free-tier.
- Sentinel: repo GitHub privata `max23468/Sentinel`, branch `main`, commit ultimo verificato `e1de497 chore: update sentinel outputs`; workflow `Sentinel` schedulato/dispatch con Node 22, test, build, scan e commit degli output `data/`, `snapshots/`, `reports/`. Ultimo run manuale visto: `26367301441`, fallito sul commit `785808b` nello step `Fail on scan errors` dopo test, build, scan e commit output; il report `reports/ortix-20260524T165908Z.md` registra 8 cambiamenti, 34 problemi e fatale `SENTINEL_EMAIL_FROM` mancante. Trattarlo come operativo ma non verde.

## Vincoli specifici

- Non applicare il piano alle altre repo finché Atlas non è stabile.
- Non trattare Atlas come prodotto applicativo.
- Non introdurre release o deploy finché non c'è decisione esplicita.
- Non confondere i template con i documenti canonici reali.
- Non perdere contenuti durante migrazioni o uniformazioni.
- Prima di applicare template Atlas a una repo, censire funzioni, documenti, runbook, workflow e regole già mature; classificare ogni extra prima di mantenerlo, promuoverlo, sostituirlo, metterlo in backlog o rimuoverlo.
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
5. leggere `docs/INDEX.md`, `docs/PROJECTS.md`, `docs/ROADMAP.md`, `docs/BACKLOG.md`, `docs/CONTEXT.md` e `docs/TOOLCHAIN.md`;
6. verificare che la richiesta riguardi Atlas e non applichi implicitamente cambiamenti ad altre repo;
7. identificare verifiche proporzionate.

Durante handoff e migrazioni, non perdere contenuti: se una nota viene spostata, indicare nuova posizione o motivo della rimozione.

## Rischi aperti

- Iniziare interventi repo-per-repo senza conferma esplicita del target e senza usare `docs/PROJECTS.md`.
- Creare documenti doppi con stesso scopo.
- Rendere Atlas troppo pesante rispetto al suo ruolo di cabina di regia.
- Trasformare vincoli repo-specifici in standard generici sbagliati.
- Perdere comportamenti o documenti maturi di una repo perché non erano previsti nel template minimo Atlas.
- Confondere publish, deploy e release nelle repo coordinate.

## Prossimo passo

- Scegliere esplicitamente la prossima repo dopo GLM/TRAM/SyncBay.
- Valutare se creare una Codex feedback inbox per Atlas quando iniziano PR o commenti operativi ricorrenti.
