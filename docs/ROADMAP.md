# Roadmap Atlas

La roadmap descrive direzione, priorità e prossimi passi di Atlas. Le idee non ancora scelte stanno in `docs/BACKLOG.md`.

## Ora

- Usare Atlas come base stabile prima di applicare il piano alla prima repo coordinata.
- Usare il registro vivo `docs/PROJECTS.md` come riferimento operativo prima degli interventi repo-per-repo.

## Prossimo

- Preparare la prima applicazione controllata del piano a una sola repo, scegliendo il target solo dopo conferma esplicita.
- Definire il primo formato di report o matrice health Atlas, se serve prima degli interventi repo-per-repo.
- Valutare se creare una Codex feedback inbox anche per Atlas, solo se iniziano PR o commenti operativi ricorrenti.

## Più avanti

- Creare una matrice periodica di conformità/health dei progetti coordinati.
- Definire un formato standard per report mensile Atlas.
- Valutare automazioni leggere per link check, duplicati documentali e presenza dei file canonici.
- Usare subagent solo nella fase implementativa, con coordinamento centrale e una repo per volta in scrittura.

## Bloccato

- Sentinel: dipende dalla decisione su scaffold iniziale, primo commit, remote GitHub e workflow operativo.
- FiscalBay upgrade Python completo: dipende dall'allineamento di manifest, CI e policy al runtime documentato.

## Fatto recente

- Creato Atlas come meta-progetto separato.
- Approvato il piano di coordinamento operativo.
- Creati template e checklist per AGENTS, documentazione, roadmap, backlog, toolchain, contesto, decisioni, implementazione e manutenzione.
- Creati i documenti canonici reali di Atlas: `AGENTS.md`, `docs/INDEX.md`, `docs/ROADMAP.md`, `docs/BACKLOG.md`, `docs/CONTEXT.md`, `docs/TOOLCHAIN.md` e `docs/decisions/README.md`.
- Inizializzato Git locale su branch `main`.
- Estratte due ADR fondative: identità/perimetro di Atlas e struttura canonica root/docs.
- Creata repository GitHub privata `https://github.com/max23468/Atlas`.
- Aggiunta baseline GitHub leggera: PR template, issue template minima e PR title check.
- Verificato che SendChimp ha runtime Next.js/Vercel/Neon e non va più trattato come docs-only.
- Verificato che Sentinel è ora una repo Git locale iniziale, senza commit/remote e con scaffold Node/TypeScript non tracciato.
- Creato `docs/PROJECTS.md` come registro vivo dei progetti coordinati.
- Rivalutato l'ordine iniziale: GLM resta la prima candidata per allineamento di una repo esistente pulita; Sentinel va trattata come baseline iniziale separata.

## Regole

- La roadmap non è un changelog.
- La roadmap non è un dump di idee.
- Le idee non ancora scelte stanno in `docs/BACKLOG.md`.
- Le decisioni stabili stanno in `docs/decisions/`.
- Ogni voce deve indicare un prossimo passo operativo reale.
