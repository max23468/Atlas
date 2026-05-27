# Backlog Atlas

Il backlog raccoglie possibilità, debiti, bug e idee non ancora promosse in roadmap.

Una voce nel backlog non è scope approvato.

## Idee operative

- Creare un template di report mensile Atlas per tutte le repo coordinate.
- Valutare se trasformare `docs/HEALTH.md` in report periodico o tenerlo come snapshot manuale.

## Backlog tecnico

- Valutare se affiancare alla issue `Codex feedback inbox`
  `#3` un handler/workflow Atlas, se serve davvero e se le Actions non sono più
  sospese.
- Valutare un controllo scriptabile per file canonici mancanti nelle repo coordinate.
- Valutare un controllo scriptabile per duplicati documentali e riferimenti a roadmap/backlog non canonici.
- Riattivazione workflow `Codex PR comments` verificata post-riavvio.
  su Pratix, DocMolder, FiscalBay, GLM, SendChimp, SyncBay, TRAM e Sentinel.
- Riattivazione del workflow runtime verificata post-riavvio.
  `Sentinel` o la scelta di un runtime alternativo.
- Riallineare Dependabot nelle repo dove oggi è sospeso, senza trattarlo come
  standard facoltativo.
- Valutare un upgrade Python completo di FiscalBay oltre `3.10` solo con decisione repo-specifica su manifest, CI, toolchain e policy.

## Documentazione

- Valutare se creare una guida breve "come usare subagent in Atlas".
- Aggiornare progressivamente eventuali riferimenti storici ancora residui che descrivono SendChimp come docs-only: oggi ha runtime Next.js e primo allineamento Atlas completato, ma resta senza invio automatico produttivo.

## Debiti

- Il piano principale è lungo e contiene sia decisioni sia azioni operative: va mantenuto leggibile prima di aggiungere nuovi livelli.
- Alcune decisioni fondative sono ancora nel piano principale e non ancora estratte in ADR autonome.
- Il piano principale contiene snapshot datati: prima di applicarlo a una repo, verificare sempre lo stato reale del checkout.
- Il primo giro GLM, TRAM, SyncBay e SendChimp ha mostrato che alcune repo hanno pattern più maturi del template minimo Atlas: usare `docs/STANDARD_CANDIDATES.md` prima di promuoverli o scartarli.
- I debiti prodotto delle repo coordinate possono essere censiti in Atlas, ma non sono scope operativo Atlas finché l'utente non indica repo target e attività esplicita.

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
