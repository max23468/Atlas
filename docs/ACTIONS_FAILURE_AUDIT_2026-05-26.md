# Audit failure GitHub Actions del 2026-05-26

Questo audit classifica i run GitHub Actions storici rimasti rossi durante la
finestra di sospensione dei minuti Actions.

Perimetro:

- ricognizione read-only con `gh run list` e `gh run view`;
- nessun workflow rilanciato;
- nessun workflow usato come gate di pubblicazione;
- log falliti non disponibili sui run campione: `gh run view --log-failed` ha
  restituito `log not found`;
- rivalutazione operativa conclusa il `2026-05-27`, dopo riavvio generale dei workflow.

## Esito sintetico

| Repo | Run verificati | Classificazione | Azione |
| --- | --- | --- | --- |
| DocMolder | `Release Please` `26459559695`; `VPS Check` `26396552938` | Failure storici su `main` durante sospensione Actions; workflow disabilitati manualmente | Non gate; riattivati dopo verifica |
| GLM | `CI` `26402576569`; branch storico `work` `26402547181`/`26402547178`; `CI` `26399261548`; Dependabot cancellato `26463136348` | Failure storici legati a lavoro Excel/CI precedente; nessuna PR o branch residua aperta | Non gate; ispezione CI prima del prossimo lavoro GLM |
| TRAM | `Repo Hygiene` `26460797194` | Failure storico su release `0.2.0`; log non disponibili; verifica locale registrata come passata nello snapshot Atlas | Non gate; ricontrollato dopo riavvio |
| SyncBay | `PR Title` `26444965298` e `26370846355`; serie `PR Title` su branch `codex/*`; Dependabot cancellati | Failure storici su PR/branch già chiusi o mergeati; workflow disabilitati manualmente | Non gate; riavviato dopo verifica |
| Sentinel | `PR Title` `26445555043`; `PR Title` `26370823951`; runtime `Sentinel` `26367032307`, `26367181521`, `26367301441`, `26367767364` | Failure/cancelled storici; runtime schedulato riavviato | Non gate; classificato in mantenimento post-riavvio |

## Dettaglio verificato

### DocMolder

- `26459559695`: workflow `Release Please`, evento `push`, branch `main`, titolo
  `chore(docs): align decision index governance`, job `release-please`, esito
  `failure`, creato il `2026-05-26T15:57:33Z`.
- `26396552938`: workflow `VPS Check`, evento `schedule`, branch `main`, job
  `Check Oracle VPS`, esito `failure`, creato il `2026-05-25T10:46:26Z`.

Classificazione: storico, non gate corrente. `Release Please` e `VPS Check`
restano workflow repo-specifici da preservare; sono stati riavviati dopo la verifica.

### GLM

- `26402576569`: workflow `CI`, evento `push`, branch `main`, titolo
  `Add Excel VBA toolkit (Pacchetto Excel) with packaging, manifest and ...`,
  job `Verifica simulatore` fallito e `Preview Cloudflare Pages` saltato.
- `26402547181` / `26402547178`: failure storici su branch `work`.
- `26399261548`: failure `CI` precedente su lavoro Excel.
- `26463136348`: Dependabot cancellato, non classificato come failure codice.

Classificazione: storico, non gate corrente. Prima di un nuovo intervento GLM va
ricontrollata la CI, ma non durante la sospensione Actions.

### TRAM

- `26460797194`: workflow `Repo Hygiene`, evento `push`, branch `main`, titolo
  `chore: release 0.2.0`, job `Secrets, docs and repo hygiene`, esito
  `failure`, creato il `2026-05-26T16:20:32Z`.

Classificazione: storico, non gate corrente. Lo snapshot Atlas registra
`npm run verify` passato localmente; il remoto va rivalutato quando Actions
torna disponibile.

### SyncBay

- `26444965298`: workflow `PR Title`, evento `pull_request`, branch
  `codex/import-mapping-snapshot`, job `Conventional PR title`, esito `failure`.
- `26370846355`: workflow `PR Title`, evento `pull_request`, branch
  `codex/atlas-pr-title-baseline`, job `Conventional PR title`, esito
  `failure`.
- Altri failure `PR Title` del `2026-05-25` e `2026-05-26` risultano legati a
  branch `codex/*` già chiusi o mergeati.

Classificazione: storico, non gate corrente. I workflow `PR Title` e
`Codex PR comments` sono stati verificati in riavvio.

### Sentinel

- `26445555043`: workflow `PR Title`, evento `pull_request`, branch
  `codex/sentinel-dashboard-policy`, job `Conventional PR title`, esito
  `failure`.
- `26370823951`: workflow `PR Title`, branch
  `codex/atlas-governance-baseline`, esito `failure`.
- `26367032307`, `26367181521`, `26367301441`: workflow runtime `Sentinel`,
  evento `main`, esito `failure`.
- `26367767364`: workflow runtime `Sentinel`, evento `main`, esito `cancelled`.

Classificazione: storico, non gate corrente. Il runtime schedulato è stato riavviato.

## Regola operativa

La regola temporanea di cui sopra è terminata il `2026-05-27`. Restano:

- rilanciare questi workflow;
- usare questi run come gate;
- aggiungere nuovi workflow per aggirare la sospensione.

Step successivi completati: repo per repo verificati e workflow riavviati in linee guida
stabili, con sostituzioni tramite verifiche locali o canali diretti dove previsto.
