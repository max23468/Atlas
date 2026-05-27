# Hardening tecnico-operativo (2026-05-27)

## Rischio iniziale

- Livello: **basso-medio**.
- Stato in questa ondata: **P1/P2** su governance docs-first.
- Rotazione segreti: **non inclusa** in questa fase (esclusa dal piano corrente).

## Contesto operativo rilevante

- Meta-progetto docs-first: Atlass coordina policy, standard e runway operativo.
- Nessun runtime applicativo primario da proteggere direttamente.
- Obiettivo: ridurre superficie documentale, evitare leak semantici e mantenere traceabilità.

## Piano tecnico (P1/P2)

### P1

- Rimuovere riferimenti operativi sensibili da documenti non trattati come segreti.
- Verificare path canonici e riferimenti tra repo, evitando cross-link opachi.
- Mantenere check `AGENTS`/`INDEX` e canonical docs aggiornati.

### P2

- Hardening anti-deriva su standard e regole: consolidare decisioni, evitare duplicazioni,
  mantenere naming e struttura stabili.
- Periodicità mensile su `docs/HEALTH.md` e `docs/PROJECTS.md` con focus su rischi
  aperti e stato hardening repo.

## Piano operativo e di governo

### P1/P2

- Applicare `atlas` governance prima degli interventi repo-per-repo:
  - leggere documenti canonicamente designati,
  - verificare branch/status, runbook e feedback Codex,
  - aggiornare registro stato operativo quando cambia il perimetro.
- Mantenere audit read-only e check periodici senza introdurre codice runtime non richiesto.
