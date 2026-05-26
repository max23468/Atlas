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
| Verde | Atlas, Pratix, FiscalBay, GLM, SendChimp | Nessun blocco operativo immediato nello snapshot aggiornato del `2026-05-26` |
| Attenzione | DocMolder, SyncBay, TRAM, Sentinel | Esistono workflow recenti non verdi, workflow sospesi, vincoli runtime o decisioni production da ricontrollare prima del prossimo lavoro |
| Bloccato | Nessuno | Nessun blocco trasversale aperto dopo il consolidamento Sentinel |

Nota:
I gap Atlas su Codex inbox, versioning, basename Markdown, lifecycle
decisionale, publish proporzionata o toolchain sono stati riallineati a livello
governance/documentazione. Restano da rivalutare dal `2026-06-02` le sospensioni
Actions. Le decisioni tag/GitHub Release per GLM, SendChimp, SyncBay e Sentinel
sono state chiuse come policy documentale: non generano tag ora e valgono solo
per release prodotto reali.

## Matrice

| Progetto | Health | Ultimo segnale verificato | Rischio operativo da tenere in vista | Prossimo controllo sensato |
| --- | --- | --- | --- | --- |
| Atlas | Verde | Nessuna PR aperta; repo docs-first senza runtime; audit completo Atlas eseguito il `2026-05-26` | Nessun rischio runtime; tenere allineato lo snapshot documentale allo stato GitHub reale | Aggiornare `docs/HEALTH.md` quando cambia stato di una repo o di un workflow trasversale |
| Pratix | Verde | PR `#159` mergiata su `main`; Vercel production `READY` con commit `59fbb05`; `/` e `/novita` rispondono `200`; nessuna release SemVer richiesta dal dry-run (`Non versionato`) | Repo già matura: non appesantire processi o UI; React Doctor dopo release minor | Solo audit read-only o aggiornamento stato salvo scope Pratix esplicito |
| DocMolder | Attenzione | PR `#168` mergiata su `main` con commit `c3aeb05`; inbox Codex `#149` senza commenti aperti; branch remota rimossa; run `Dependency Graph` cancellata durante la finestra Actions | `Release Please` e `VPS Check` restano sospesi durante la finestra Actions; preservare Release Please e runbook locali | Dal `2026-06-02` rivalutare riattivazione `Release Please`/`VPS Check` e ricontrollare i run remoti |
| FiscalBay | Verde | PR `#80` mergiata su `main` con commit `d67c912`; inbox Codex `#69` senza thread actionable; branch remota rimossa; run `Dependency Graph` cancellata durante la finestra Actions | Non rompere supporto `>=3.10` senza decisione repo-specifica; deploy VPS resta repo-specifico | Solo audit read-only; upgrade Python o deploy VPS solo con scope FiscalBay esplicito |
| GLM | Verde | PR `#12` mergiata su `main`; deploy Cloudflare Pages produzione completato sul commit `0ad6a6a`; home e `/api/version` rispondono `200`; nessuna release SemVer richiesta dal dry-run | Non usare Vercel/Supabase; non toccare allegati gara o Git LFS senza scope esplicito | Audit read-only; ricontrollare i failure Actions storici dal `2026-06-02` |
| SendChimp | Verde | PR `#24` mergiata su `main`; Vercel production `READY`; `/api/health` risponde `200` e `/` redirige correttamente a `/auth/sign-in`; nessuna release SemVer richiesta dal dry-run (`Non versionato`) | MVP manuale e vincolo free-tier; tag/GitHub Release ammessi solo per release prodotto reali, separati da deploy Vercel e invii reali | Solo controllo governance/provider read-only salvo scope SendChimp esplicito |
| SyncBay | Attenzione | PR `#48` mergiata; release locale `0.17.2` pubblicata con PR `#50` e commit `b28ef47`; Vercel production `READY`; home/about/privacy rispondono `200`; smoke UI passato | React Doctor resta con warning preesistenti; App Store production, billing e tag/GitHub Release restano decisioni separate | Dal `2026-06-02` rivalutare workflow sospesi; App Store/billing/support policy solo con decisione SyncBay |
| TRAM | Attenzione | PR `#9` mergiata su `main` con commit `581dd43`; nessuna release/deploy eseguita perché la policy richiede richiesta esplicita e non esiste target deploy approvato | Failure remoto storico senza step/log durante finestra Actions; release e deploy restano distinti | Dal `2026-06-02` ricontrollare `Repo Hygiene`; non rilanciare Actions prima senza decisione |
| Sentinel | Attenzione | PR `#8` mergiata su `main`; dashboard Vercel production `READY` (`dpl_FNWzcTzDfRVasCSWoSHDesvtagtL`); Basic Auth risponde `401` senza credenziali; runtime Actions non riattivato | Monitor schedulato sospeso fino al `2026-06-01` compreso; release versionate valgono solo per tool/dashboard, non per scan/report | Rivalutare dal `2026-06-02` la riattivazione del workflow e ricontrollare `PR Title` |

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
