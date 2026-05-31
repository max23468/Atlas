# Manutenzione periodica Atlas

Questo documento definisce il ciclo operativo di manutenzione Atlas. La checklist
dettagliata resta `CHECKLIST-MANUTENZIONE.md`; questa pagina stabilisce ordine,
scope e output.

## Frequenza

- Ciclo completo: mensile o prima di un blocco operativo trasversale.
- Ciclo rapido: dopo publish, deploy, release o workflow operativo significativo
  in una repo coordinata.
- Ciclo mirato: su una sola repo quando `docs/HEALTH.md` la segnala in
  `Attenzione` o `Bloccato`.

## Ordine del ciclo completo

1. Atlas: verificare `git status`, documenti canonici, `docs/HEALTH.md`,
   `docs/STANDARDS.md`, `docs/STANDARD_CANDIDATES.md`,
   `docs/PUBLISH_DEPLOY_RELEASE.md`, `docs/NEXT_STEPS.md` e coerenza con
   `docs/PROJECTS.md`.
2. Repo in `Bloccato`: risolvere prima dei debiti ordinari.
3. Repo in `Attenzione`: fare audit read-only e promuovere solo problemi reali.
4. Repo in `Verde`: controllare solo segnali leggeri o debiti scelti.
5. Aggiornare `docs/HEALTH.md`, `docs/PROJECTS.md`, `docs/STANDARDS.md`,
   `docs/STANDARD_CANDIDATES.md`, `docs/PUBLISH_DEPLOY_RELEASE.md`,
   `docs/NEXT_STEPS.md`, `docs/ROADMAP.md` o `docs/BACKLOG.md` solo dove
   cambia lo stato.

## Audit read-only minimo

Per ogni repo controllata:

- `AGENTS.md`;
- `git status --short --branch`;
- branch corrente e remote;
- PR aperte;
- issue/inbox operative se presenti;
- workflow falliti recenti;
- documenti canonici e toolchain se il rischio riguarda governance o runtime.

## Criteri di intervento

- Fix immediato: bug piccolo, rischio basso, policy chiara e verifiche locali
  disponibili.
- Backlog: problema reale ma non urgente, oppure serve decisione prodotto,
  provider, release o deploy.
- Solo osservazione: warning noto, report non bloccante o rischio già descritto.
- Stop: dati sensibili, credenziali, deploy/release non richiesti o policy repo
  non chiara.

## Primo ciclo

Data: 2026-05-24

Scope:

- partire dalle repo in `Attenzione` in `docs/HEALTH.md`: FiscalBay, SendChimp,
  TRAM e Sentinel;
- non modificare codice applicativo senza evidenza concreta;
- registrare in Atlas eventuali cambi di stato o prossime azioni;
- lasciare le repo `Verde` senza audit pesante finché non c'è un debito scelto.

Output atteso:

- aggiornamento di `docs/HEALTH.md` se lo stato cambia;
- aggiornamento di `docs/BACKLOG.md` o `docs/ROADMAP.md` se emerge un debito
  trasversale;
- nessun deploy o release implicito.

Esito storico:

- FiscalBay: checkout pulito, nessuna PR aperta, inbox Codex senza thread
  actionable, workflow recenti verdi.
- SendChimp: checkout pulito, nessuna PR aperta, inbox Codex senza thread
  actionable, workflow recenti verdi.
- TRAM: checkout pulito dopo merge, inbox Codex senza thread actionable, PR
  `max23468/TRAM#6` pubblicata e mergiata con Quality, Repo Hygiene, PR Title e
  Codex sync verdi; React Doctor `100 / 100` verificato localmente.
- Sentinel: checkout pulito, nessuna PR o issue aperta, workflow recenti verdi;
  restano da osservare i report schedulati e gli avvisi 404 Ortix non bloccanti.
- Nessun deploy o release eseguito.

