# 0006 - CODEOWNERS non adottato come baseline

Data: 2026-05-31

Stato: Accettata

## Contesto

Nel perimetro Atlas le repository sono gestite in prevalenza da un maintainer singolo. Senza branch protection o ruleset che richiedano review da code owner, un file `CODEOWNERS` assegna ownership nominale ma non aggiunge controllo operativo reale.

La baseline GitHub condivisa ha già PR template, issue template, controlli di titolo PR, workflow proporzionati, `Codex feedback inbox`, squash merge only e cancellazione automatica dei branch dopo merge.

## Decisione

`CODEOWNERS` non fa parte della baseline Atlas.

Non introdurre nuovi file `CODEOWNERS` nelle repo coordinate e rimuoverli dove restano solo come ownership nominale. Una repo potrà reintrodurlo solo con decisione esplicita, motivando il controllo reale atteso e l'eventuale ruleset/branch protection collegato.

## Alternative considerate

- Mantenerlo ovunque: rifiutato perché crea burocrazia senza enforcement reale nel contesto attuale.
- Mantenerlo solo dove già presente: rifiutato perché lascerebbe una differenza non motivata tra repo single-maintainer.
- Reintrodurlo con ruleset obbligatori: rimandato a una decisione repo-specifica se emergerà un team o un rischio che lo richiede.

## Impatti

- Prodotto: nessun impatto runtime o utente.
- Tecnico: meno file di governance ridondanti.
- Dati/privacy: nessun impatto.
- Deploy/release: non applicabile.
- Documentazione: aggiornare i riferimenti a `CODEOWNERS` nelle repo interessate.

## Conseguenze operative

- La governance resta su branch dedicati, PR, template, controlli GitHub, inbox Codex e cleanup post-merge.
- Branch protection/ruleset restano decisioni separate e si applicano solo quando aggiungono controllo reale.
- Eventuali `CODEOWNERS` dentro dipendenze o vendor non sono policy della repo e non vanno toccati in questa decisione.

## Verifiche

- Ricerca `CODEOWNERS` nel perimetro repo escludendo dipendenze/vendor.
- Verifica GitHub delle impostazioni merge e branch cleanup quando rilevante.

## Collegamenti

- Piano: `piano-coordinamento-progetti.md`, sezione `10. GitHub`.
- Documenti collegati: `docs/DECISIONS.md`.
