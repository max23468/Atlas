# Pattern candidati a standard Atlas

Data ultimo aggiornamento: 2026-05-31.

Questo registro serve a non perdere i pattern maturi emersi nelle repo
coordinate e, allo stesso tempo, a non trasformare ogni scelta locale in uno
standard trasversale.

## Legenda

- `Promosso`: è già uno standard Atlas.
- `Candidato`: è promettente, ma serve altra evidenza o una decisione esplicita.
- `Repo-specifico`: va preservato nella repo, ma non generalizzato.
- `Sospeso`: è utile, ma non va attivato nelle condizioni operative attuali.
- `Respinto`: non va standardizzato.

## Matrice

| Pattern | Stato | Evidenza | Uso Atlas |
| --- | --- | --- | --- |
| Discovery degli extra repo-specifici prima dei template | Promosso | GLM, TRAM, SyncBay, SendChimp | Regola operativa in `AGENTS.md`, `CHECKLIST-IMPLEMENTAZIONE.md`, `CHECKLIST-NUOVA-REPO.md` e `docs/APPLYING_ATLAS.md` |
| Branch dedicata per interventi Atlas su repo coordinate | Promosso | Ciclo multi-repo Atlas | Obbligatoria prima di modifiche; worktree separato quando serve isolamento reale |
| Separazione esplicita tra publish, release e deploy | Promosso | Tutte le repo coordinate | Fonte sintetica in `docs/PUBLISH_DEPLOY_RELEASE.md` |
| Runbook deploy con target, comando e verifica | Promosso come principio | Pratix, DocMolder, FiscalBay, GLM, SyncBay, SendChimp | I dettagli restano repo-specifici; Atlas richiede solo che esistano quando si deploya |
| Codex feedback inbox | Promosso con condizione | Atlas, Pratix, DocMolder, FiscalBay, GLM, SendChimp, SyncBay, TRAM, Sentinel | Da usare dove ci sono PR operative ricorrenti; il workflow mantiene la issue canonica marcata `codex-feedback-inbox` |
| React Doctor | Promosso con condizione | Pratix, GLM, SendChimp, SyncBay, TRAM, Sentinel | Obbligatorio per app React dopo release major/minor o modifiche React trasversali, con `npx --yes react-doctor@latest` |
| Basename Markdown univoci | Promosso | TRAM, decisione Atlas 0004 | Regola trasversale: niente due file Markdown con lo stesso basename nella stessa repo |
| Decision register separato dagli ADR puntuali | Promosso | TRAM, DocMolder, decisione utente Atlas | Standard pieno: registro stabile, pending separato e ADR puntuali con basename univoci |
| Changelog/frontend versioning locale senza GitHub Release | Promosso come fase transitoria limitata | SendChimp, SyncBay | Ammesso solo per docs-only, lavori pre-release o stati non ancora rilasciati come prodotto reale |
| Release prodotto reale con tag/GitHub Release separata dal deploy | Promosso | Tutte le repo coordinate con release prodotto reale | Ogni release prodotto reale deve creare sempre tag Git e GitHub Release `vX.Y.Z`; source of truth versione, changelog, comando e rapporto con deploy restano repo-specifici |
| Allegati, benchmark o fonti esterne fuori dal flusso Git ordinario | Repo-specifico con principio comune | GLM, TRAM, FiscalBay, DocMolder | Preservare LFS, fixture o archivi solo secondo policy locale e senza dati sensibili |
| Dependabot come baseline universale | Promosso | Tutte le repo coordinate con dipendenze, manifest compatibili o workflow GitHub Actions | Standard pieno Atlas; la pausa temporanea non ne declassa il livello |
| Runtime operativo su GitHub Actions | Repo-specifico e riallineato | Sentinel | Non generalizzare; il runtime è operativo con monitoraggio post-riavvio |

## Standard già promossi

- Discovery repo-specifica prima di qualunque template.
- Branch dedicata prima di modificare repo coordinate; worktree separato quando
  il checkout va preservato o il lavoro è parallelo/lungo.
- Separazione tra `pubblica`, `rilascia` e `deploya`.
- Verifiche proporzionate al rischio e dichiarate senza inventare risultati.
- React Doctor solo per app React e solo nei casi previsti.
- Codex inbox solo dove il volume di PR/commenti la giustifica; quando esiste,
  la issue canonica usa la label `codex-feedback-inbox`.
- Basename Markdown univoci: `README.md` solo in root, `docs/INDEX.md` come
  indice documentale e `docs/DECISIONS.md` come indice decisionale.
- Lifecycle decisionale completo: registro stabile, pending separato e ADR
  puntuali.
- Dependabot come standard pieno nelle repo con dipendenze, manifest
  compatibili o workflow GitHub Actions.

## Candidati da rivalutare

## Pattern da preservare ma non generalizzare

- Sentinel come runtime schedulato GitHub Actions.
- GLM con Cloudflare Pages e allegati gara gestiti come fonti specifiche.
- DocMolder con flusso Telegram-first, release manuale e runbook VPS.
- FiscalBay con Python `3.13` come baseline unica e deploy/release via script
  locali/VPS fuori da GitHub Actions.

## Pattern respinti come stato stabile

- Changelog/versioning locale senza tag o GitHub Release: ammesso solo per
  docs-only, lavori pre-release o stati dove non esiste ancora release prodotto
  reale.

## Criterio di promozione

Un pattern può diventare standard Atlas quando:

- esiste evidenza in almeno due repo comparabili o una decisione esplicita;
- non aumenta rumore operativo, costo o fragilità;
- non viola gli `AGENTS.md` locali;
- è verificabile senza segreti, dati reali o provider non approvati;
- può essere documentato come principio senza cancellare differenze tecniche
  motivate.
