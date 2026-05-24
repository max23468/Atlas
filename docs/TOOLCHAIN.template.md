# Toolchain

## Runtime

| Area | Versione | Fonte |
| --- | --- | --- |
| Node | `[latest LTS supportata o non applicabile]` | `[package.json/.node-version]` |
| npm | `[latest stabile compatibile o non applicabile]` | `[packageManager]` |
| Python | `[latest stable compatibile o guardrail repo-specifico]` | `[pyproject.toml/.python-version]` |

## Package manager e lockfile

- JavaScript/TypeScript: `[npm/yarn/pnpm/non applicabile]`
- Lockfile JS: `[package-lock.json/yarn.lock/pnpm-lock.yaml/non applicabile]`
- Python: `[pip/uv/poetry/non applicabile]`
- Lockfile Python: `[file o non applicabile]`

## Tool esterni

| Tool | Versione/canale | Uso |
| --- | --- | --- |
| `gh` | `[versione/canale]` | GitHub |
| `vercel` | `[versione/canale]` | deploy |
| `wrangler` | `[versione/canale]` | Cloudflare |
| `supabase` | `[versione/canale]` | Supabase |
| `docker` | `[versione/canale]` | runtime/dev |

## Comandi

- install/setup: `[comando]`
- dev: `[comando]`
- lint/typecheck: `[comando]`
- test: `[comando]`
- build: `[comando]`
- smoke: `[comando]`
- release: `[comando o non applicabile]`
- deploy: `[comando o non applicabile]`

## Regole

- Usare la versione più nuova ragionevolmente supportata dal progetto.
- Per Node usare la latest LTS supportata dallo stack.
- Per Python usare la latest stable compatibile con dipendenze, deploy e tooling.
- Rispettare guardrail repo-specifici.
- Aggiornamenti di toolchain strutturali richiedono roadmap/backlog o ADR.

## Eccezioni e guardrail

- `[repo-specific guardrail]`
