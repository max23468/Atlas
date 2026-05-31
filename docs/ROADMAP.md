# Roadmap Atlas

Data ultimo aggiornamento: 2026-05-31

La roadmap descrive direzione, priorità e prossimi passi di Atlas. Le idee non ancora scelte stanno in `docs/BACKLOG.md`.

## Ora

- Avvio hardening repo: primo step operativo su Pratix seguendo i gate P0/P1
  già documentati in `SECURITY.md` e `docs/SECURITY_HARDENING.md` della repo.
  Gli altri repo restano in attesa del loro slot.
- Prendere spunto dal primo giro GLM/TRAM/SyncBay/SendChimp e dalla seconda ondata Pratix/DocMolder/FiscalBay.
- Usare il registro vivo `docs/PROJECTS.md`, la matrice `docs/HEALTH.md`, `docs/STANDARDS.md`, `docs/PUBLISH_DEPLOY_RELEASE.md` e `docs/STANDARD_CANDIDATES.md` come riferimento operativo prima degli interventi repo-per-repo.
- Applicare sempre la discovery degli extra repo-specifici prima di template, normalizzazioni o migrazioni.
- Usare `docs/NEXT_STEPS.md` quando viene chiesto "e ora?": proporre solo lavoro Atlas-first, non sviluppo prodotto delle repo coordinate.

## Ordine hardening completo (priorità alta → bassa)

1. **Pratix**: P0/P1 (bloccante) — `git` + Vercel + Supabase, `.env` tracciati e hardening minimi prima di nuove aperture.
2. **FiscalBay**: P0/P1 — separazione runtime e credenziali ambientali, webhook/API hygiene, logging payload.
3. **SyncBay**: P0/P1 — keyset separati, firma callback, policy OAuth/sessioni e rate limit.
4. **DocMolder**: P0/P1 — VPS + Telegram con runbook deploy/rollback e idempotenza script.
5. **TRAM**: P1 — confine documentazione pubblica/interiore, CI su regressioni operanti.
6. **Sentinel**: P1 — env locali fuori repo, retention controllata, scheduler resilient.
7. **SendChimp**: P1 — capienza provider, guardrail quota e governance provider.
8. **GLM**: P1/P2 — hardening deploy target, review dipendenze, contenuti demo.
9. **Atlas**: P1/P2 — governance, standard e audit docs-first.

## Stato aggiornamento hardening 2026-05-27 (tracciamento operativo)

- **Obiettivo ondata:** implementare i piani P0/P1/P2/operativo su tutte le repo coordinate, senza attività di rotazione preventiva.
- **Metodo di verifica usato:** per ogni repo verificati:
  - presenza documento operativo (`SECURITY.md` e/o `docs/SECURITY_HARDENING.md`);
  - nessun file `.env` tracciato in git;
  - assenza di terminologia di rotazione preventiva nei piani tecnici;
  - stato branch coerente (`codex/hardening-operativo-2026-05-27`).

### Risultato per repo (2026-05-27)

- **Pratix**: `SECURITY.md` aggiornato con P0/P1/P2 espliciti + stop interventi funzionali finché P0/P1; nessuna rotazione preventiva; `docs/ROADMAP.md` aggiornata.
- **DocMolder**: `docs/SECURITY_HARDENING.md` creato + aggiornato `docs/OPERATIONS_SECURITY.md` con sezione hardening-operativo e ritiro del riferimento a rotazioni periodiche.
- **FiscalBay**: `docs/SECURITY_HARDENING.md` aggiornato; `docs/SECURITY_OPERATIONS.md` con sostituzione credenziali solo in incidente; nessuna rotazione programmata.
- **GLM**: `docs/SECURITY_HARDENING.md` aggiornato con P0/P1/P2 e hardening deploy target esplicito.
- **SyncBay**: `docs/SECURITY_HARDENING.md` aggiornato + `SECURITY.md` allineata su sostituzione credenziali in incidente (non rotazione periodica).
- **TRAM**: `docs/SECURITY_HARDENING.md` aggiornato con focus su confine pubblico/interno e checklist trimestrale.
- **Sentinel**: `docs/SECURITY_HARDENING.md` aggiornato con monitor runtime e guardrail su scheduler/retry/offline.
- **SendChimp**: `docs/SECURITY_HARDENING.md` aggiornato con capacity check pre-estensione e controllo provider.
- **Atlas**: `docs/SECURITY_HARDENING.md` aggiunto con governance docs-first + anti-deriva.

