# Matrice standard Atlas

Data ultimo aggiornamento: 2026-05-26

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
| Source of truth | Ogni repo dichiara fonti primarie e documenti da leggere prima di intervenire | `OK pieno`: dichiarate; restano alcune differenze motivate, per esempio registri storici come `docs/DECISIONS.md` |
| Basename Markdown univoci | Niente due file Markdown con lo stesso basename nella stessa repo; usare `docs/INDEX.md` per indice documentale e `docs/DECISIONS.md` per indice decisionale | `OK pieno`: verificato sui file Markdown tracciati di tutte le repo coordinate |
| Lifecycle decisionale | Registro stabile, pending separato e ADR puntuali: `docs/DECISIONS.md`, `docs/DECISIONS_PENDING.md` e `docs/decisions/NNNN-slug.md` | `OK pieno`: modello presente in tutte le repo coordinate |
| Scope Atlas vs prodotto | Atlas censisce e coordina; non propone sviluppo prodotto delle repo come prossimo passo generico | `OK pieno`: procedura dedicata in `docs/NEXT_STEPS.md` |
| Isolamento Git | Interventi Atlas su repo coordinate sempre su branch dedicata; worktree separato quando serve preservare stato o parallelizzare | `OK pieno`: regola Atlas definita; da applicare in ogni intervento futuro |
| GitHub baseline | PR template, issue template, PR title check o equivalente, policy PR/merge | `OK equivalente`: baseline presente; alcune repo usano `pr-title.yml`, altre controlli equivalenti nella CI/policy locale |
| Codex feedback inbox | Issue `Codex feedback inbox` e, quando le Actions non sono sospese, handler/workflow coerente dove ci sono PR operative ricorrenti | `Sospeso`: Atlas va allineato tramite issue inbox; nuovi workflow o riattivazioni Actions restano sospesi fino al `2026-06-01` compreso |
| Versioning | Semantica comune; source of truth dichiarata; tag e GitHub Release quando esiste release reale | `OK equivalente`: GLM, SendChimp e SyncBay dichiarano source of truth locale e decisione pending per tag/GitHub Release prima di release prodotto reale |
| Publish/deploy/release | Parole chiave comuni, target e comandi repo-specifici, niente deploy/release inventati | `OK pieno`: matrice sintetica in `docs/PUBLISH_DEPLOY_RELEASE.md` |
| Pubblicazione proporzionata | Ogni repo deve dichiarare un percorso proporzionato al diff: docs-only/governance-only senza smoke, deploy, release o gate runtime non pertinenti | `OK pieno`: principio dichiarato nei context/policy repo o già presente in policy locale |
| Verifiche | Gate proporzionati al rischio, senza test inventati | `Sospeso`: fino al `2026-06-01` compreso non usare GitHub Actions come gate; raccontare eventuali run failure/cancelled come stato remoto, non come verifica richiesta |
| React Doctor | Obbligatorio per app React dopo release minor o modifiche React trasversali | `OK pieno`: applicato in Pratix, GLM, SendChimp, SyncBay e TRAM |
| Dependabot | Standard pieno in tutte le repo con dipendenze o manifest compatibili | `OK pieno`: GLM e Sentinel hanno `dependabot.yml`; le cancellazioni Actions storiche non declassano lo standard |
| Toolchain/versioni | Runtime, package manager, lockfile e versioni minime dichiarati | `OK equivalente`: FiscalBay mantiene Python `>=3.10` come compatibilità repo-specifica motivata, con VPS `3.13` come runtime controllato |
| Privacy/sicurezza | No segreti, no dati reali non necessari, provider/API variabili verificati | `OK pieno`: policy comune presente; i dettagli restano repo-specifici |
| Artefatti generati | `.DS_Store`, cache, build output e file temporanei non sono contenuto progettuale | `OK equivalente`: regola comune rispettata; Sentinel mantiene output applicativi previsti dal proprio runtime |
| Handoff | `docs/CONTEXT.md` o path dichiarato per riprendere il lavoro | `OK pieno`: handoff presente; SendChimp riallineato a `docs/CONTEXT.md` |

## Matrice repo

