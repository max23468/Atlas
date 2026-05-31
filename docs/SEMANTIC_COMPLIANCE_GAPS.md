# Checklist gap compliance semantica Atlas

Data: 2026-05-26.

Questa checklist raccoglie i problemi emersi dall'audit read-only del
`2026-05-26` su `origin/main`, documenti canonici, baseline GitHub e stato
remoto delle repo coordinate. Non valuta sviluppo prodotto e non usa come
segnale canonico working tree locali, branch locali o file sporchi temporanei.

## Scope

Sistemare solo governance e documentazione:

- contenuto dei documenti canonici;
- chiarezza delle source of truth;
- policy publish/release/deploy;
- handoff;
- eccezioni repo-specifiche;
- distinzione tra debiti repo e scope Atlas.

Fuori scope:

- feature prodotto;
- refactor runtime;
- deploy;
- release;
- workflow GitHub Actions nuovi o riattivati;
- cleanup di working tree locali.

Nota metodologica:

- per richiesta esplicita del maintainer, questo audit non usa come segnale
  canonico il checkout locale temporaneamente in lavorazione di SyncBay e TRAM;
- i failure o le code GitHub rilevate durante l'audit sono segnali operativi da
  registrare in Atlas, ma non autorizzano da soli modifiche prodotto sulle repo
  coordinate.

## Checklist

- [x] Definire una checklist semantica Atlas.
  - Verdetto: da riallineare.
  - Problema: Atlas oggi elenca bene i file canonici, ma non definisce ancora in
    modo verificabile cosa deve contenere ciascun documento.
  - Decisione applicata: creata `docs/SEMANTIC_CHECKLIST.md`, collegata da
    `docs/INDEX.md` e richiamata in `docs/STANDARDS.md` e
    `docs/APPLYING_ATLAS.md`.
  - Output atteso: una checklist che dica quali informazioni minime devono
    comparire in `AGENTS.md`, `docs/INDEX.md`, `docs/CONTEXT.md`,
    `docs/TOOLCHAIN.md`, `docs/ROADMAP.md`, `docs/BACKLOG.md` e decisioni.

- [x] Riallineare i basename Markdown duplicati.
  - Verdetto: da riallineare.
  - Repo interessate: Pratix, FiscalBay, GLM, SendChimp, SyncBay, Sentinel.
  - Problema: la decisione Atlas 0004 promuove a standard la regola "niente due
    file Markdown con lo stesso basename nella stessa repo".
  - Output atteso: migrare gli eventuali `docs/decisions/README.md` verso
    `docs/DECISIONS.md`, preservando contenuti e link.
  - Decisione applicata: nessuna repo coordinata conserva basename Markdown
    duplicati tra i file tracciati. I rinvii puri sono stati rimossi e gli
    indici storici sono stati migrati verso basename univoci.

- [x] Normalizzare il contenuto dei `docs/CONTEXT.md` non template-style.
  - Verdetto: da riallineare.
  - Repo interessate: Pratix, DocMolder, FiscalBay, SendChimp, SyncBay, TRAM.
  - Problema: i documenti sono utili e spesso molto maturi, ma non espongono
    sempre in modo uniforme stato progetto, release corrente, deploy corrente,
    fonti primarie, vincoli, rischi aperti, handoff e prossimo controllo.
  - Output atteso: mantenere il contenuto utile esistente, aggiungendo sezioni o
    rinvii espliciti senza perdere informazioni.
  - Decisione applicata: aggiunti stato, source of truth, release/deploy,
    pubblicazione proporzionata, eccezioni o handoff dove mancavano.

- [x] Rendere più esplicito negli indici il rapporto con root docs e `AGENTS.md`.
  - Verdetto: da riallineare.
  - Repo interessate: soprattutto FiscalBay e SendChimp.
  - Problema: gli indici sono ricchi, ma non sempre dichiarano chiaramente
    `AGENTS.md`, `README.md` e i documenti root come ingresso operativo primario.
  - Output atteso: ogni `docs/INDEX.md` deve indicare l'ingresso operativo e
    distinguere documenti root, docs canonici, guide operative e decisioni.
  - Decisione applicata: FiscalBay e SendChimp ora indicano esplicitamente
    ingresso operativo root e registri decisionali; gli altri indici sono già
    conformi o sono stati aggiornati per i nuovi nomi.