### Prossimi passi Atlas (fine ondata)

- Tracciare anche i risultati di verifica nei record operativi (`docs/HEALTH.md`, `docs/PROJECTS.md`) con data di check.
- Prima di un nuovo ciclo funzionale su repo sensibili, verificare `P0/P1` non in stato bloccante.

## Prossimo

- Mantenere `docs/STANDARDS.md` come fonte di verità per standard uniformati, equivalenti, sospesi e non applicabili.
- Rivalutare periodicamente `docs/STANDARD_CANDIDATES.md` prima di promuovere nuovi pattern a standard Atlas.
- Tenere separati debiti repo e scope Atlas: i debiti repo si censiscono o si impacchettano, ma non diventano lavoro esecutivo senza target esplicito.
- Confermare il riavvio dei workflow `Codex PR comments` dove previsto.
- Confermare il riavvio del workflow runtime `Sentinel` dove previsto.
- Riallineare Dependabot dove oggi è sospeso, senza declassarlo da standard
  pieno.
- Non forzare upgrade Python FiscalBay oltre `3.10`: la VPS `3.13` è compatibilità operativa finché la repo non decide un upgrade completo.

## Più avanti

- Definire un formato standard per report mensile Atlas.
- Valutare se trasformare `docs/HEALTH.md` in report periodico o tenerlo come snapshot manuale.
- Valutare automazioni leggere per link check, duplicati documentali e presenza dei file canonici.
- Mantenere la scrittura repo-per-repo con coordinamento centrale, discovery iniziale e nessuna perdita di contenuti.

## Bloccato

- Nessun blocco operativo trasversale aperto; la sospensione
  globale GitHub Actions temporanea è chiusa, incluso il runtime
  schedulato Sentinel.

## In corso ora

- Hardening Pratix:
  - rimozione e controllo `.env` tracciati nel sorgente;
  - audit segreti/runtime nel perimetro (senza rotazione come richiesto);
  - verifica esposizione integrazioni e policy base di sicurezza documentata;
  - verifica check di governance prima di nuovi interventi funzionali.

## Fatto recente

- Creato Atlas come meta-progetto separato.
- Approvato il piano di coordinamento operativo.
- Creati template e checklist per AGENTS, documentazione, roadmap, backlog, toolchain, contesto, decisioni, implementazione e manutenzione.
- Creati i documenti canonici reali di Atlas: `AGENTS.md`, `docs/INDEX.md`, `docs/ROADMAP.md`, `docs/BACKLOG.md`, `docs/CONTEXT.md`, `docs/TOOLCHAIN.md` e `docs/DECISIONS.md`.
- Inizializzato Git locale su branch `main`.
- Estratte tre ADR fondative: identità/perimetro di Atlas, struttura canonica root/docs e repository GitHub privata.
- Creata repository GitHub privata `https://github.com/max23468/Atlas`.
- Aggiunta baseline GitHub leggera: PR template, issue template minima e PR title check.
- Verificato che SendChimp ha runtime Next.js/Vercel/Neon e non va più trattato come docs-only.
- Verificato che Sentinel è ora una repo GitHub privata operativa `max23468/Sentinel`, con `main`, workflow schedulato/dispatch e output applicativi committabili.
- Creato `docs/PROJECTS.md` come registro vivo dei progetti coordinati.
- Rivalutato l'ordine iniziale: GLM e TRAM sono stati completati come primi pilot; Sentinel va trattata come baseline runtime separata.
- Completato il primo allineamento GLM: documenti canonici, baseline GitHub e roadmap/backlog più maturi, con merge della PR `max23468/GLM#7`.
- Promossa in Atlas la regola di discovery degli extra repo-specifici prima di applicare standard o template.
- Completato l'allineamento TRAM: roadmap migrata in `docs/ROADMAP.md`, aggiunti `docs/BACKLOG.md`, `docs/TOOLCHAIN.md` e template ADR con basename unico, con merge della PR `max23468/TRAM#7`.
- Completato l'allineamento SyncBay e pubblicata la release locale 0.6.0: documenti canonici in `docs/`, Codex inbox pulita, Docker Node allineato a engine e merge delle PR `max23468/SyncBay#27`, `#28` e `#29`.
- Completato l'allineamento SendChimp: roadmap in `docs/ROADMAP.md`, indice in `docs/INDEX.md`, creati `docs/BACKLOG.md` e `docs/TOOLCHAIN.md`, chiuso P1 Codex sulla migration URL e merge della PR `max23468/SendChimp#20`; Docs hygiene, Codex inbox e Vercel automatico passati.
- Completata la seconda ondata Pratix: fix Codex P2 su `/novita`, release patch `1.11.15`, documenti canonici Atlas e merge della PR `max23468/Pratix#156`; Vercel production verificata con `publish:finish`.
- Completata la seconda ondata DocMolder: creati `docs/BACKLOG.md`, `docs/TOOLCHAIN.md`, `docs/decisions/` e merge della PR `max23468/DocMolder#166`; release/deploy non eseguiti perché docs-only.
- Completata la seconda ondata FiscalBay: creati `docs/BACKLOG.md`, `docs/TOOLCHAIN.md`, `docs/decisions/`, risolto il P1 Codex su `deploy/linux-setup.sh` e merge della PR `max23468/FiscalBay#78`; deploy/release non eseguiti.
- Completato il consolidamento Sentinel: documenti canonici Atlas, decisione su GitHub Actions come runtime operativo MVP, baseline GitHub minima e merge della PR `max23468/Sentinel#1`; workflow manuale `26369906474` verde e output commit `4b9d151`.
- Creata la prima matrice health Atlas in `docs/HEALTH.md`, con stato sintetico verde/attenzione/bloccato e prossimi controlli per ogni repo.
- Definito il ciclo di manutenzione periodica in `docs/MAINTENANCE.md`.
- Eseguito il primo ciclo di manutenzione sulle repo in `Attenzione`: FiscalBay, SendChimp, TRAM e Sentinel; inbox pulite, workflow recenti verdi e merge della PR `max23468/TRAM#6` con React Doctor `100 / 100`.
- Creato `docs/STANDARDS.md` e completato un ciclo correttivo sugli standard
  Atlas: SendChimp PR `#21`, Pratix PR `#157`, SyncBay PR `#30`, Sentinel PR
  `#2`, GLM commit `[skip ci]`; GitHub Actions non usate come gate predefinito e
  workflow `Codex PR comments` riattivati dove previsto.
