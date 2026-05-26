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

Esito:

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

## Regole

- La matrice health è uno snapshot, non un'autorizzazione a modificare repo.
- Prima di scrivere in una repo coordinata serve sempre perimetro chiaro e
  rispetto dell'`AGENTS.md` locale.
- Non copiare in Atlas segreti, dump, dati applicativi reali o log sensibili.
- Non trasformare warning noti in blocchi se i run operativi sono verdi.
