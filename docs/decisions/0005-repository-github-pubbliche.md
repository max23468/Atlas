# 0005 - Repository GitHub pubbliche nel perimetro Atlas

Data: 2026-05-31

Stato: Accettata

Supera: [0003 - Repository GitHub privata per Atlas](0003-repository-github-privata.md)

## Contesto

La verifica corrente via GitHub API indica che Atlas e le repo coordinate sono pubbliche. I documenti Atlas conservavano ancora riferimenti a repository private per Atlas, Sentinel e altri snapshot storici.

La visibilità pubblica è una scelta accettata dal maintainer. Atlas deve quindi documentare il fatto corrente invece di mantenere una policy privata non più vera.

## Decisione

Atlas e le repo coordinate nel perimetro corrente sono considerate repository GitHub pubbliche.

La repository remota canonica di Atlas resta `https://github.com/max23468/Atlas`.

La visibilità pubblica non cambia i vincoli su segreti, dati utente, documenti sensibili, provider, deploy, release o output applicativi: restano vietati segreti e dati sensibili nei repository.

## Alternative considerate

- Ripristinare la visibilità privata: respinta perché il maintainer ha confermato che le repo devono restare pubbliche.
- Lasciare i documenti invariati: respinta perché avrebbe mantenuto una contraddizione operativa.

## Impatti

- Prodotto: nessun cambio di perimetro prodotto.
- Tecnico: le policy GitHub e la documentazione devono riflettere repository pubbliche.
- Sicurezza/privacy: aumenta l'importanza di non committare segreti, dati utente reali, HTML completo non previsto o dettagli operativi sensibili.
- Deploy/release: non cambia i target e non abilita deploy o release.
- Documentazione: README, contesto, indice, toolchain, publish/deploy/release e registro progetti devono parlare di repository pubbliche.

## Conseguenze operative

- Non usare "repository privata" come assunzione nei piani Atlas.
- Prima di pubblicare contenuti nuovi, verificare che siano adatti a repository pubbliche.
- Continuare a separare visibilità GitHub pubblica da canali, webhook, segreti e deploy privati.

## Verifiche

- `gh api repos/max23468/<repo> --jq '.private'`
- `git diff --check`

## Collegamenti

- Decisione superata: `0003-repository-github-privata.md`
- Documenti collegati: `../../README.md`, `../../AGENTS.md`, `../CONTEXT.md`, `../TOOLCHAIN.md`, `../PUBLISH_DEPLOY_RELEASE.md`, `../PROJECTS.md`
