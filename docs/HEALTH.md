# Matrice health Atlas

Data ultimo aggiornamento: 2026-05-24

Questa matrice è lo snapshot operativo dei progetti coordinati da Atlas. Serve a
decidere dove guardare prima, non sostituisce `docs/PROJECTS.md` né gli
`AGENTS.md` delle singole repo.

## Legenda

| Stato | Significato | Azione |
| --- | --- | --- |
| Verde | Nessun blocco noto; ultimo allineamento o gate rilevante completato | Monitorare al prossimo ciclo o intervenire solo su debito scelto |
| Attenzione | Nessun blocco immediato, ma c'è un rischio o una decisione da non dimenticare | Tenere in vista prima di cambiare codice, runtime o processo |
| Bloccato | C'è un impedimento operativo che blocca publish, deploy, release o uso previsto | Risolvere prima di nuove iniziative sulla repo |
| Non applicabile | La categoria non ha senso per quel progetto | Non forzare controlli o processi inutili |

## Sintesi

| Stato | Progetti | Motivo |
| --- | --- | --- |
| Verde | Atlas, Pratix, DocMolder, GLM, SyncBay | Allineamento completato e nessun blocco operativo noto nello snapshot Atlas |
| Attenzione | FiscalBay, SendChimp, TRAM, Sentinel | Esistono vincoli o osservazioni da rispettare prima del prossimo lavoro |
| Bloccato | Nessuno | Nessun blocco trasversale aperto dopo il consolidamento Sentinel |

## Matrice

| Progetto | Health | Ultimo segnale verificato | Rischio da tenere in vista | Prossimo controllo sensato |
| --- | --- | --- | --- | --- |
| Atlas | Verde | `main` pubblicato dopo la chiusura delle ondate e il consolidamento Sentinel | Non trasformare Atlas in runtime o dashboard applicativa | Aggiornare `docs/HEALTH.md` quando cambia stato di una repo |
| Pratix | Verde | PR `max23468/Pratix#156` mergiata, release patch `1.11.15`, Vercel production verificata con `publish:finish` | Repo già matura: non appesantire processi o UI; React Doctor dopo release minor | Scegliere solo debiti prodotto/tecnici reali con nuova conferma |
| DocMolder | Verde | PR `max23468/DocMolder#166` mergiata; publish docs-only completato senza release/deploy | Mantenere Release Please, VPS e policy repo-specifica; documenti utente sensibili | Prossimo intervento solo su debito reale o manutenzione GitHub/VPS |
| FiscalBay | Attenzione | PR `max23468/FiscalBay#78` mergiata; `ci_verify` e check GitHub passati | Upgrade Python misto: runtime VPS `3.13`, manifest/ruff/mypy/CI ancora `3.10` | Decidere upgrade Python solo aggiornando manifest, CI, toolchain e policy insieme |
| GLM | Verde | Primo allineamento Atlas completato con PR `max23468/Gare-Lotti-Milanesi#7` | Non perdere pattern maturi: simulatore, allegati Git LFS, runbook Cloudflare | Scegliere un debito reale: fonti pubbliche, import/export o ADR Cloudflare-only |
| SendChimp | Attenzione | PR `max23468/SendChimp#20` mergiata; Docs hygiene, Codex inbox e Vercel automatico passati | MVP manuale e vincolo free-tier; nessun invio reale o provider nuovo senza piano | Verificare capienza free-tier prima di cambiare provider, billing o invii |
| SyncBay | Verde | PR `max23468/SyncBay#27`, `#28`, `#29` mergiate; release locale `0.6.0`; Vercel automatico passato | No tag/GitHub Release/App Store production finché la policy non cambia | Scegliere un debito reale: keyset/OAuth eBay o import listing live |
| TRAM | Attenzione | PR `max23468/TRAM#6` e `#7` mergiate; React Doctor `100 / 100`, Quality, hygiene, PR title e Codex sync passati | Release/deploy policy non definita | Scegliere tra pilot Fase 7, policy release, provider/data policy o hardening T1/T2/T3 |
| Sentinel | Attenzione | PR `max23468/Sentinel#1` mergiata; workflow manuale `26369906474` verde; output commit `4b9d151` | Ortix ha 33 avvisi 404 ma 0 cambiamenti; retention output da valutare se cresce | Osservare il prossimo run schedulato e promuovere solo problemi reali da report/log |

## Regole di aggiornamento

- Aggiornare questa matrice dopo publish, merge, deploy, release o workflow
  operativo significativo.
- Non usare questa matrice per autorizzare modifiche automatiche alle repo:
  prima serve sempre conferma esplicita sul target.
- Se un dato dipende da provider, piani gratuiti, prezzi, API o limiti variabili,
  verificarlo live prima di trasformarlo in decisione.
- Se emerge un blocco reale, spostarlo anche in `docs/ROADMAP.md` o
  `docs/BACKLOG.md` secondo priorità.
- Tenere il dettaglio lungo in `docs/PROJECTS.md`; qui deve restare il colpo
  d'occhio operativo.

## Prossima revisione

- Dopo il prossimo intervento repo-specifico.
- Oppure al prossimo ciclo di manutenzione periodica Atlas.