Questo esito è utile come traccia del primo passaggio, ma è stato superato
dall'audit completo del `2026-05-26`.

## Audit Codex feedback inbox del 2026-05-31

Esito aggiornato:

- Nessuna PR aperta su Atlas, Pratix, DocMolder, FiscalBay, GLM, SendChimp,
  SyncBay, TRAM e Sentinel.
- Le inbox Codex canoniche sono: Atlas `#10`, Pratix `#163`,
  DocMolder `#149`, FiscalBay `#86`, GLM `#14`, SendChimp `#2`,
  SyncBay `#2`, TRAM `#2`, Sentinel `#4`.
- Tutte le inbox risultano senza thread Codex actionable al momento del
  controllo.
- Il modello operativo è normalizzato sulla label `codex-feedback-inbox`.
  DocMolder mantiene varianti motivate nel workflow/handler per checkout PR-head
  e fallback API, senza uscire dallo standard.
- GLM resta con checkout principale sporco per lavoro utente separato; gli
  interventi Atlas vanno fatti da worktree dedicato fino a cleanup completato.
- Nessun deploy o release Atlas eseguito in questo audit.

## Snapshot storico del 2026-05-26

Questo snapshot resta come traccia storica e non va riusato come stato corrente
senza verifica live:

- Nessuna PR aperta su Atlas, Pratix, DocMolder, FiscalBay, GLM, SendChimp,
  SyncBay, TRAM e Sentinel.
- Atlas: nessuna inbox Codex aperta; il riallineamento resta aperto.
- Pratix: inbox Codex `#34`; ultimo run GitHub `Dependabot Updates`
  cancellato il `2026-05-25`.
- DocMolder: inbox Codex `#149`; commit docs-only `bf54615` pubblicato su
  `main`; branch locale residua rimossa; venv locale riparata; workflow legacy di
  rilascio fallita su `bf54615` senza log disponibili; il flusso legacy è
  stato disattivato e sostituito dal flusso manuale repository-specifico.
- FiscalBay: inbox Codex `#69`; ultimo run GitHub `Dependabot Updates`
  cancellato il `2026-05-25`.
- GLM: inbox Codex `#3`; branch remota residua `origin/work-codex-excel-sync`
  rimossa; `CI` fallita su `main` il `2026-05-25`.
- SendChimp: inbox Codex `#2`; ultimo run GitHub `Dependabot Updates`
  cancellato il `2026-05-25`.
- SyncBay: inbox Codex `#2`; checkout `main` pulito e allineato a
  `origin/main`; nessuna PR, branch locale o branch remota extra; commit
  `dc5ba72` pubblicato; Vercel production `READY` e home `200 OK`; verifiche
  locali passate senza rilanciare Actions. Workflow `PR Title` e
  `Codex PR comments` risultano verificati attivi nel ripristino post-riavvio.
- TRAM: inbox Codex `#2`; checkout `main` pulito; branch locale assorbita
  `codex/tram-fase-7-pilot-stabilizzazione` rimossa; `Repo Hygiene` fallita su
  `main` senza log disponibili; `npm run verify` passa localmente.
- Sentinel: inbox Codex `#4`; `PR Title` fallita il `2026-05-26`; workflow
  runtime `Sentinel` verificato attivo dopo il ripristino post-riavvio.
- Il checkout locale di SyncBay è ora segnale canonico perché ricontrollato su
  richiesta esplicita; la branch locale feature non esiste più e il lavoro è su
  `main`.
- Nessun deploy o release Atlas eseguito in questo audit.

## Regole

- La matrice health è uno snapshot, non un'autorizzazione a modificare repo.
- Prima di scrivere in una repo coordinata serve sempre perimetro chiaro e
  rispetto dell'`AGENTS.md` locale.
- Non copiare in Atlas segreti, dump, dati applicativi reali o log sensibili.
- Non trasformare warning noti in blocchi se i run operativi non impattano il
  flusso reale della repo.
