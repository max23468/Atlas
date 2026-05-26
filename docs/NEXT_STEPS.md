# Prossimi passi Atlas

Questo documento definisce come rispondere quando si chiede ad Atlas "e ora?",
"prossimi passi?" o formule equivalenti.

## Principio

Atlas non propone sviluppo prodotto delle repo coordinate come prossimo passo
predefinito.

Atlas può coordinare, verificare, classificare e pubblicare governance. Non deve
trasformare backlog, idee o debiti prodotto di Pratix, DocMolder, FiscalBay,
GLM, SendChimp, SyncBay, TRAM o Sentinel in attività operative salvo richiesta
esplicita sulla singola repo.

## Cosa può proporre Atlas

Quando il contesto non indica una repo target e uno scope applicativo esplicito,
Atlas può proporre solo attività Atlas-first:

- manutenzione governance e documentale;
- audit read-only di repo o gruppi di repo;
- controllo branch, PR, run, workflow e pubblicazioni residue;
- aggiornamento di `docs/PROJECTS.md`, `docs/HEALTH.md`, `docs/STANDARDS.md`,
  `docs/PUBLISH_DEPLOY_RELEASE.md` o `docs/STANDARD_CANDIDATES.md`;
- pulizia o chiarimento di policy, template, checklist e handoff;
- promozione, sospensione o parcheggio di pattern trasversali;
- preparazione di pacchetti di lavoro per repo, senza implementarli.

## Cosa non deve proporre Atlas

Atlas non deve proporre come prossimo passo generico:

- sviluppare nuove feature prodotto in una repo coordinata;
- hardening applicativo non richiesto;
- pilot, import, export, UI, provider, OAuth, deploy o dati live di una repo;
- refactor runtime;
- upgrade runtime o dipendenze come attività di prodotto;
- release o deploy di una repo non richiesti dal task corrente.

Questi lavori diventano ammessi solo se l'utente indica chiaramente la repo e lo
scope, oppure chiede esplicitamente ad Atlas di preparare una fase operativa su
quella repo.

## Debiti repo vs scope Atlas

Un debito di repo può comparire in Atlas in tre forme:

- **Osservazione**: informazione utile in `docs/PROJECTS.md` o `docs/HEALTH.md`;
- **Classificazione**: pattern da mantenere, promuovere, sospendere o scartare;
- **Pacchetto futuro**: lavoro descrivibile ma non ancora autorizzato.

Queste tre forme non autorizzano sviluppo prodotto.

Per passare da debito censito ad attività esecutiva servono:

- repo target esplicita;
- scopo operativo dichiarato;
- lettura dell'`AGENTS.md` locale;
- branch dedicata o worktree secondo policy;
- verifiche locali repo-specifiche;
- publish/deploy/release solo se richiesti e previsti dalla repo.

## Procedura quando viene chiesto "e ora?"

1. Controllare se la domanda riguarda Atlas o una repo specifica.
2. Se riguarda Atlas, proporre solo prossime azioni di governance,
   manutenzione, audit read-only, cleanup o documentazione.
3. Se emergono debiti repo, presentarli come opzioni da autorizzare, non come
   lavoro da iniziare.
4. Se la richiesta è ambigua, chiarire che Atlas può censire e preparare, ma non
   sviluppare prodotto senza target esplicito.
5. Se si procede su una repo, applicare `docs/APPLYING_ATLAS.md` e la policy di
   branch/worktree.

## Risposta attesa

Una risposta corretta di Atlas deve distinguere:

- cosa è lavoro Atlas;
- cosa è solo debito censito di una repo;
- cosa richiede autorizzazione separata;
- quali verifiche o cleanup sono possibili senza toccare prodotto.

Non deve chiudere con una proposta di sviluppo prodotto mascherata da prossimo
passo Atlas.
