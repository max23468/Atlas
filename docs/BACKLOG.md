# Backlog Atlas

Il backlog raccoglie possibilità, debiti, bug e idee non ancora promosse in roadmap.

Una voce nel backlog non è scope approvato.

## Idee operative

- Creare una checklist rapida "nuova repo" derivata dalla baseline del piano.
- Creare un template di report mensile Atlas per tutte le repo coordinate.
- Evolvere `docs/PROJECTS.md` in una matrice health periodica, se serve oltre al registro operativo.
- Valutare una vista sintetica per distinguere publish, deploy e release repo per repo.
- Valutare quali pattern GLM/TRAM/SyncBay/SendChimp meritano una regola Atlas: documento di logica/modello, changelog frontend, runbook deploy molto concreto, separazione nome prodotto/URL tecnico, basename Markdown univoci, decision register separato dagli ADR puntuali, rinvii compatibili dopo migrazione dei documenti canonici.

## Backlog tecnico

- Valutare se creare una Codex feedback inbox per Atlas quando iniziano PR o commenti operativi ricorrenti.
- Valutare un controllo scriptabile per file canonici mancanti nelle repo coordinate.
- Valutare un controllo scriptabile per duplicati documentali e riferimenti a roadmap/backlog non canonici.
- Valutare una Codex feedback inbox per Sentinel solo se iniziano review o commenti PR ricorrenti.
- Riconciliare FiscalBay: runtime VPS Python `3.13` documentato, ma manifest/CI ancora su Python `3.10`.

## Documentazione

- Valutare se creare una guida breve "come applicare Atlas a una repo", includendo discovery repo-specifica e classificazione degli extra.
- Valutare se creare una guida breve "come usare subagent in Atlas".
- Aggiornare progressivamente eventuali riferimenti storici ancora residui che descrivono SendChimp come docs-only: oggi ha runtime Next.js e primo allineamento Atlas completato, ma resta senza invio automatico produttivo.

## Debiti

- Il piano principale è lungo e contiene sia decisioni sia azioni operative: va mantenuto leggibile prima di aggiungere nuovi livelli.
- Alcune decisioni fondative sono ancora nel piano principale e non ancora estratte in ADR autonome.
- Il piano principale contiene snapshot datati: prima di applicarlo a una repo, verificare sempre lo stato reale del checkout.
- Il primo giro GLM, TRAM, SyncBay e SendChimp ha mostrato che alcune repo hanno pattern più maturi del template minimo Atlas: non vanno persi né trasformati subito in standard.

## Decisioni sospese

- Estrarre altre ADR fondative subito o lasciarle nel piano finché non servono.
- Definire se Atlas avrà una manutenzione mensile autonoma oltre alla manutenzione delle repo coordinate.

## Attività operative ricorrenti

- Rileggere `piano-coordinamento-progetti.md` prima di applicare il piano a una repo.
- Aggiornare `docs/ROADMAP.md` quando cambia la priorità trasversale.
- Aggiornare `docs/BACKLOG.md` quando emergono idee o debiti non ancora promossi.
- Aggiornare `docs/CONTEXT.md` dopo passaggi lunghi o cambi di stato.
- Verificare che i template restino coerenti con le decisioni approvate.

## Regole

- Quando una voce diventa prioritaria, promuoverla in `docs/ROADMAP.md`.
- Quando una voce diventa decisione stabile, collegarla o spostarla in `docs/decisions/`.
- Non usare il backlog come storico dei lavori completati.
