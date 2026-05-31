# Matrice standard Atlas

Data ultimo aggiornamento: 2026-05-31

Questa matrice verifica gli standard che Atlas deve rendere espliciti e, dove
possibile, uniformare nelle repo coordinate. Atlas coordina e pubblica la
governance: non forza runtime, release, deploy o workflow dove la policy della
repo non li prevede.

Documenti collegati:

- `docs/PUBLISH_DEPLOY_RELEASE.md`: semantica e matrice operativa di publish, release e deploy.
- `docs/STANDARD_CANDIDATES.md`: pattern maturi non ancora tutti promossi a standard.
- `docs/SEMANTIC_CHECKLIST.md`: contenuti minimi richiesti nei documenti canonici.
- `docs/NEXT_STEPS.md`: distinzione tra prossimi passi Atlas e sviluppo prodotto delle repo coordinate.

Legenda:

- `OK pieno`: standard presente nel formato e nel contenuto attesi.
- `OK equivalente`: standard soddisfatto con una soluzione locale diversa, ma
  semanticamente equivalente.
- `Da riallineare`: gap reale o allineamento incompleto da chiudere.
- `Sospeso`: standard applicabile ma temporaneamente non attivato.
- `N/A`: non applicabile alla fase o allo stack.

In questa matrice `OK equivalente` non significa formato identico: significa
stesso risultato operativo o di governance, ottenuto con implementazione locale
diversa ma accettata.

## Standard trasversali

