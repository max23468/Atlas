# Roadmap Atlas

La roadmap descrive direzione, priorità e prossimi passi di Atlas. Le idee non ancora scelte stanno in `docs/BACKLOG.md`.

## Ora

- Usare il primo giro GLM/TRAM/SyncBay/SendChimp, la seconda ondata Pratix/DocMolder/FiscalBay e il consolidamento Sentinel come feedback reale sul metodo di allineamento Atlas.
- Usare il registro vivo `docs/PROJECTS.md`, la matrice `docs/HEALTH.md`, `docs/STANDARDS.md`, `docs/PUBLISH_DEPLOY_RELEASE.md` e `docs/STANDARD_CANDIDATES.md` come riferimento operativo prima degli interventi repo-per-repo.
- Applicare sempre la discovery degli extra repo-specifici prima di template, normalizzazioni o migrazioni.
- Usare `docs/NEXT_STEPS.md` quando viene chiesto "e ora?": proporre solo lavoro Atlas-first, non sviluppo prodotto delle repo coordinate.

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
- Usare subagent solo nella fase implementativa, con coordinamento centrale e una repo per volta in scrittura.

## Bloccato

- Nessun blocco operativo trasversale aperto; la sospensione
  globale GitHub Actions temporanea è chiusa, incluso il runtime
  schedulato Sentinel.

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