- [x] Uniformare la frase "il backlog non è scope approvato".
  - Verdetto: da riallineare.
  - Repo interessate: soprattutto SendChimp; verificare anche le altre durante
    la normalizzazione.
  - Problema: alcune repo comunicano il concetto in modo implicito o con wording
    diverso.
  - Output atteso: in ogni `docs/BACKLOG.md` deve essere chiaro che una voce nel
    backlog non autorizza implementazione, release o deploy.
  - Decisione applicata: tutte le repo coordinate contengono la frase
    `Una voce nel backlog non è scope approvato.`

- [x] Marcare sempre le eccezioni motivate come tali.
  - Verdetto: da riallineare.
  - Repo interessate: TRAM, DocMolder, GLM, Sentinel.
  - Problema: alcune eccezioni sono corrette ma deducibili, non sempre etichettate
    come `OK equivalente`, `repo-specifico`, `sospeso` o `N/A`.
  - Output atteso: le eccezioni devono essere leggibili senza dover ricostruire
    il contesto storico.
  - Decisione applicata: GLM, DocMolder, FiscalBay, TRAM e Sentinel marcano le
    eccezioni nei rispettivi context o registri pending.

- [x] Riallineare FiscalBay alla baseline Python `3.13`.
  - Repo interessata: FiscalBay.
  - Verdetto: gap chiuso.
  - Problema precedente: manifest/CI e runtime VPS erano descritti come stato
    misto tra Python `3.10` e `3.13`.
  - Decisione aggiornata: Python `3.13` è baseline unica per manifest,
    lint/typecheck, CI, package build e VPS.
  - Output atteso: non abbassare il supporto a minor version precedenti senza
    decisione esplicita e aggiornamento coerente della policy.

- [x] Riallineare Atlas alla Codex feedback inbox.
  - Repo interessata: Atlas.
  - Problema: Atlas è oggi trattato come `N/A` o `sospeso` per la Codex feedback
    inbox, ma la decisione è riallinearlo alla baseline comune invece di
    mantenerlo come eccezione.
  - Decisione: Atlas deve avere una Codex feedback inbox propria come le repo
    operative coordinate.
- Vincolo: workflow e riattivazioni erano stati vincolati dalla finestra
  temporanea, poi riavviati dopo verifica locale e remota.
- Decisione applicata: Atlas usa la issue GitHub `#10` `Codex feedback inbox`
  come baseline; i workflow sono ora riavviati e verificati nel ciclo post-riavvio.
  - Output atteso: creare o documentare issue inbox, handler/workflow coerente
    con la baseline Atlas, controllo prima di publish/merge e stato esplicito in
    `docs/STANDARDS.md`, `docs/TOOLCHAIN.md` e documenti collegati.

- [x] Riallineare Dependabot dove oggi è sospeso.
  - Repo interessate: GLM, Sentinel e, come stato remoto da monitorare,
    DocMolder, Pratix, FiscalBay, SendChimp, SyncBay e TRAM.
- Decisione: Dependabot resta standard Atlas pieno in tutte le repo con
    dipendenze, manifest compatibili o workflow GitHub Actions. La sospensione globale non cambia lo
    standard e non impedisce la riattivazione verificata dove previsto.
  - Evidenza aggiornata audit `2026-05-26`: GLM e Sentinel risultano ancora
    senza `dependabot.yml`; in parallelo GitHub mostra ancora run
    `Dependabot Updates` cancelled su altre repo, quindi la sospensione Atlas
    non va descritta come freeze totale dello stato remoto.
  - Output atteso: verificare repo per repo se Dependabot è attivo, se manca
    configurazione o se richiede allineamento, senza trattarlo come pattern
    facoltativo.
  - Decisione applicata: aggiunti `dependabot.yml` a GLM e Sentinel. Le altre
    repo compatibili lo avevano già; la sospensione Actions non declassa lo
    standard.

- [x] Riallineare SyncBay a un flusso release più standard.
  - Repo interessata: SyncBay.
  - Problema: SyncBay oggi dichiara versioning locale `0.x`, niente tag Git,
    niente GitHub Release e niente App Store production; Vercel automatico è
    presente ma resta distinto dalla release prodotto.
  - Decisione: non trattare più questa configurazione come eccezione stabile da
    preservare; va riallineata a un flusso release più standard.
  - Output atteso: valutare e implementare in un intervento dedicato una policy
    coerente per tag, GitHub Release, changelog/source of truth versione e
    rapporto con Vercel/App Store production, senza confondere deploy hosting e
    rilascio prodotto.
  - Decisione applicata: ADR SyncBay `0008-tag-e-github-release.md`,
    `docs/CONTEXT.md`, `docs/DECISIONS_PENDING.md` e la guida versioning
    dichiarano che tag/GitHub Release sono obbligatori per release prodotto reale,
    mentre App Store production resta decisione separata dal deploy Vercel.

- [x] Riallineare DocMolder a una pubblicazione proporzionata standard Atlas.
  - Repo interessata: DocMolder.
  - Problema: `make publish-docs` è oggi una scorciatoia locale DocMolder per
    cambi minuscoli solo documentali da `main`, con preflight mirato e senza PR,
    release o deploy. Non va mantenuta come eccezione isolata.
  - Decisione: il principio corretto diventa standard Atlas per tutte le repo:
    la pubblicazione deve essere proporzionata al diff.
  - Caso base da applicare: cambi solo documentali o di governance non devono
    attivare smoke test, deploy, release, App Store, VPS o controlli runtime non
    pertinenti; richiedono invece review documentale, `git diff --check`,
    controlli link/coerenza e pubblicazione nel canale Git coerente con la repo.
  - Output atteso: ogni repo deve dichiarare una modalità docs-only/governance-only
    proporzionata, mantenendo branch/PR quando richiesto dalla policy locale ma
    senza imporre gate runtime o deploy inutili.
  - Decisione applicata: il principio è esplicitato in
    `docs/SEMANTIC_CHECKLIST.md`, `docs/APPLYING_ATLAS.md` e nei context/policy
    delle repo riallineate.

- [x] Definire in futuro un target deploy per TRAM.
  - Repo interessata: TRAM.
  - Verdetto: eccezione motivata ma temporanea.
  - Problema: TRAM è una web app Next.js/React e ha policy SemVer/release, ma
    non ha ancora un target deploy approvato; quindi oggi release e deploy
    restano separati e non va inventato un deploy.
  - Decisione: confermare l'assenza di deploy come stato corretto attuale, ma
    non trattarla come eccezione permanente. Prima o poi TRAM dovrà avere target,
    comando, ambiente, runbook e verifica post-deploy dichiarati.
  - Output atteso: mantenere "nessun deploy" finché manca decisione esplicita;
    aprire un intervento dedicato quando sarà il momento di definire deploy,
    senza confonderlo con release SemVer o publish GitHub.
  - Decisione applicata: `docs/CONTEXT.md` e `docs/DECISIONS_PENDING.md`
    marcano il target deploy come decisione futura, senza inventare deploy ora.

- [x] Promuovere il modello decisionale completo a standard pieno.
  - Repo interessate: tutte le repo coordinate.
  - Decisione: ogni repo deve distinguere registro decisionale stabile,
    decisioni pending e ADR puntuali.
  - Caso base: `docs/DECISIONS.md` come registro/indice delle decisioni stabili,
    `docs/DECISIONS_PENDING.md` o equivalente con basename univoco per decisioni
    non ancora approvate, `docs/decisions/NNNN-slug.md` per ADR puntuali.
  - Vincolo: non creare `docs/decisions/README.md` e non duplicare basename
    Markdown; migrare o collegare contenuti storici senza perdita.
  - Output atteso: aggiornare Atlas e poi riallineare repo per repo dove pending,
    registro stabile o ADR puntuali sono assenti, ambigui o nominati in modo non
    conforme.
  - Decisione applicata: tutte le repo coordinate hanno `docs/DECISIONS.md`,
    `docs/DECISIONS_PENDING.md` e ADR puntuali in `docs/decisions/`, senza
    `docs/decisions/README.md`.

- [x] Riallineare changelog/versioning locale verso tag e GitHub Release.
  - Repo interessate: GLM, SendChimp, SyncBay e ogni repo con versioning reale.
  - Problema: alcune repo hanno changelog o versione locale senza tag Git e
    senza GitHub Release; questo può essere transitorio, ma non deve restare
    pattern stabile quando esiste una release reale.
  - Decisione: il changelog frontend/locale senza tag o GitHub Release va
    riallineato. Dove una repo dichiara una release prodotto reale, deve creare
    sempre tag Git e GitHub Release `vX.Y.Z`, definendo source of truth,
    changelog e rapporto con deploy/runtime.
  - Output atteso: valutare repo per repo una policy release completa,
    distinguendo release prodotto, deploy hosting, App Store o runtime live; non
    creare tag/GitHub Release retroattivi senza una decisione di migrazione.
  - Decisione applicata: Atlas richiede tag Git e GitHub Release `vX.Y.Z` per
    ogni release prodotto reale. Nessun tag retroattivo creato; Sentinel limita
    l'obbligo a release tool/dashboard, non a scan/report.

- [x] Riallineare i `docs/CONTEXT.md` che dichiarano una versione statica non aggiornata.
  - Repo interessata: GLM.
  - Verdetto: da riallineare.
  - Problema: in GLM il `docs/CONTEXT.md` dichiara versione applicativa `1.1.1`,
    mentre la source of truth reale `package.json` dichiara `1.6.0`.
  - Decisione: non è una discrepanza tra nome prodotto, repository, slug deploy
    e URL runtime; quel mapping in GLM è già coerente e dichiarato. Il gap reale
    è il drift documentale tra contesto operativo e source of truth della
    versione.
  - Output atteso: aggiornare `docs/CONTEXT.md` nella repo interessata e
    valutare in Atlas se i `docs/CONTEXT.md` debbano riportare una versione
    statica solo quando esiste un meccanismo affidabile di mantenimento.
  - Decisione applicata: GLM ora rimanda a `package.json` come source of truth
    della versione invece di riportare una versione statica soggetta a drift.

- [x] Preservare GLM come eccezione repo-specifica per Cloudflare Pages e Git LFS.
  - Repo interessata: GLM.
  - Verdetto: eccezione motivata confermata, non gap da riallineare.
  - Evidenza: `AGENTS.md` dichiara GLM come app React/Vite con deploy
    Cloudflare Pages, non Vercel/Supabase; `docs/guides/cloudflare-pages.md`
    dichiara progetto Pages `gare-lotti-milanesi`, produzione
    `https://gare-lotti-milanesi.pages.dev` e deploy produzione solo tramite
    `npm run deploy:cloudflare` su richiesta esplicita; `.gitattributes`
    mette `docs/milano-lotti-extraurbani-om/**` sotto Git LFS.
  - Decisione confermata: non riallineare GLM a Vercel, Supabase o ad altri provider
    standardizzati; non rimuovere Git LFS e non trattare gli allegati gara come
    cache o file temporanei.
  - Output atteso: marcare in Atlas GLM come `repo-specifico` per deploy
    Cloudflare Pages e allegati gara LFS; eventuali interventi futuri devono
    preservare runbook Cloudflare, `.gitattributes`, path degli allegati e regole
    di non modifica degli allegati salvo richiesta esplicita.

- [x] Non trattare GLM come eccezione per la separazione tra nome prodotto e URL runtime.
  - Repo interessata: GLM.
  - Verdetto: nessuna discrepanza reale.
  - Evidenza: GLM dichiara esplicitamente nome prodotto visibile `Simulatore
    gara TPL lotti 1-4`, repository `GLM` (GitHub), progetto/slug deploy
    `gare-lotti-milanesi` e URL pubblico
    `https://gare-lotti-milanesi.pages.dev`.
  - Decisione confermata: non aprire un riallineamento su questo punto; la
    separazione è intenzionale, coerente e già documentata.

- [x] Chiarire che "OK equivalente" non significa formato identico.
  - Repo interessate: tutte, via Atlas.
  - Problema: la matrice `docs/STANDARDS.md` usa spesso `OK`, ma non distingue
    abbastanza tra compliance semantica, uniformità formale e sospensione
    temporanea.
  - Decisione applicata: `docs/STANDARDS.md` ora distingue `OK pieno`,
    `OK equivalente`, `Da riallineare`, `Sospeso` e `N/A`, chiarendo che
    `OK equivalente` non implica formato identico.

- [x] Aggiornare `docs/STANDARDS.md` con i gap semantici.
  - Problema: la matrice standard era troppo sintetica per dimostrare la
    compliance di contenuto.
  - Decisione applicata: `docs/STANDARDS.md` ora distingue meglio `OK pieno`,
    `OK equivalente`, `Da riallineare`, `Sospeso` e `N/A`, e riporta anche i
    drift correnti emersi dall'audit GitHub del `2026-05-26`.

- [x] Aggiornare `docs/HEALTH.md` senza trasformare questi gap in blocchi.
  - Problema: i gap sono debiti di governance leggera, non blocchi operativi.
  - Decisione applicata: `docs/HEALTH.md` ora dichiara esplicitamente che i gap
    semantici Atlas restano in `docs/SEMANTIC_COMPLIANCE_GAPS.md` e incidono
    sulla health solo se diventano rischio operativo reale.

- [x] Aggiornare `docs/PROJECTS.md` solo come registro, non come autorizzazione.
  - Problema: le prossime azioni repo-specifiche potevano essere lette come
    lavoro prodotto se non formulate con cautela.
  - Decisione applicata: `docs/PROJECTS.md` ora usa wording da registro
    operativo, segnala gli ultimi segnali GitHub verificati e mantiene le
    prossime azioni nel perimetro `audit read-only` o `solo con scope esplicito`.

- [x] Non toccare codice prodotto.
  - Verdetto: da riallineare.
  - Problema: questi gap riguardano compliance Atlas, non implementazioni nelle
    app o bot.
  - Output atteso: eventuali PR repo-per-repo devono essere docs/governance-only,
    su branch dedicata, con `[skip ci]` se compatibile e senza deploy/release.
  - Decisione applicata: gli interventi repo-per-repo sono limitati a
    documentazione/governance e `dependabot.yml` dove mancava; niente codice
    prodotto, deploy o release.

## Eccezioni note da preservare

- TRAM: `docs/DECISIONS.md` e basename Markdown univoci sono il nuovo caso base;
  non creare `docs/decisions/README.md`. L'assenza di target deploy è
  eccezione motivata ma temporanea: non inventare deploy ora, ma prevedere una
  decisione deploy futura.
- DocMolder: PR title validato nella policy/CI locale è equivalente accettato.
- FiscalBay: Python `3.13` è baseline unica; preservare invece le eccezioni
  repo-specifiche su dati fiscali eBay, VPS corretta e deploy/release via script
  locali fuori da GitHub Actions.
- GLM: Cloudflare Pages e Git LFS/allegati gara sono eccezioni motivate da
  preservare; non riallineare a Vercel/Supabase e non trattare gli allegati come
  cache.
- Sentinel: eccezione confermata. GitHub Actions resta runtime operativo MVP,
  `data/`, `snapshots/` e `reports/` restano output applicativi committabili,
  e il workflow runtime `Sentinel` è stato riavviato e verificato.
- Atlas: la Codex inbox non è più eccezione `N/A`; va riallineata alla baseline
  comune e i workflow sono ora disponibili dopo il riavvio del `2026-05-27`.

## Criterio di completamento

La checklist è chiusa quando:

- ogni repo ha documenti canonici semanticamente verificabili;
- le eccezioni sono marcate come equivalenti, sospese, N/A o repo-specifiche;
- Atlas distingue compliance semantica e uniformità formale;
- nessun documento trasforma debiti prodotto in scope Atlas;
- nessun codice prodotto, deploy o release è stato toccato per chiudere questi
  gap.