| Area | Regola Atlas | Stato attuale |
| --- | --- | --- |
| Documenti canonici | `AGENTS.md`, `README.md`, indice, roadmap, backlog, context, toolchain e decisioni dove applicabili | `OK pieno`: presenti nelle repo coordinate; SendChimp ora usa `docs/CONTEXT.md` canonico |
| Catalogo documentazione | Root come ingresso/esecuzione, `docs/` come governance e approfondimento, indici canonici, anti-duplicati, anti-perdita ed eccezioni operative dichiarate | `OK pieno`: punto 2/24 completato e pubblicato in Atlas, Pratix, DocMolder, FiscalBay, GLM, SendChimp, SyncBay, TRAM e Sentinel |
| AGENTS.md | Standard sostanziale comune da integrare granularmente, senza blocchi Atlas incollati: priorità/fonti, perimetro, Git/worktree, inbox, verifiche a corsie, publish completo e proporzionato, release/deploy valutati insieme, sicurezza, UI/provider/deploy/output quando applicabili, risposta finale e completamento | `OK pieno`: punto 1/24 completato e pubblicato in Atlas, Pratix, DocMolder, FiscalBay, GLM, SendChimp, TRAM e Sentinel; SyncBay verificata già conforme senza diff necessario |
| Source of truth | Ogni repo dichiara fonti primarie e documenti da leggere prima di intervenire | `OK pieno`: dichiarate; restano alcune differenze motivate, per esempio registri storici come `docs/DECISIONS.md` |
| Basename Markdown univoci | Niente due file Markdown con lo stesso basename nella stessa repo; usare `docs/INDEX.md` per indice documentale e `docs/DECISIONS.md` per indice decisionale | `OK pieno`: verificato sui file Markdown tracciati di tutte le repo coordinate |
| Lifecycle decisionale | Registro stabile, pending separato e ADR puntuali: `docs/DECISIONS.md`, `docs/DECISIONS_PENDING.md` e `docs/decisions/NNNN-slug.md` | `OK pieno`: modello presente in tutte le repo coordinate |
| Scope Atlas vs prodotto | Atlas censisce e coordina; non propone sviluppo prodotto delle repo come prossimo passo generico | `OK pieno`: procedura dedicata in `docs/NEXT_STEPS.md` |
| Isolamento Git | Interventi Atlas su repo coordinate sempre su branch dedicata; worktree separato quando serve preservare stato o parallelizzare | `OK pieno`: regola Atlas definita; da applicare in ogni intervento futuro |
| GitHub baseline | PR template, issue template, PR title check o equivalente, policy PR/merge | `OK equivalente`: baseline presente; alcune repo usano `pr-title.yml`, altre controlli equivalenti nella CI/policy locale |
| Merge GitHub | Squash merge come unico metodo consentito e cancellazione automatica branch dopo merge | `OK pieno`: Atlas, Pratix, DocMolder, FiscalBay, GLM, SendChimp, SyncBay, TRAM e Sentinel sono configurate su squash-only + delete branch |
| Codex feedback inbox | Issue `Codex feedback inbox`, label canonica `codex-feedback-inbox` e, quando le Actions sono attive, handler/workflow coerente dove ci sono PR operative ricorrenti | `OK pieno`: Atlas e repo coordinate allineate al modello con label canonica; workflow operativi attivi |
| Versioning | Semantica comune; source of truth dichiarata; tag e GitHub Release quando esiste release reale | `OK equivalente`: GLM, SendChimp, SyncBay e Sentinel dichiarano source of truth e policy tag/GitHub Release proporzionata alla release reale |
| Publish/deploy/release | Parole chiave comuni, target e comandi repo-specifici, niente deploy/release inventati | `OK pieno`: matrice sintetica in `docs/PUBLISH_DEPLOY_RELEASE.md` |
| Pubblicazione proporzionata | Ogni repo deve dichiarare un percorso proporzionato al diff: docs-only/governance-only senza smoke, deploy, release o gate runtime non pertinenti | `OK pieno`: principio dichiarato nei context/policy repo o già presente in policy locale |
| Verifiche | Gate proporzionati al rischio, senza test inventati | `OK pieno`: run remote storiche sono contesto e non sostituiscono verifiche locali dichiarate |
| React Doctor | Obbligatorio per app React dopo release minor o modifiche React trasversali | `OK pieno`: applicato in Pratix, GLM, SendChimp, SyncBay e TRAM |
| Dependabot | Standard pieno in tutte le repo con dipendenze o manifest compatibili, incluse GitHub Actions dove non esistono manifest runtime | `OK pieno`: Atlas copre GitHub Actions; le repo con manifest runtime hanno `dependabot.yml` |
| Toolchain/versioni | Runtime, package manager, lockfile e versioni minime dichiarati | `OK pieno`: FiscalBay è riallineata a Python `3.13` come baseline unica; Node/npm e Python restano dichiarati repo per repo |
| Privacy/sicurezza | No segreti, no dati reali non necessari, provider/API variabili verificati | `OK pieno`: policy comune presente; i dettagli restano repo-specifici |
| Artefatti generati | `.DS_Store`, cache, build output e file temporanei non sono contenuto progettuale | `OK equivalente`: regola comune rispettata; Sentinel mantiene output applicativi previsti dal proprio runtime |
| Handoff | `docs/CONTEXT.md` o path dichiarato per riprendere il lavoro | `OK pieno`: handoff presente; SendChimp riallineato a `docs/CONTEXT.md` |

## Matrice repo

| Repo | Docs | GitHub/PR title | Codex inbox | Versioning/release | React Doctor | Dependabot | Note |
| --- | --- | --- | --- | --- | --- | --- | --- |
| Atlas | OK pieno | OK pieno | OK pieno | N/A | N/A | OK pieno | Inbox Codex issue `#10`; Dependabot copre GitHub Actions |
| Pratix | OK pieno | OK pieno | OK pieno | OK pieno | OK pieno | OK pieno | Nessuna PR aperta; inbox `#163`; `Dependabot Updates` cancellato il `2026-05-25` |
| DocMolder | OK pieno | OK equivalente | OK pieno | OK pieno | N/A | OK pieno | Inbox `#149`; PR title controllato nella CI/policy locale; release manuale documentata, con check VPS del runbook |
| FiscalBay | OK pieno | OK pieno | OK pieno | OK pieno | N/A | OK pieno | Inbox `#86`; Python `3.13` è baseline unica per manifest, CI, toolchain e VPS |
| GLM | OK pieno | OK equivalente | OK pieno | OK equivalente | OK pieno | OK pieno | Inbox `#14`; Dependabot aggiunto; `docs/CONTEXT.md` punta a `package.json` come source of truth versione; tag/GitHub Release definiti per release prodotto reale |
| SendChimp | OK pieno | OK pieno | OK pieno | OK equivalente | OK pieno | OK pieno | Nessuna PR aperta; inbox `#2`; tag/GitHub Release definiti per release prodotto reale |
| SyncBay | OK pieno | OK equivalente | OK pieno | OK equivalente | OK pieno | OK pieno | Inbox `#2`; Vercel production pilota distinta da Shopify App Store production; tag/GitHub Release solo per release prodotto reale |
| TRAM | OK pieno | OK equivalente | OK pieno | OK pieno | OK pieno | OK pieno | Inbox `#2`; SemVer `0.x`, tag/GitHub Release `v0.2.0` già esistenti; nessun target deploy approvato |
| Sentinel | OK pieno | OK equivalente | OK pieno | OK equivalente | OK pieno | OK pieno | Inbox `#4` marcata `codex-feedback-inbox`; runtime GitHub Actions e dashboard Vercel/Blob sono canali distinti; tag/GitHub Release solo per tool/dashboard |

