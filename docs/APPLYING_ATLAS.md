# Come applicare Atlas a una repo

Atlas non serve a continuare lo sviluppo prodotto delle repo coordinate. Serve a
rendere espliciti e coerenti governance, documentazione, GitHub, verifiche,
versioning, publish, deploy, release e handoff dove possibile.

## Principio

Prima si capisce la repo, poi si applica Atlas.

Non partire dai template. Partire da:

1. `AGENTS.md` della repo;
2. `git status --short --branch`;
3. documenti canonici e runbook reali;
4. workflow, test, script, release, deploy e policy esistenti;
5. Codex feedback inbox se la repo la usa;
6. vincoli su dati, provider, segreti e runtime.

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

## Fase 4 - Verifica

La verifica dipende dallo scope:

- docs-only: rilettura, `git diff --check`, link e coerenza documentale;
- workflow/GitHub: review YAML o parser locale, senza forzare Actions;
- runtime: test locali repo-specifici;
- React: React Doctor quando previsto;
- deploy: solo con target e runbook repo-specifici;
- sicurezza: controllo segreti, dump, export e file sensibili.

Se GitHub Actions è senza budget, non usarle come gate e non creare workflow
schedulati nuovi.

## Fase 5 - Pubblicazione

Seguire `docs/PUBLISH_DEPLOY_RELEASE.md` e la policy della repo:

- `pubblica`: porta il diff nel canale canonico;
- `rilascia`: crea versione solo se la repo ha policy;
- `deploya`: aggiorna runtime solo se esiste target approvato;
- `pubblica tutto`: publish più eventuale release/deploy solo dove davvero
  richiesti.

Quando serve pubblicare senza Actions, usare commit `[skip ci]` solo se la repo
lo accetta e il diff è compatibile.

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
