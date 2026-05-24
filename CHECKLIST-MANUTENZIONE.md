# Checklist manutenzione periodica

Frequenza:

- mensile per tutte le repo;
- obbligatoria prima di `publish`, `deploy` o `release`.

## Stato repository

1. `git status --short`
2. branch locali e remoti stale
3. worktree attivi
4. modifiche non proprie

## GitHub

1. PR aperte
2. issue rilevanti
3. `Codex feedback inbox`
4. workflow falliti
5. PR title check
6. Dependabot/security alerts
7. branch protection se applicabile

## Documentazione

1. `docs/INDEX.md`
2. `docs/HEALTH.md` se la repo è Atlas o una meta-repo equivalente
3. `docs/ROADMAP.md`
4. `docs/BACKLOG.md`
5. `docs/TOOLCHAIN.md`
6. `docs/CONTEXT.md`
7. `docs/decisions/`
8. duplicati o documenti non canonici
9. rinvii temporanei ancora necessari
10. contenuti migrati senza perdita

## Toolchain

1. runtime dichiarati
2. package manager e lockfile
3. engines/pyproject
4. tool esterni
5. guardrail repo-specifici
6. scostamenti dalla latest LTS/stable compatibile dichiarati in `docs/TOOLCHAIN.md`

## Verifiche

1. lint/typecheck
2. test
3. build
4. smoke
5. React Doctor se applicabile
6. pulizia `.DS_Store` se presente o tracciato per errore

## Publish, deploy e release

1. changelog/release pendenti
2. tag/versioni coerenti
3. target deploy dichiarato
4. health/rollback se produzione
5. cleanup branch/worktree

## Output

- Stato:
- Anomalie:
- Azioni da eseguire:
- Contenuti a rischio perdita:
- Verifiche eseguite:
- Blocchi:
- Prossima manutenzione:
