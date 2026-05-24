# Roadmap Atlas

La roadmap descrive direzione, priorità e prossimi passi di Atlas. Le idee non ancora scelte stanno in `docs/BACKLOG.md`.

## Ora

- Usare Atlas come base stabile prima di applicare il piano alla prima repo coordinata.
- Riallineare la matrice operativa alle novità verificate: Atlas pubblicato, SendChimp con runtime Next.js, Sentinel da censire, stati Python aggiornati di DocMolder/FiscalBay.

## Prossimo

- Preparare la prima applicazione controllata del piano a una sola repo, scegliendo dopo il riallineamento della matrice.
- Definire il primo formato di report o matrice health Atlas, se serve prima degli interventi repo-per-repo.
- Valutare se creare una Codex feedback inbox anche per Atlas, solo se iniziano PR o commenti operativi ricorrenti.

## Più avanti

- Creare una matrice periodica di conformità/health dei progetti coordinati.
- Definire un formato standard per report mensile Atlas.
- Valutare automazioni leggere per link check, duplicati documentali e presenza dei file canonici.
- Usare subagent solo nella fase implementativa, con coordinamento centrale e una repo per volta in scrittura.

## Bloccato

- Prima applicazione repo-per-repo: sospesa finché il riallineamento dello snapshot 2026-05-24 non è chiuso.
- Sentinel: dipende da baseline reale, Git/GitHub e `AGENTS.md`.
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
- Verificato che Sentinel esiste localmente ma non è ancora una repo Git/GitHub utilizzabile.

## Regole

- La roadmap non è un changelog.
- La roadmap non è un dump di idee.
- Le idee non ancora scelte stanno in `docs/BACKLOG.md`.
- Le decisioni stabili stanno in `docs/decisions/`.
- Ogni voce deve indicare un prossimo passo operativo reale.
