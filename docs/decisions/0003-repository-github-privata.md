# 0003 - Repository GitHub privata per Atlas

Data: 2026-05-24

Stato: Superata

Superata da: [0005 - Repository GitHub pubbliche nel perimetro Atlas](0005-repository-github-pubbliche.md)

## Contesto

Atlas è stato inizializzato come repository Git locale. Per renderlo recuperabile, versionabile e pubblicabile nel canale canonico del maintainer serve una repository GitHub dedicata.

Atlas contiene governance, template, roadmap e riferimenti ai progetti locali. Anche senza segreti o dati applicativi reali, questi contenuti sono operativi e non pensati come materiale pubblico.

## Decisione

Creare una repository GitHub privata per Atlas.

Questa decisione è storica: lo stato corrente approvato è pubblico.

La repository remota canonica è `https://github.com/max23468/Atlas`.

Atlas resta docs-first: non ha runtime, release o deploy. La pubblicazione su GitHub serve solo a versionare e conservare il meta-progetto.

## Alternative considerate

- Tenere Atlas solo locale: respinta, perché riduce tracciabilità e recuperabilità.
- Creare repository pubblica: respinta per prudenza, perché Atlas contiene governance e riferimenti operativi ai progetti locali.
- Aggiungere subito una baseline GitHub pesante: respinta, perché Atlas è docs-first e non ha dipendenze runtime.

## Impatti

- Prodotto: Atlas resta meta-progetto interno.
- Tecnico storico: `origin` puntava alla repository GitHub privata al momento della decisione.
- Dati/privacy: nessun segreto deve essere committato; la decisione corrente sulla visibilità è in `0005`.
- Deploy/release: non applicabili.
- Documentazione: README, contesto, toolchain, roadmap e indice decisioni dichiarano il nuovo stato GitHub.

## Conseguenze operative

- Usare `main` come branch principale.
- Usare PR e issue in modo leggero quando il lavoro diventa non banale.
- Mantenere una baseline GitHub proporzionata: PR template, issue template minima e controllo titolo PR.
- Non aggiungere Dependabot finché non esistono dipendenze runtime reali.
- Non aggiungere release o deploy finché non vengono decisi esplicitamente.

## Verifiche

- `git status --short`
- `git remote -v`
- `git push -u origin main`
- `gh repo view max23468/Atlas --json nameWithOwner,url,visibility`

## Collegamenti

- Roadmap: `../ROADMAP.md`
- Backlog: `../BACKLOG.md`
- PR/issue: repository GitHub privata al momento della decisione storica
- Documenti collegati: `../../README.md`, `../../AGENTS.md`, `../CONTEXT.md`, `../TOOLCHAIN.md`
