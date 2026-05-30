# Matrice health Atlas

Data ultimo aggiornamento: 2026-05-30

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
| Verde | Atlas, GLM, SendChimp | Nessun blocco operativo immediato nello snapshot aggiornato del `2026-05-27` |
| Attenzione | Pratix, FiscalBay, DocMolder, SyncBay, TRAM, Sentinel | Hardening tecnico-operativo in corso con rischi residui e controlli non ancora chiusi |
| Bloccato | Nessuno | Nessun blocco trasversale aperto dopo il consolidamento Sentinel |

Nota:
I gap Atlas su Codex inbox, versioning, basename Markdown, lifecycle
decisionale, publish proporzionata o toolchain sono stati riallineati a livello
governance/documentazione. Stato: workflow verificati e sospensione globale
Actions rimossa. Le decisioni su tag/GitHub Release per GLM, SendChimp,
SyncBay e Sentinel
sono formalizzate come policy documentali: non richiedono tag finché non esiste
una release prodotto reale.

## Matrice

| Progetto | Health | Ultimo segnale verificato | Rischio operativo da tenere in vista | Prossimo controllo sensato |
| --- | --- | --- | --- | --- |
| Atlas | Verde | Nessuna PR aperta; repo docs-first senza runtime; audit completo Atlas eseguito il `2026-05-26` | Nessun rischio runtime; tenere allineato lo snapshot documentale allo stato GitHub reale | Aggiornare `docs/HEALTH.md` quando cambia stato di una repo o di un workflow trasversale |
| Pratix | Attenzione | PR `#159` mergiata su `main`; `SECURITY.md`, `docs/SECURITY_HARDENING.md` e `docs/ROADMAP.md` aggiornati con hardening P0/P1; Vercel production `READY` con commit `59fbb05`; `/` e `/novita` rispondono `200`; nessuna release SemVer richiesta dal dry-run (`Non versionato`) | Gate P0/P1 documentato in `docs/SECURITY_HARDENING.md`: segreti, guardrail pre-merge e verifica CI; promuovere a verde solo dopo evidenza di completamento | Completare e registrare la verifica hardening P0/P1 indicata in `docs/SECURITY_HARDENING.md` |
| DocMolder | Attenzione | PR `#168` mergiata su `main` con commit `c3aeb05`; `docs/OPERATIONS_SECURITY.md` e `docs/SECURITY_HARDENING.md` aggiornati al `2026-05-27`; inbox Codex `#149` senza commenti aperti; branch remota rimossa | P0/P1 su pipeline VPS + Telegram-first: dry-run, artifact immutabile e lock esecuzione ancora da rendere verificabili | Verificare runbook VPS e checklist di deployment prima di nuove aperture operative |
| FiscalBay | Attenzione | PR `#80` mergiata su `main` con commit `d67c912`; `docs/SECURITY_HARDENING.md` e `docs/SECURITY_OPERATIONS.md` aggiornati il `2026-05-27`; inbox Codex `#69` senza thread actionable | P0/P1 su separazione ambienti e gestione webhook/API; non prevedere rotazioni preventive nel piano corrente | Chiudere controllo P0/P1 su segreti runtime e integrazioni prima di riaprire lavori sensibili |
| GLM | Verde | PR `#12` mergiata su `main`; deploy Cloudflare Pages produzione completato sul commit `0ad6a6a`; home e `/api/version` rispondono `200`; nessuna release SemVer richiesta dal dry-run | Non usare Vercel/Supabase; non toccare allegati gara o Git LFS senza scope esplicito | Audit read-only; ricontrollare i failure Actions storici dopo riavvio |
| SendChimp | Verde | PR `#24` mergiata su `main`; `docs/SECURITY_HARDENING.md` aggiornato il `2026-05-27`; Vercel production `READY`; `/api/health` risponde `200` e `/` redirige correttamente a `/auth/sign-in`; nessuna release SemVer richiesta dal dry-run (`Non versionato`) | Operativo stabile con vincolo free-tier; capacity check prima di estensioni | Controllo governance/provider read-only salvo scope SendChimp esplicito |
| SyncBay | Attenzione | PR `#48` mergiata; release locale `0.17.2` pubblicata con PR `#50` e commit `b28ef47`; `docs/SECURITY_HARDENING.md` e `SECURITY.md` aggiornati il `2026-05-27`; Vercel production `READY`; home/about/privacy rispondono `200`; smoke UI passato | P0/P1 su separazione credenziali webhooks e integrazioni in corso; App Store/billing restano separati dalla roadmap release | Workflow riavviati e verificati; richiedere checklist manuale prima di modifiche credenziali |
| TRAM | Attenzione | PR `#9` mergiata su `main` con commit `581dd43`; `docs/SECURITY_HARDENING.md` aggiornato il `2026-05-27`; nessuna release/deploy eseguita perché policy esplicita | P1/P2 di classificazione public/internal non ancora consolidato in tutte le doc di contesto | Ricontrollare perimetro pubblico interno e `Repo Hygiene` dopo riavvio |
| Sentinel | Attenzione | PR `#8` mergiata su `main`; dashboard Vercel production `READY` (`dpl_FNWzcTzDfRVasCSWoSHDesvtagtL`); `docs/SECURITY_HARDENING.md` aggiornato il `2026-05-27`; Basic Auth risponde `401` senza credenziali; runtime Actions attivo | P1 su env locali e retention report/scheduler; monitor settimanale e credenziali seguenti runbook | Verificare post-esecuzione workflow e rivedere retention nel runbook |

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
