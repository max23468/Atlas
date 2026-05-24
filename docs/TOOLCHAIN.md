# Toolchain Atlas

Atlas è un meta-progetto docs-first. Non ha runtime applicativo, package manager o build.

## Runtime

| Area | Versione | Fonte |
| --- | --- | --- |
| Node | non applicabile | nessun `package.json` |
| npm | non applicabile | nessun `packageManager` |
| Python | non applicabile | nessun `pyproject.toml` |

## Package manager e lockfile

- JavaScript/TypeScript: non applicabile.
- Lockfile JS: non applicabile.
- Python: non applicabile.
- Lockfile Python: non applicabile.

## Tool esterni

| Tool | Versione/canale | Uso |
| --- | --- | --- |
| `git` | locale | stato repository e branch |
| `rg` | locale | ricerca e inventario file |
| `gh` | opzionale | GitHub, solo se Atlas verrà pubblicato o usato con issue/PR |

## Comandi

- install/setup: non applicabile.
- dev: non applicabile.
- lint/typecheck: non applicabile.
- test: non applicabile.
- build: non applicabile.
- smoke: controllo manuale documenti/link/coerenza.
- inventario file: `rg --files`.
- stato Git: `git status --short`.
- branch Git: `git branch --show-current`.
- release: non applicabile.
- deploy: non applicabile.

## Regole

- Non introdurre runtime solo per formalità.
- Se in futuro Atlas avrà script o automazioni, dichiarare runtime, package manager, lockfile e comandi qui prima di considerarli canonici.
- Se Atlas viene inizializzato su GitHub, aggiornare questa pagina con strumenti effettivamente usati.
- Aggiornamenti di toolchain strutturali richiedono roadmap/backlog o ADR.

## Eccezioni e guardrail

- React Doctor non applicabile ad Atlas.
- Codex feedback inbox non applicabile finché Atlas non ha una repo GitHub.
- Nessuna regola di Pratix, DocMolder, FiscalBay, GLM, SendChimp, SyncBay o TRAM si applica automaticamente ad Atlas senza adattamento esplicito.
