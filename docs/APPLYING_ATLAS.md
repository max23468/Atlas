# Come applicare Atlas a una repo

Atlas non serve a continuare lo sviluppo prodotto delle repo coordinate. Serve a
rendere espliciti e coerenti governance, documentazione, GitHub, verifiche,
versioning, publish, deploy, release e handoff dove possibile.

Per scegliere cosa fare dopo un giro Atlas, usare anche
`docs/NEXT_STEPS.md`: i debiti prodotto delle repo coordinate non sono prossimi
passi Atlas finché non esistono repo target e scope operativo espliciti.

## Principio

Prima si capisce la repo, poi si applica Atlas.

Applicare Atlas non significa sviluppare la repo. Significa rendere leggibili e
coerenti governance, policy, verifiche, pubblicazione e handoff, preservando i
vincoli locali.

Non partire dai template. Partire da:

1. `AGENTS.md` della repo;
2. `git status --short --branch`;
3. branch dedicata o worktree separato se servono modifiche;
4. documenti canonici e runbook reali, verificati con `docs/SEMANTIC_CHECKLIST.md`;
5. workflow, test, script, release, deploy e policy esistenti;
6. Codex feedback inbox se la repo la usa;
7. vincoli su dati, provider, segreti e runtime.

## Isolamento Git

Per interventi Atlas su repo coordinate, non lavorare direttamente su
`main`/`master`.

Regola minima:

- discovery read-only: può avvenire sulla branch corrente se il checkout è pulito;
- qualunque modifica: creare prima una branch dedicata `codex/...`;
- lavoro lungo, repo non pulita, modifiche utente presenti o più repo in parallelo:
  usare un worktree separato;
- publish: pubblicare solo la branch prevista o il canale dichiarato dalla repo;
- chiusura: dichiarare branch, worktree, PR aperte e residui.

Il worktree è uno strumento di isolamento, non un rito obbligatorio. Diventa
obbligatorio quando evita di mischiare lavoro Atlas, modifiche dell'utente e
stato operativo della repo.

## Fase 1 - Discovery read-only

Raccogliere evidenza senza modificare:

- stack e runtime;
- package manager e lockfile;
- test/build/lint/typecheck/smoke;
- documenti governanti;
- source of truth decisionale;
- workflow GitHub e automazioni;
- deploy/release/versioning;
- dati sensibili e artefatti ignorati;
- pattern maturi non previsti da Atlas.

Output atteso: una classificazione, non una patch immediata.

## Fase 2 - Classificazione degli extra

Ogni elemento repo-specifico va classificato:

- **Mantenere specifico**: utile ma legato alla repo;
- **Promuovere**: maturo e trasferibile come standard Atlas;
- **Sostituire**: standard Atlas o altra repo hanno pattern migliore;
- **Parcheggiare**: utile ma non urgente;
- **Rimuovere**: duplicato o superato, solo dopo migrazione completa.

Questa fase previene la perdita di contenuti maturi e l'applicazione cieca dei
template.

## Fase 3 - Intervento minimo corretto

Applicare solo ciò che migliora davvero la governance:

- creare documenti canonici mancanti;
- rinominare o collegare documenti solo se non rompe convenzioni locali;
- separare decisioni stabili, decisioni pending e ADR puntuali con basename
  Markdown univoci;
- aggiungere PR template, issue template o PR title check se coerenti;
- aggiungere Codex inbox solo se ci sono review/PR ricorrenti;
- dichiarare versioning/release/deploy senza inventarli;
- registrare eccezioni motivate in Atlas.

Non introdurre:

- runtime;
- deploy;
- release automation;
- provider;
- billing;
- dati reali;
- workflow GitHub Actions non necessari.

Non proporre pilot, feature, import/export, UI, OAuth, hardening applicativo o
altro sviluppo prodotto come esito naturale dell'allineamento Atlas. Questi
lavori vanno solo censiti o impacchettati, salvo richiesta esplicita sulla repo.

## Fase 4 - Verifica

La verifica dipende dallo scope:

- docs-only: rilettura, `git diff --check`, link e coerenza documentale;
- workflow/GitHub: review YAML o parser locale, senza forzare Actions;
- runtime: test locali repo-specifici;
- React: React Doctor quando previsto;
- deploy: solo con target e runbook repo-specifici;
- sicurezza: controllo segreti, dump, export e file sensibili.


## Fase 5 - Pubblicazione

Seguire `docs/PUBLISH_DEPLOY_RELEASE.md` e la policy della repo:

- `pubblica`: porta il diff nel canale canonico;
- `rilascia`: crea versione solo se la repo ha policy;
- `deploya`: aggiorna runtime solo se esiste target approvato;
- `pubblica tutto`: publish più eventuale release/deploy solo dove davvero
  richiesti.

Quando una repo ha versioning o release reale, non lasciare come stato stabile un
solo changelog/versioning locale: la policy deve chiarire source of truth,
formato tag, GitHub Release, changelog e rapporto con deploy/runtime. Ogni
release prodotto reale deve creare sempre tag Git e GitHub Release nel formato
`vX.Y.Z`.

Quando la policy repo prevede una pubblicazione documentale rapida, usare commit
`[skip ci]` solo se la repo lo accetta e il diff è compatibile.

La pubblicazione deve restare proporzionata al diff:

- docs-only/governance-only: review documentale, `git diff --check`,
  coerenza/link e publish Git secondo policy repo;
- nessuno smoke test, deploy, release, App Store, VPS o gate runtime se il diff
  non cambia runtime, prodotto, configurazione operativa o documenti di deploy;
- branch/PR restano obbligatori dove la policy locale li richiede, ma non
  giustificano controlli runtime non pertinenti;
- le scorciatoie locali come `make publish-docs` non sono eccezioni isolate:
  vanno ricondotte a questo principio comune.

## Fase 6 - Handoff Atlas

Dopo l'intervento aggiornare Atlas:

- `docs/PROJECTS.md` per stato dettagliato;
- `docs/HEALTH.md` per colpo d'occhio operativo;
- `docs/STANDARDS.md` per stato degli standard;
- `docs/PUBLISH_DEPLOY_RELEASE.md` se cambia semantica publish/deploy/release;
- `docs/STANDARD_CANDIDATES.md` se emergono pattern trasferibili;
- `docs/BACKLOG.md` per debiti non promossi;
- `docs/CONTEXT.md` per lavori lunghi o cambi di stato.

## Criterio di uscita

Il lavoro è chiuso quando:

- lo scope richiesto è completato;
- non sono stati persi contenuti;
- non sono state applicate modifiche prodotto fuori richiesta;
- verifiche proporzionate sono state eseguite o dichiarate non applicabili;
- publish/deploy/release sono gestiti o esclusi con motivo;
- branch, PR e run non necessari sono puliti o dichiarati.