- Definita la policy SemVer/release di TRAM con commit `783b783` `[skip ci]`; nessun deploy perché TRAM non ha target deploy approvato.
- Verificata la policy Python di FiscalBay: supporto dichiarato `>=3.10`, VPS `3.13` come runtime operativo compatibile, nessun upgrade forzato.
- Riavviato manualmente il workflow runtime `Sentinel` dopo verifica iniziale.
- Creata `CHECKLIST-NUOVA-REPO.md` per inserire una nuova repository nel perimetro Atlas senza applicare template in modo meccanico.
- Completato e pubblicato il punto 1/24 `AGENTS.md`: contenuti sostanziali integrati granularmente nelle repo, senza blocco comune Atlas incollato; PR pubblicate Atlas `#19` e `#20`, Pratix `#171`, DocMolder `#190`, FiscalBay `#89`, GLM `#20`, SendChimp `#33`, TRAM `#22` e Sentinel `#20`; SyncBay verificata già conforme senza diff necessario.
- Completato e pubblicato il punto 2/24 `Catalogo documentazione`: chiariti root/docs, indici canonici, anti-duplicati, riferimenti errati ed eccezioni operative in Atlas, Pratix, DocMolder, FiscalBay, GLM, SendChimp, SyncBay, TRAM e Sentinel.
- Creata `docs/PUBLISH_DEPLOY_RELEASE.md` per separare publish, release e deploy repo per repo.
- Creata `docs/APPLYING_ATLAS.md` per chiarire come applicare Atlas senza trasformarlo in sviluppo prodotto delle repo coordinate.
- Creato `docs/STANDARD_CANDIDATES.md` per classificare i pattern emersi da GLM, TRAM, SyncBay, SendChimp e dalle altre repo coordinate.
- Creato `docs/NEXT_STEPS.md` per impedire che i prossimi passi Atlas vengano confusi con sviluppo prodotto delle repo coordinate.

## Regole

- La roadmap non è un changelog.
- La roadmap non è un dump di idee.
- Le idee non ancora scelte stanno in `docs/BACKLOG.md`.
- Le decisioni stabili stanno in `docs/decisions/`.
- Ogni voce deve indicare un prossimo passo operativo reale.
