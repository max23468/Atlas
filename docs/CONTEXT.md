# Contesto operativo Atlas

## Stato progetto

- Fase: docs-first / coordinamento operativo.
- Ultima versione/release: non applicabile.
- Ultimo deploy: non applicabile.
- Git: repository locale inizializzata su branch `main` il 2026-05-24.
- GitHub: non configurato.

## Fonte di verità

- Piano principale: `piano-coordinamento-progetti.md`
- Indice documentale: `docs/INDEX.md`
- Roadmap: `docs/ROADMAP.md`
- Backlog: `docs/BACKLOG.md`
- Toolchain: `docs/TOOLCHAIN.md`
- Decisioni: `docs/decisions/`
- ADR fondative: `docs/decisions/0001-atlas-meta-progetto-leggero.md`, `docs/decisions/0002-struttura-canonica-root-docs.md`
- Regole operative: `AGENTS.md`
- Template: file `*.template.md`
- Checklist implementazione: `CHECKLIST-IMPLEMENTAZIONE.md`
- Checklist manutenzione: `CHECKLIST-MANUTENZIONE.md`

## Ultimo contesto utile

Atlas nasce dalla ricognizione trasversale dei progetti locali e dal piano approvato in `piano-coordinamento-progetti.md`.

Obiettivo corrente: stabilizzare Atlas come progetto leggero prima di applicare il piano a Pratix, DocMolder, FiscalBay, GLM, SendChimp, SyncBay o TRAM.

## Vincoli specifici

- Non applicare il piano alle altre repo finché Atlas non è stabile.
- Non trattare Atlas come prodotto applicativo.
- Non introdurre release o deploy finché non c'è decisione esplicita.
- Non confondere i template con i documenti canonici reali.
- Non perdere contenuti durante migrazioni o uniformazioni.
- Rispettare sempre l'`AGENTS.md` della repo bersaglio prima di qualunque intervento fuori da Atlas.
- Usare i subagent solo nella fase implementativa, con coordinamento centrale, prima passata read-only e una sola repo per volta in scrittura.

## Verifiche da ricordare

- `git status --short`: se Atlas è una repo Git; se non lo è, dichiarare lo stato.
- `git branch --show-current`: confermare branch corrente.
- `rg --files`: inventario rapido file.
- Controllo manuale link e coerenza tra documenti canonici.
- Verifica che `.DS_Store` non sia trattato come contenuto progettuale.

## Handoff per nuova chat

Prima di procedere:

1. leggere `AGENTS.md`;
2. controllare se Atlas è stato inizializzato come repo Git;
3. leggere `README.md`;
4. leggere `piano-coordinamento-progetti.md`;
5. leggere `docs/INDEX.md`, `docs/ROADMAP.md`, `docs/BACKLOG.md`, `docs/CONTEXT.md` e `docs/TOOLCHAIN.md`;
6. verificare che la richiesta riguardi Atlas e non applichi implicitamente cambiamenti ad altre repo;
7. identificare verifiche proporzionate.

Durante handoff e migrazioni, non perdere contenuti: se una nota viene spostata, indicare nuova posizione o motivo della rimozione.

## Rischi aperti

- Iniziare interventi repo-per-repo prima che Atlas sia abbastanza stabile.
- Creare documenti doppi con stesso scopo.
- Rendere Atlas troppo pesante rispetto al suo ruolo di cabina di regia.
- Trasformare vincoli repo-specifici in standard generici sbagliati.
- Confondere publish, deploy e release nelle repo coordinate.

## Prossimo passo

- Decidere se pubblicare Atlas su GitHub.
- Decidere se aggiungere una baseline GitHub leggera.