## Interventi del ciclo correttivo

- SendChimp: PR `max23468/SendChimp#21` mergiata; aggiunto
  `quality:react-doctor`, rinominato `docs/context.md` in `docs/CONTEXT.md`,
  corretto export non usato, verificato React Doctor `100 / 100` e controllato
  deploy Vercel production `Ready` con `/api/health` OK.
- Sentinel: PR `max23468/Sentinel#2` mergiata; aggiunti Codex inbox workflow e
  handler, poi corretto handler con label gestita e limite ai thread actionable;
  il modello con label `codex-feedback-inbox` è stato promosso alle altre repo.
- Pratix: PR `max23468/Pratix#157` mergiata; aggiunto controllo PR title
  dedicato.
- SyncBay: PR `max23468/SyncBay#30` mergiata; aggiunto controllo PR title
  dedicato.
- GLM: Dependabot resta standard Atlas pieno; i failure storici nella finestra globale GitHub Actions non cambiano la regola.
- TRAM: definita la policy SemVer/release con commit `783b783` `[skip ci]`;
  nessun deploy eseguito perché non esiste target deploy approvato.
- FiscalBay: Python `3.13` è baseline unica dopo il riallineamento di manifest,
  CI, toolchain e VPS.
- Atlas semantic compliance: aggiunta `docs/SEMANTIC_CHECKLIST.md`; riallineati
  basename Markdown, registri `DECISIONS`/`DECISIONS_PENDING`, backlog wording,
  context, publication docs-only, Dependabot GLM/Sentinel e versioning pending
  per GLM/SendChimp/SyncBay.
- Atlas: aggiunti `docs/PUBLISH_DEPLOY_RELEASE.md`,
  `docs/STANDARD_CANDIDATES.md`, `docs/APPLYING_ATLAS.md` e
  `CHECKLIST-NUOVA-REPO.md` per rendere operativo il metodo trasversale senza
  applicarlo automaticamente alle altre repo.
- Atlas: aggiunto `docs/NEXT_STEPS.md` per separare prossimi passi Atlas da
  sviluppo prodotto delle repo coordinate.

## Regola temporanea GitHub Actions

La regola Atlas ora prevede che GitHub Actions possa essere usata nelle repo coordinate
quando riavviata e verificata; le esecuzioni passate restano contesto storico.
Questo però non significa che GitHub sia già fermo:

- non usare Actions come gate ordinario;
- preferire verifiche locali equivalenti e dichiararle;
- usare `[skip ci]` sui commit di sola governance quando si pubblica comunque;
- tenere disabilitato manualmente solo i workflow codex PR comments dove ancora non
  necessario;
- verificare la riattivazione workflow/runtime on-demand secondo audit recente;
- non declassare Dependabot: resta standard pieno, anche se alcune repo hanno
  avuto sospensioni temporanee storiche;
- eseguire deploy applicativi solo quando il diff e la policy della repo lo
  richiedono davvero.
