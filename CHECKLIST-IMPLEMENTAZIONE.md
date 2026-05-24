# Checklist implementazione piano

Usare questa checklist prima di applicare il piano a una repository.

## Prima di modificare

1. Leggere `AGENTS.md`.
2. Eseguire `git status --short`.
3. Identificare modifiche non proprie.
4. Leggere `README.md`, `docs/INDEX.md`, `docs/CONTEXT.md`, `docs/ROADMAP.md`, `docs/BACKLOG.md`, `docs/TOOLCHAIN.md`.
5. Censire funzioni, documenti, workflow, runbook, policy e comportamenti repo-specifici non previsti dal piano Atlas.
6. Classificare gli extra: mantenere specifico, promuovere ad Atlas, sostituire con pattern più maturo, mettere in backlog o rimuovere solo se duplicato/superato.
7. Controllare `Codex feedback inbox`.
8. Identificare verifiche proporzionate.
9. Dichiarare se publish, deploy o release sono fuori scope.

## Discovery repo-specifica

1. Non copiare template Atlas alla cieca sopra documenti o funzioni già maturi.
2. Segnalare gli extra rilevanti prima di normalizzarli.
3. Promuovere un pattern ad Atlas solo dopo verifica almeno su un'altra repo comparabile o decisione esplicita.
4. Mantenere in backlog ciò che è promettente ma non ancora standard.
5. Non rimuovere contenuti solo per uniformità.

## Migrazioni documentali

1. Fare inventario dei contenuti da migrare.
2. Creare o aggiornare documento canonico.
3. Spostare o assorbire contenuti senza perdita.
4. Lasciare rinvio temporaneo quando serve.
5. Aggiornare link da `README.md` e `AGENTS.md`.
6. Aggiornare `docs/INDEX.md`.
7. Dichiarare eventuali contenuti rimossi e motivo.
8. Verificare che tool o subagent non abbiano riassunto, scartato o compresso contenuti utili.

## File canonici

- `docs/INDEX.md`
- `docs/ROADMAP.md`
- `docs/BACKLOG.md`
- `docs/TOOLCHAIN.md`
- `docs/CONTEXT.md`
- `docs/decisions/`
- `docs/decisions/README.md`
- `docs/decisions/template.md`

## Doppioni documentali

- Non creare documenti con lo stesso titolo o lo stesso scopo.
- Se esiste già un documento equivalente, migrarlo nel documento canonico o trasformarlo in rinvio temporaneo.
- Se un contenuto resta fuori dal documento canonico, indicare dove si trova e perché.

## GitHub

- PR template.
- Issue template minima.
- Codex feedback inbox.
- Workflow Codex PR comments.
- PR title check.
- Dependabot solo con dipendenze runtime reali.
- Branch protection solo se utile.

## Subagent

- Usarli solo in fase implementativa, non per ridecidere il piano.
- Prima passata read-only.
- Una sola repo per volta in scrittura.
- Ogni subagent deve restituire inventario file, contenuti migrati, contenuti non migrati e verifiche.

## Verifiche

- Lint/typecheck:
- Test:
- Build:
- Smoke:
- React Doctor se app React dopo release minor `X.Y.Z`, cioè quando cambia `Y`:
- Check docs:
- Pulizia `.DS_Store` se compare nel working tree o risulta tracciato:

## Chiusura

Il riepilogo finale deve includere:

- file modificati;
- contenuti migrati;
- contenuti rimossi o rinvii temporanei;
- verifiche eseguite;
- controlli non eseguiti e impatto;
- rischi residui;
- prossimo passo.
