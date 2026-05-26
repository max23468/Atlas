# Pattern candidati a standard Atlas

Data ultimo aggiornamento: 2026-05-26.

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
| Codex feedback inbox | Promosso con condizione | Pratix, DocMolder, FiscalBay, GLM, SendChimp, SyncBay, TRAM, Sentinel | Da usare dove ci sono PR operative ricorrenti; esecuzione workflow sospesa finché Actions è senza budget |
| React Doctor | Promosso con condizione | Pratix, GLM, SendChimp, SyncBay, TRAM | Obbligatorio per app React dopo release minor o modifiche React trasversali |
| Basename Markdown univoci | Candidato | TRAM | Utile dove la repo lo richiede; non imporre ad Atlas perché `docs/decisions/README.md` è intenzionale |
| Decision register separato dagli ADR puntuali | Candidato | TRAM | Utile quando ci sono molte decisioni operative; non obbligatorio per repo piccole |
| Changelog frontend locale senza GitHub Release | Candidato | GLM, SendChimp, SyncBay | Da usare solo quando tag/GitHub Release non sono ancora policy mature |
| Separazione tra nome prodotto e URL tecnico | Candidato | GLM | Utile per prodotti con brand, repository e runtime non allineati |
| Allegati, benchmark o fonti esterne fuori dal flusso Git ordinario | Repo-specifico con principio comune | GLM, TRAM, FiscalBay, DocMolder | Preservare LFS, fixture o archivi solo secondo policy locale e senza dati sensibili |
| Dependabot come baseline universale | Candidato sospeso | GLM, Sentinel, repo con dipendenze runtime | Attivare solo se dipendenze reali, budget Actions e rumore operativo sono sostenibili |
| Runtime operativo su GitHub Actions | Repo-specifico e sospeso | Sentinel | Non generalizzare; oggi resta sospeso per budget Actions |

## Standard già promossi

- Discovery repo-specifica prima di qualunque template.
- Branch dedicata prima di modificare repo coordinate; worktree separato quando
  il checkout va preservato o il lavoro è parallelo/lungo.
- Separazione tra `pubblica`, `rilascia` e `deploya`.
- Verifiche proporzionate al rischio e dichiarate senza inventare risultati.
- React Doctor solo per app React e solo nei casi previsti.
- Codex inbox solo dove il volume di PR/commenti la giustifica.

## Candidati da rivalutare

- Basename Markdown univoci.
- Registro decisionale separato dagli ADR puntuali.
- Changelog frontend locale senza tag o GitHub Release.
- Separazione tra nome prodotto, repository e URL runtime.
- Dependabot con soglia esplicita di sostenibilità.

## Pattern da preservare ma non generalizzare

- Sentinel come runtime schedulato GitHub Actions.
- GLM con Cloudflare Pages e allegati gara gestiti come fonti specifiche.
- FiscalBay con compatibilità Python `>=3.10` e VPS `3.13` come runtime
  operativo controllato.
- DocMolder con flusso Telegram-first, Release Please e runbook VPS.

## Criterio di promozione

Un pattern può diventare standard Atlas quando:

- esiste evidenza in almeno due repo comparabili o una decisione esplicita;
- non aumenta rumore operativo, costo o fragilità;
- non viola gli `AGENTS.md` locali;
- è verificabile senza segreti, dati reali o provider non approvati;
- può essere documentato come principio senza cancellare differenze tecniche
  motivate.
