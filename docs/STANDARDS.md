# Matrice standard Atlas

Data ultimo aggiornamento: 2026-05-24

Questa matrice verifica gli standard che Atlas deve rendere espliciti e, dove
possibile, uniformare nelle repo coordinate. Atlas coordina e pubblica la
governance: non forza runtime, release, deploy o workflow dove la policy della
repo non li prevede.

Legenda:

- `OK`: standard presente o equivalente repo-specifico accettato.
- `Parziale`: presente ma incompleto o con decisione aperta.
- `Sospeso`: standard applicabile ma temporaneamente non attivato.
- `N/A`: non applicabile alla fase o allo stack.

## Standard trasversali

| Area | Regola Atlas | Stato attuale |
| --- | --- | --- |
| Documenti canonici | `AGENTS.md`, `README.md`, indice, roadmap, backlog, context, toolchain e decisioni dove applicabili | OK nelle repo coordinate; SendChimp ora usa `docs/CONTEXT.md` canonico |
| Source of truth | Ogni repo dichiara fonti primarie e documenti da leggere prima di intervenire | OK, con eccezioni motivate per registri storici come `docs/DECISIONS.md` |
| GitHub baseline | PR template, issue template, PR title check o equivalente, policy PR/merge | OK o equivalente; Pratix e SyncBay hanno ora `pr-title.yml` dedicato |
| Codex feedback inbox | Workflow/handler e issue `Codex feedback inbox` dove ci sono PR operative ricorrenti | OK nel codice in Pratix, DocMolder, FiscalBay, GLM, SendChimp, SyncBay, TRAM e Sentinel; esecuzione workflow sospesa finché Actions resta senza budget |
| Versioning | Semantica comune; strumenti repo-specifici dichiarati | OK; TRAM ha ora policy SemVer/release in ADR dedicata |
| Publish/deploy/release | Parole chiave comuni, target e comandi repo-specifici, niente deploy/release inventati | OK; deploy applicativo eseguito solo quando la repo e il diff lo richiedono |
| Verifiche | Gate proporzionati al rischio, senza test inventati | OK come regola; GitHub Actions non usate come gate durante esaurimento minuti |
| React Doctor | Obbligatorio per app React dopo release minor o modifiche React trasversali | OK in Pratix, GLM, SendChimp, SyncBay e TRAM |
| Dependabot | Solo dove ci sono dipendenze runtime reali e budget/rumore sono sostenibili | OK dove già attivo; sospeso su GLM e Sentinel finché i minuti Actions sono esauriti |
| Toolchain/versioni | Runtime, package manager, lockfile e versioni minime dichiarati | OK; FiscalBay mantiene supporto `>=3.10` e runtime VPS `3.13` come compatibilità operativa |
| Privacy/sicurezza | No segreti, no dati reali non necessari, provider/API variabili verificati | OK come policy; resta repo-specifico il dettaglio operativo |
| Artefatti generati | `.DS_Store`, cache, build output e file temporanei non sono contenuto progettuale | OK come regola; Sentinel conserva invece output applicativi previsti |
| Handoff | `docs/CONTEXT.md` o path dichiarato per riprendere il lavoro | OK; SendChimp è stato riallineato a `docs/CONTEXT.md` |

## Matrice repo

| Repo | Docs | GitHub/PR title | Codex inbox | Versioning/release | React Doctor | Dependabot | Note |
| --- | --- | --- | --- | --- | --- | --- | --- |
| Atlas | OK | OK | Sospeso | N/A | N/A | N/A | Niente workflow Codex finché non ci sono commenti ricorrenti e finché Actions sono limitate |
| Pratix | OK | OK | OK | OK | OK | OK | PR `max23468/Pratix#157` ha aggiunto `pr-title.yml`; nessun deploy richiesto dal diff |
| DocMolder | OK | OK equivalente | OK | OK | N/A | OK | PR title controllato nella CI/policy locale, non con workflow separato |
| FiscalBay | OK | OK | OK | OK | N/A | OK | Python `>=3.10` resta supporto dichiarato; VPS `3.13` è compatibilità operativa, non upgrade da forzare |
| GLM | OK | OK | OK | OK | OK | Sospeso | Dependabot aggiunto e poi sospeso con commit `[skip ci]` per evitare run durante budget Actions esaurito |
| SendChimp | OK | OK | OK | OK locale | OK | OK | PR `max23468/SendChimp#21`: `quality:react-doctor`, `docs/CONTEXT.md`, React Doctor `100 / 100`; Vercel production ready e health OK |
| SyncBay | OK | OK | OK | OK locale | OK | OK | PR `max23468/SyncBay#30` ha aggiunto `pr-title.yml`; no release/deploy/App Store |
| TRAM | OK | OK | OK | OK | OK | OK | Policy SemVer/release definita in `docs/decisions/0003-versioning-release-policy.md`; niente `docs/decisions/README.md` per regola basename |
| Sentinel | OK | OK | OK | Parziale | N/A | Sospeso | PR `max23468/Sentinel#2` ha aggiunto Codex inbox; issue `#4` pulita; workflow runtime `Sentinel` e Dependabot sospesi per budget Actions |

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
- GLM: aggiunto e poi sospeso Dependabot con commit diretti `[skip ci]`, per
  non consumare ulteriori GitHub Actions durante l'esaurimento minuti.
- TRAM: definita la policy SemVer/release con commit `783b783` `[skip ci]`;
  nessun deploy eseguito perché non esiste target deploy approvato.
- FiscalBay: verificata la policy Python repo-specifica; nessun cambio forzato a
  `3.13` perché il supporto dichiarato resta `>=3.10`.

## Regola temporanea GitHub Actions

Finché il budget GitHub Actions è esaurito:

- non usare Actions come gate ordinario;
- preferire verifiche locali equivalenti e dichiararle;
- usare `[skip ci]` sui commit di sola governance quando si pubblica comunque;
- evitare di attivare nuovi workflow schedulati o Dependabot dove generano run;
- tenere disabilitato manualmente il workflow `Codex PR comments` su Pratix,
  DocMolder, FiscalBay, GLM, SendChimp, SyncBay, TRAM e Sentinel;
- considerare `Dependabot Updates` un workflow dinamico non disabilitabile via
  Actions API; sospendere via config repo solo se inizia a generare run;
- tenere disabilitato manualmente anche il workflow runtime `Sentinel`, perché
  usa GitHub Actions come canale operativo schedulato;
- eseguire deploy applicativi solo quando il diff e la policy della repo lo
  richiedono davvero.