| Repo | Docs | GitHub/PR title | Codex inbox | Versioning/release | React Doctor | Dependabot | Note |
| --- | --- | --- | --- | --- | --- | --- | --- |
| Atlas | OK pieno | OK pieno | Sospeso | N/A | N/A | N/A | Inbox Codex issue `#3`; nessun nuovo workflow Actions prima del `2026-06-02` |
| Pratix | OK pieno | OK pieno | OK pieno | OK pieno | OK pieno | OK pieno | Nessuna PR aperta; inbox `#34`; `Dependabot Updates` cancellato il `2026-05-25` |
| DocMolder | OK pieno | OK equivalente | OK pieno | OK pieno | N/A | OK pieno | PR title controllato nella CI/policy locale; branch residua rimossa; `Release Please`/`VPS Check` disabilitati manualmente nella finestra Actions |
| FiscalBay | OK pieno | OK pieno | OK pieno | OK pieno | N/A | OK pieno | Nessuna PR aperta; inbox `#69`; Python `>=3.10` è compatibilità repo-specifica motivata, non mismatch da forzare |
| GLM | OK pieno | Da riallineare | OK pieno | OK equivalente | OK pieno | OK pieno | Dependabot aggiunto; `docs/CONTEXT.md` punta a `package.json` come source of truth versione; tag/GitHub Release in `docs/DECISIONS_PENDING.md` |
| SendChimp | OK pieno | OK pieno | OK pieno | OK equivalente | OK pieno | OK pieno | Nessuna PR aperta; inbox `#2`; tag/GitHub Release da decidere prima di release prodotto reale |
| SyncBay | OK pieno | OK equivalente | OK equivalente | OK equivalente | OK pieno | OK pieno | Checkout `main` pulito, Vercel production `READY`; tag/GitHub Release/App Store production restano decisione pending esplicita |
| TRAM | OK pieno | OK equivalente | OK pieno | OK pieno | OK pieno | OK pieno | Branch locale residua rimossa; `Repo Hygiene` fallita senza log su `main`, ma `npm run verify` passa localmente |
| Sentinel | OK pieno | Da riallineare | OK pieno | OK equivalente | N/A | OK pieno | Dependabot aggiunto; release versionate e runtime post-Actions restano in `docs/DECISIONS_PENDING.md` |

## Interventi del ciclo correttivo

- SendChimp: PR `max23468/SendChimp#21` mergiata; aggiunto
  `quality:react-doctor`, rinominato `docs/context.md` in `docs/CONTEXT.md`,
  corretto export non usato, verificato React Doctor `100 / 100` e controllato
  deploy Vercel production `Ready` con `/api/health` OK.
- Sentinel: PR `max23468/Sentinel#2` mergiata; aggiunti Codex inbox workflow e
  handler, poi corretto handler con label gestita e limite ai thread actionable;
  issue `#4` è la inbox canonica, issue `#3` chiusa come superata.
- Pratix: PR `max23468/Pratix#157` mergiata; aggiunto controllo PR title
  dedicato.
- SyncBay: PR `max23468/SyncBay#30` mergiata; aggiunto controllo PR title
  dedicato.
- GLM: Dependabot resta standard Atlas pieno; la sospensione attuale e
  temporanea nella finestra globale GitHub Actions non cambia la regola.
- TRAM: definita la policy SemVer/release con commit `783b783` `[skip ci]`;
  nessun deploy eseguito perché non esiste target deploy approvato.
- FiscalBay: la policy Python `>=3.10` è classificata come compatibilità
  repo-specifica motivata, con VPS `3.13` come runtime controllato.
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

Fino al `2026-06-01` compreso, la regola Atlas è di non usare GitHub Actions
come gate e di non riattivare deliberatamente workflow nelle repo coordinate.
Questo però non significa che GitHub sia già fermo:

- non usare Actions come gate ordinario;
- preferire verifiche locali equivalenti e dichiararle;
- usare `[skip ci]` sui commit di sola governance quando si pubblica comunque;
- tenere disabilitato manualmente il workflow `Codex PR comments` su Pratix,
  DocMolder, FiscalBay, GLM, SendChimp, SyncBay, TRAM e Sentinel;
- tenere disabilitato manualmente anche il workflow runtime `Sentinel`, perché
  usa GitHub Actions come canale operativo schedulato;
- non riattivare workflow o gate basati su GitHub Actions prima del
  `2026-06-02`, salvo nuova decisione esplicita;
- non declassare Dependabot: resta standard pieno, anche se alcune repo sono
  temporaneamente sospese nella stessa finestra;
- eseguire deploy applicativi solo quando il diff e la policy della repo lo
  richiedono davvero.
