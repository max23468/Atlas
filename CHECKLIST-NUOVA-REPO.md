# Checklist nuova repo Atlas

Questa checklist serve quando una nuova repository entra nel perimetro Atlas.
Non applicare template in modo meccanico: prima leggere la repo reale, poi
decidere cosa mantenere, promuovere, adattare o lasciare fuori.

## Prima lettura

- Controllare `git status --short --branch`.
- Leggere l'eventuale `AGENTS.md`.
- Leggere `README.md`, documenti in `docs/`, guide operative e workflow.
- Verificare remote, branch principale e repository GitHub.
- Censire runtime, package manager, lockfile, framework, provider e ambienti.
- Censire test, build, lint, typecheck, smoke, deploy, release e runbook.
- Censire issue/PR operative, Codex feedback inbox e review thread se presenti.
- Censire dati sensibili, file ignorati, fixture, export, cache e artefatti
  generati.

## Isolamento lavoro

- Fare discovery read-only prima di cambiare file.
- Prima di qualunque modifica creare una branch dedicata `codex/...`, salvo
  regola repo-specifica più restrittiva.
- Usare un worktree separato se il checkout non è pulito, se ci sono modifiche
  dell'utente, se l'intervento durerà più turni o se Atlas sta lavorando su più
  repo nello stesso ciclo.
- Non lasciare lavoro Atlas mischiato su `main`/`master`.
- Dichiarare in chiusura branch, worktree e PR residue.

## Classificazione Atlas

Per ogni elemento già presente nella repo decidere una sola categoria:

- mantenere specifico: è maturo ma non generalizzabile;
- promuovere a standard Atlas: è utile e trasferibile ad altre repo;
- sostituire con pattern più maturo: esiste già uno standard migliore;
- parcheggiare in backlog: utile ma non urgente o non deciso;
- rimuovere solo se duplicato o superato e assorbito senza perdita.

Non rimuovere contenuti prima di avere migrato o collegato tutte le informazioni
utili.

## Baseline documentale

Verificare o creare, adattandoli alla repo:

- `AGENTS.md`;
- `README.md`;
- `docs/INDEX.md`;
- `docs/ROADMAP.md`;
- `docs/BACKLOG.md`;
- `docs/CONTEXT.md`;
- `docs/TOOLCHAIN.md`;
- `docs/decisions/` o registro decisionale equivalente.

Eccezioni ammesse:

- non creare documenti doppi con stesso titolo o scopo;
- rispettare regole locali come basename Markdown univoci;
- mantenere registri storici maturi se sono la source of truth reale.

## GitHub

- PR template presente o motivatamente non applicabile.
- Issue template minima presente o motivatamente non applicabile.
- PR title check presente o equivalente nella policy locale.
- Codex feedback inbox presente solo dove ci sono PR operative ricorrenti o
  review thread da gestire.
- Dependabot presente solo dove ci sono dipendenze runtime reali e budget/rumore
  sostenibili.
- Workflow GitHub Actions compatibili con budget, policy e ruolo della repo.

Se i minuti GitHub Actions sono esauriti, non attivare nuovi workflow schedulati
e non usare Actions come gate.

## Versioning, release e deploy

- Dichiarare cosa significa `pubblica`.
- Dichiarare se esiste una release versionata e quale file contiene la versione.
- Dichiarare se esiste deploy, target, comando, ambiente e verifica post-deploy.
- Separare sempre publish, release e deploy.
- Non introdurre tag, GitHub Release, Release Please, deploy o runtime esterni se
  la repo non li ha decisi.
- Aggiornare `docs/PUBLISH_DEPLOY_RELEASE.md` in Atlas se la repo entra nel
  perimetro coordinato.

## Verifiche

- Per docs-only: rilettura, `git diff --check`, link/coerenza documentale e
  controllo `.DS_Store`.
- Per codice runtime: test locali repo-specifici.
- Per React: React Doctor dopo release minor o modifiche React trasversali.
- Per deploy: verifiche post-deploy dichiarate dal runbook della repo.
- Per dati sensibili: controllare che segreti, dump, export, pacchetti reali o
  file personali non entrino in Git.

## Handoff Atlas

Aggiornare in Atlas:

- `docs/PROJECTS.md`;
- `docs/HEALTH.md`;
- `docs/STANDARDS.md`;
- `docs/PUBLISH_DEPLOY_RELEASE.md`;
- `docs/STANDARD_CANDIDATES.md` se emergono pattern maturi;
- `docs/CONTEXT.md` dopo interventi lunghi o cambi di stato.

## Chiusura

- Working tree pulito o modifiche residue dichiarate.
- Branch locali/remoti non necessari rimossi.
- PR aperte solo se intenzionali.
- Publish/deploy/release eseguiti o dichiarati fuori scope.
- Rischi residui e prossimo passo operativo espliciti.
