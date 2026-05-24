# Roadmap Atlas

La roadmap descrive direzione, priorità e prossimi passi di Atlas. Le idee non ancora scelte stanno in `docs/BACKLOG.md`.

## Ora

- Usare il primo giro GLM/TRAM/SyncBay/SendChimp e la seconda ondata Pratix/DocMolder/FiscalBay come feedback reale sul metodo di allineamento Atlas.
- Usare il registro vivo `docs/PROJECTS.md` come riferimento operativo prima degli interventi repo-per-repo.
- Applicare sempre la discovery degli extra repo-specifici prima di template, normalizzazioni o migrazioni.

## Prossimo

- Consolidare Sentinel solo con conferma esplicita: è l'ultimo target rimasto, va trattato come baseline runtime separata e non come normale repo docs-only.
- Definire il primo formato di report o matrice health Atlas, se serve prima degli interventi repo-per-repo.
- Valutare se creare una Codex feedback inbox anche per Atlas, solo se iniziano PR o commenti operativi ricorrenti.
- Valutare se i pattern emersi dalle due ondate meritano una regola Atlas dopo confronto con repo comparabili.

## Più avanti

- Creare una matrice periodica di conformità/health dei progetti coordinati.
- Definire un formato standard per report mensile Atlas.
- Valutare automazioni leggere per link check, duplicati documentali e presenza dei file canonici.
- Usare subagent solo nella fase implementativa, con coordinamento centrale e una repo per volta in scrittura.

## Bloccato

- FiscalBay upgrade Python completo: dipende dall'allineamento di manifest, CI e policy al runtime documentato.

## Fatto recente

- Creato Atlas come meta-progetto separato.
- Approvato il piano di coordinamento operativo.
- Creati template e checklist per AGENTS, documentazione, roadmap, backlog, toolchain, contesto, decisioni, implementazione e manutenzione.
- Creati i documenti canonici reali di Atlas: `AGENTS.md`, `docs/INDEX.md`, `docs/ROADMAP.md`, `docs/BACKLOG.md`, `docs/CONTEXT.md`, `docs/TOOLCHAIN.md` e `docs/decisions/README.md`.
- Inizializzato Git locale su branch `main`.
- Estratte tre ADR fondative: identità/perimetro di Atlas, struttura canonica root/docs e repository GitHub privata.
- Creata repository GitHub privata `https://github.com/max23468/Atlas`.
- Aggiunta baseline GitHub leggera: PR template, issue template minima e PR title check.
- Verificato che SendChimp ha runtime Next.js/Vercel/Neon e non va più trattato come docs-only.
- Verificato che Sentinel è ora una repo GitHub privata operativa `max23468/Sentinel`, con `main`, workflow schedulato/dispatch e output applicativi committabili.
- Creato `docs/PROJECTS.md` come registro vivo dei progetti coordinati.
- Rivalutato l'ordine iniziale: GLM e TRAM sono stati completati come primi pilot; Sentinel va trattata come baseline runtime separata.
- Completato il primo allineamento GLM: documenti canonici, baseline GitHub e roadmap/backlog più maturi, con merge della PR `max23468/Gare-Lotti-Milanesi#7`.
- Promossa in Atlas la regola di discovery degli extra repo-specifici prima di applicare standard o template.
- Completato l'allineamento TRAM: roadmap migrata in `docs/ROADMAP.md`, aggiunti `docs/BACKLOG.md`, `docs/TOOLCHAIN.md` e template ADR con basename unico, con merge della PR `max23468/TRAM#7`.
- Completato l'allineamento SyncBay e pubblicata la release locale 0.6.0: documenti canonici in `docs/`, Codex inbox pulita, Docker Node allineato a engine e merge delle PR `max23468/SyncBay#27`, `#28` e `#29`.
- Completato l'allineamento SendChimp: roadmap in `docs/ROADMAP.md`, indice in `docs/INDEX.md`, creati `docs/BACKLOG.md` e `docs/TOOLCHAIN.md`, chiuso P1 Codex sulla migration URL e merge della PR `max23468/SendChimp#20`; Docs hygiene, Codex inbox e Vercel automatico passati.
- Completata la seconda ondata Pratix: fix Codex P2 su `/novita`, release patch `1.11.15`, documenti canonici Atlas e merge della PR `max23468/Pratix#156`; Vercel production verificata con `publish:finish`.
- Completata la seconda ondata DocMolder: creati `docs/BACKLOG.md`, `docs/TOOLCHAIN.md`, `docs/decisions/` e merge della PR `max23468/DocMolder#166`; release/deploy non eseguiti perché docs-only.
- Completata la seconda ondata FiscalBay: creati `docs/BACKLOG.md`, `docs/TOOLCHAIN.md`, `docs/decisions/`, risolto il P1 Codex su `deploy/linux-setup.sh` e merge della PR `max23468/FiscalBay#78`; deploy/release non eseguiti.

## Regole

- La roadmap non è un changelog.
- La roadmap non è un dump di idee.
- Le idee non ancora scelte stanno in `docs/BACKLOG.md`.
- Le decisioni stabili stanno in `docs/decisions/`.
- Ogni voce deve indicare un prossimo passo operativo reale.
