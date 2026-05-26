# Matrice health Atlas

Data ultimo aggiornamento: 2026-05-26

Questa matrice è lo snapshot operativo dei progetti coordinati da Atlas. Serve a
decidere dove guardare prima, non sostituisce `docs/PROJECTS.md` né gli
`AGENTS.md` delle singole repo.

I gap semantici, documentali o di governance Atlas non cambiano da soli lo
stato health: vanno tracciati in `docs/SEMANTIC_COMPLIANCE_GAPS.md` e diventano
health `Attenzione` o `Bloccato` solo quando creano un rischio operativo reale.

## Legenda

| Stato | Significato | Azione |
| --- | --- | --- |
| Verde | Nessun blocco noto; ultimo allineamento o gate rilevante completato | Monitorare al prossimo ciclo o fare solo audit read-only se emerge un segnale |
| Attenzione | Nessun blocco immediato, ma c'è un rischio operativo o una decisione runtime da non dimenticare | Tenere in vista prima di cambiare codice, runtime o processo |
| Bloccato | C'è un impedimento operativo che blocca publish, deploy, release o uso previsto | Risolvere prima di nuove iniziative sulla repo |
| Non applicabile | La categoria non ha senso per quel progetto | Non forzare controlli o processi inutili |

## Sintesi

| Stato | Progetti | Motivo |
| --- | --- | --- |
| Verde | Atlas, Pratix, FiscalBay, TRAM | Nessun blocco operativo immediato nello snapshot aggiornato del `2026-05-26` |
| Attenzione | DocMolder, GLM, SendChimp, SyncBay, Sentinel | Esistono workflow recenti non verdi, vincoli runtime o segnali GitHub da ricontrollare prima del prossimo lavoro |
| Bloccato | Nessuno | Nessun blocco trasversale aperto dopo il consolidamento Sentinel |

Nota:
I gap Atlas su Codex inbox, versioning, basename Markdown, lifecycle
decisionale, Publish proporzionata o toolchain restano manutenzione governance
finché non diventano un problema operativo reale nella repo interessata.

## Matrice

| Progetto | Health | Ultimo segnale verificato | Rischio operativo da tenere in vista | Prossimo controllo sensato |
| --- | --- | --- | --- | --- |
| Atlas | Verde | Nessuna PR aperta; repo docs-first senza runtime; audit completo Atlas eseguito il `2026-05-26` | Nessun rischio runtime; tenere allineato lo snapshot documentale allo stato GitHub reale | Aggiornare `docs/HEALTH.md` quando cambia stato di una repo o di un workflow trasversale |
| Pratix | Verde | Nessuna PR aperta; inbox Codex `#34`; ultimo run GitHub `Dependabot Updates` cancellato il `2026-05-25` | Repo già matura: non appesantire processi o UI; React Doctor dopo release minor | Solo audit read-only o aggiornamento stato salvo scope Pratix esplicito |
| DocMolder | Attenzione | Nessuna PR aperta; checkout `main` pulito; branch residua rimossa; inbox Codex `#149`; commit docs-only `bf54615` pubblicato; `Release Please` fallita su `bf54615` senza log disponibili | Venv locale riparata; `Release Please` e `VPS Check` disabilitati manualmente durante la finestra Actions; preservare Release Please e runbook locali | Dal `2026-06-02` rivalutare riattivazione `Release Please`/`VPS Check` e ricontrollare il failure remoto |
| FiscalBay | Verde | Nessuna PR aperta; inbox Codex `#69`; ultimo run GitHub `Dependabot Updates` cancellato il `2026-05-25` | Non rompere supporto `>=3.10` senza decisione repo-specifica; deploy VPS resta repo-specifico | Solo audit read-only; upgrade Python solo con scope FiscalBay esplicito |
| GLM | Attenzione | Nessuna PR aperta; checkout `main` pulito; branch remota residua rimossa; inbox Codex `#3`; `CI` fallita su `main` il `2026-05-25` | Prima del prossimo lavoro GLM serve ricontrollare la `CI` su `main`; non toccare deploy Cloudflare o allegati Git LFS senza scope esplicito | Audit read-only e ispezione del failure `CI` prima di nuove modifiche GLM |
| SendChimp | Attenzione | Nessuna PR aperta; inbox Codex `#2`; ultimo run GitHub `Dependabot Updates` cancellato il `2026-05-25` | MVP manuale e vincolo free-tier; versioning/release ancora non pienamente riallineati | Solo controllo governance/provider read-only salvo scope SendChimp esplicito |
| SyncBay | Attenzione | Nessuna PR aperta; nessuna inbox Codex aperta; `PR Title` fallita il `2026-05-26` | Baseline GitHub non tutta verde; release pubblica ancora non standardizzata | Ricontrollare `PR Title` e lo stato inbox prima del prossimo lavoro SyncBay |
| TRAM | Verde | Nessuna PR aperta; inbox Codex `#2`; ultimo run GitHub `Dependabot Updates` cancellato il `2026-05-25` | Nessun target deploy approvato: release e deploy restano distinti | Solo audit read-only o aggiornamento stato salvo scope TRAM esplicito |
| Sentinel | Attenzione | Nessuna PR aperta; inbox Codex `#4`; `PR Title` fallita il `2026-05-26`; workflow runtime `Sentinel` disabilitato manualmente | Monitor schedulato sospeso fino al `2026-06-01` compreso; baseline GitHub non ancora tutta verde | Rivalutare dal `2026-06-02` la riattivazione del workflow e ricontrollare `PR Title` |

## Regole di aggiornamento

- Aggiornare questa matrice dopo publish, merge, deploy, release o workflow
  operativo significativo.
- Non usare questa matrice per autorizzare modifiche automatiche alle repo:
  prima serve sempre conferma esplicita sul target.
- Non usare questa matrice per registrare gap semantici o debiti documentali
  Atlas se non hanno ancora impatto operativo: per quelli usare
  `docs/SEMANTIC_COMPLIANCE_GAPS.md`.
- Se un dato dipende da provider, piani gratuiti, prezzi, API o limiti variabili,
  verificarlo live prima di trasformarlo in decisione.
- Se emerge un blocco reale, spostarlo anche in `docs/ROADMAP.md` o
  `docs/BACKLOG.md` secondo priorità.
- Tenere il dettaglio lungo in `docs/PROJECTS.md`; qui deve restare il colpo
  d'occhio operativo.

## Prossima revisione

- Dopo un cambio reale di stato repo, publish, merge, deploy o release.
- Oppure al prossimo ciclo di manutenzione periodica Atlas.
