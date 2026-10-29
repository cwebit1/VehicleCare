# VehicleCare — Changelog

---

## v111 — 2026-10-29
### Gomme: modifica dei set montati e in deposito
- **Toccando un set gomme** nelle sezioni "Montate" o "In deposito" si apre la maschera di modifica di quel set (nessun pulsante in più; l'etichetta mostra ✏️)
- Campi modificabili: stagione (estive, invernali, 4 stagioni), marca, modello, dimensione, quantità, data e km di montaggio, data e km di smontaggio (solo set in deposito), km percorsi nei montaggi precedenti, note. Si salvano solo i campi cambiati
- Controlli: marca obbligatoria, km non negativi, smontaggio non precedente al montaggio (date e km)
- **Elimina set** con conferma, per i set registrati per errore
- Montaggio e smontaggio restano affidati al cambio gomme
- Icona 🌦️ e dicitura "4 stagioni" per i set 4 stagioni
- In-app 1.1.12

---

## v110 — 2026-10-27
### Documenti mezzi: visualizzatore funzionante su telefono
- **Visualizzatore immagini**: su telefono e tablet i pulsanti Ruota, Zoom, Reset, Salva e Chiudi non rispondevano al tocco e il visualizzatore a tutto schermo non si chiudeva più, bloccando l'app. Ora i tocchi sui pulsanti funzionano; pizzico e trascinamento sull'immagine invariati
- Chiudendo il visualizzatore si rimuovono anche i suoi ascoltatori del mouse (prima si accumulavano a ogni apertura)
- **PDF**: la finestra si apre subito al tocco, così il browser mobile non la blocca più; se viene comunque bloccata il PDF si apre tramite link invece di andare in errore
- In-app 1.1.11

---

## v109 — 2026-10-22
### Maschere: km proposti, crea/modifica separati, gomme
- **Km proposti in grigio** (campo vuoto, valore suggerito): apertura intervento = km dell'ultimo check, chiusura = km di apertura; se non si scrive nulla vale il proposto. Vale per tutte le maschere di creazione intervento, chiusura, segnalazione, revisione, risolvi anomalia, prima registrazione gomme e cambio gomme. Nel nuovo check i km in grigio sono solo un promemoria: vanno scritti
- Scheda mezzo: i km si aggiornano solo se più alti; l'ultimo check solo se il check è il più recente
- Controlli su tutte le maschere che creano o chiudono interventi: data chiusura non precedente all'apertura, programmazione non successiva all'intervento, km chiusura non inferiori ai km apertura; revisione: nuova scadenza successiva alla data
- **Check: maschere Crea/Modifica separate**. La modifica mostra il check com'è stato registrato (voci, ordine, NON PRESENTE di allora — comprese "Freni" e "Pressione pneumatici") e salva solo i campi cambiati
- **Gomme**: in modifica cambio gomme il veicolo non è più modificabile e si salvano solo i campi cambiati (prima cambiare veicolo svuotava i dati delle gomme); km di vita dei set cumulativi tra una stagione e l'altra; gomme 4 stagioni considerate in regola tutto l'anno
- Pulsanti "+ Intervento" e "Risolto" delle anomalie funzionanti con note che contengono a capo, virgolette o apostrofi
- **Veicolo e Fornitore: maschere Crea/Modifica separate**; targa duplicata bloccata; km del veicolo salvati come numero; il tipo fornitore non in elenco (es. "Centro revisioni") non viene più cambiato in modifica
- In-app 1.1.10

---

## v108 — 2026-10-22
### Interventi: maschere separate per Crea e Modifica
- **Crea** e **Modifica** intervento sono ora due maschere distinte (prima un'unica maschera per entrambe)
- Modifica: mostra il record com'è (campi vuoti restano vuoti) e salva **solo i campi cambiati**; non riscrive più origine, non aggiunge data programmazione né km, non perde il fornitore se non attivo (mostrato come "non attivo"), non aggiunge collegamenti a check da creazioni abbandonate
- Riepilogo origine (check/segnalazione/revisione/manuale) e data di creazione in testa alla modifica
- Controlli su entrambe: data intervento obbligatoria, programmazione non successiva all'intervento, chiusura non precedente all'apertura, km chiusura non inferiori ai km apertura
- Campi di chiusura solo con stato "Chiuso"; riaprendo un intervento chiuso compare l'avviso che i dati di chiusura verranno rimossi
- In-app 1.1.09

---

## v107 — 2026-10-22
### Avviso cambio gomme secondo il Codice della Strada
- Le date in Impostazioni sono ora le **scadenze**: invernali entro il **15/11**, estive entro il **15/05** (prima 15/10 e 15/04, che sono inizio finestra e fine obbligo)
- Nuovo campo **Preavviso cambio gomme (giorni)**, default 30 (prima 14 fissi nel codice)
- Avviso per mezzo: conta i mezzi attivi con montate le gomme dell'altra stagione e indica quanti hanno già un cambio programmato; dopo la scadenza il chip diventa rosso finché il cambio non è registrato
- In-app 1.1.08

---

## v106 — 2026-10-22
### Revisione integrità cloud + correzioni (roadmap del 22/10)
- **DB Editor compatibile con il cloud**: ogni modifica/aggiunta/eliminazione fatta in `vcp-db-editor.html` viene accodata e inviata al cloud dall'app (alla riapertura, o subito se l'app è aperta in un'altra scheda); documenti modificati e foto sostituite arrivano a tutti i dispositivi
- **Azzera tutti i dati**: se collegato al cloud, copia di sicurezza automatica e cancellazione su tutti i dispositivi (prima i dati ricomparivano alla riapertura)
- **Ripristina da ZIP**: copia di sicurezza automatica, poi sostituzione completa anche nel cloud; i documenti assenti dallo ZIP vengono eliminati ovunque (un backup senza documenti non li cancella)
- Fix: nel ripristino da copia/ZIP le impostazioni non arrivavano al cloud
- Fix: foto veicolo sostituita non arrivava agli altri dispositivi; foto scaricata dal cloud non viene più ricaricata come doppione
- Fix: voce check "Lavavetri posteriori" controllata su `lavavetriPost` (prima su `spazzolePost`)
- Fix: il Cronologico mostra i cambi gomme chiusi (stato `completato`, prima cercava `eseguito`)
- Rimossa `vehiclecare-pro (71).html` (versione obsoleta ancora pubblicata, incompatibile col database attuale)
- In-app 1.1.07

---

## v105 — 2026-10-22 `a94acf8`
- Copia di sicurezza automatica settimanale nel cloud (conservazione 30 giorni, ripristino da Impostazioni → Cloud con copia preventiva dello stato attuale). File eliminati conservati 30 giorni. In-app 1.1.06.

---

## v104 — 2026-10-22 `55ebe91`
- Sincronizzazione cloud Firebase: copia principale di dati, foto e documenti su Firestore (login Google, ripristino automatico dopo pulizia cache, coda offline). Sezione Cloud in Impostazioni. In-app 1.1.05.

---

## v103 — 2026-07-02 `3ff55ac`
- Fix planner: i giorni di coda del mese prec./succ. mostrano data reale, check ed eventi; range eventi esteso all intera griglia visibile (aggancio per data reale in _pushDateRangeSegments). In-app 1.1.04.

---

## v102 — 2026-06-29 `6d02e96`
- Backup completo: include segnalazioni (export+import+conteggio conferma) e calibration (vcp_calibration) in export e ripristino. In-app 1.1.03.

---

## v101 — 2026-06-29 `195427a`
- Fix pulsante Documenti: getByVehicle con fallback se manca indice vehicleId; openDocuments mostra errore invece di fallire muto; richiesta storage persistente per evitare sfratto IndexedDB (foto/documenti). In-app 1.1.02.

---

## v100 — 2026-06-29 `36d29e3`
- Nuova voce menu Stampa check: selettore mese + lista check del mese (checkbox, targa, data, pallino anomalie), PDF multipagina Apri/Stampa. Rendering modulo estratto in _drawCheckCanvas e riusato. Versione in-app 1.1.01.

---

## v99 — 2026-06-29 `ec5f5d6`
- Fix stampa su mobile: il pulsante Stampa inietta il modulo nel print-frame e apre la finestra di stampa di sistema (window.print), invece dellautoPrint del PDF che Chrome mobile ignorava. Versione 1.99.

---

## v98 — 2026-06-29 `7616745`
- Fix pulsante stampa (file fornito dall utente). Versione 1.98.

---

## v97 — 2026-06-28 `bafc3da`
- Dettaglio intervento: km sotto il nome mezzo, label data 📅 Intervento programmato per il, riga vuota e 🏠 Presso : fornitore; badge In attesa di lavorazione anche nel dettaglio. Dicitura versione 1.97.

---

## v96 — 2026-06-27 `80c1e55`
- Chip notifiche: revisione un chip per veicolo che apre openRevisioneForm del mezzo; chip lavorazione distingue In lavorazione (data oggi/passata) da In attesa di lavorazione (data futura).

---

## v95 — 2026-06-27 `b43c48a`
- Planner (solo grafica): le barre verdi -risolto- vengono disegnate per ultime (sort stabile) cosi restano sopra arancio/transizione e tornano visibili sulle anomalie risolte in giornata.

---

## v94 — 2026-06-27 `bd8f577`
- Ripristinata la visualizzazione della data reale di scadenza revisione (fmtDate) su scheda veicolo e modale alert; la logica mensile resta solo per stato/preavviso.

---

## v93 — 2026-06-27 `d705d2a`
- Card gestione: pulsante Revisione prima di Modifica, 4 pulsanti in linea, Segna venduto rinominato Venduto.

---

## v92 — 2026-06-27 `1f0e750`
- Revisione: pulsante spostato dalle azioni alla data revisione sulla scheda (cliccabile, mostra mese); note precompilate con Revisione regolare.

---

## v91 — 2026-06-27 `6274525`
- Aggiunto pulsante Revisione sulla scheda veicolo che apre il form di risoluzione revisione (oltre che dall alert).

---

## v90 — 2026-06-27 `0242939`
- Gestione revisione: logica su base mese (preavviso 15gg prima del mese, scaduta a fine mese), alert include scadute, form risoluzione revisione (data/km/fornitore/nuova scadenza +2 anni/Risolto) che crea intervento chiuso Revisione periodica nello storico e aggiorna la scadenza sul veicolo; nel planner rosso senza tratteggio.

---

## v88 — 2026-06-27 `d1fa91b`
- Planner: giallo/arancio fino al giorno di apertura incluso (sfumatura sopra, niente stacco); sfumatura verde mezzo disponibile resa orizzontale (trasparente->verde).

---

## v87 — 2026-06-27 `76cba40`
- FIX: ripristinato il ramo else del rendering barre intervento (var color + barsHtml +=) rimasto troncato nella v=86, che faceva crashare il planner.

---

## v86 — 2026-06-27 `683cc4d`
- Planner: transizione origine->intervento con sfumatura (giallo/arancio -> rosso) sul giorno di creazione, attesa tratteggiata vera con trattini corti che parte dopo la sfumatura. Stesso trattamento per segnalazioni e anomalie.

---

## v85 — 2026-06-27 `adce147`
- Storico: a parita di data ordina per createdAt (creato dopo = piu in alto), cosi gli interventi creati dopo un check appaiono sopra e non sotto.

---

## v84 — 2026-06-27 `1065ab3`
- Planner: click su cella (mezzo+giorno) apre elenco di tutti gli eventi di quella cella (check, interventi, segnalazioni, gomme) con pulsanti operativi. Unificato un solo handler al posto dei fumetti per-barra.

---

## v83 — 2026-06-27 `05de334`
- Storico check: X di eliminazione (solo gestione avanzata) prima di ogni intervento nella lista collegata al check, per cancellare interventi da anomalia risolta.

---

## v82 — 2026-06-27 `8cb474a`
- Check viewer: due pulsanti separati Visualizza PDF e Stampa (stampa diretta via print frame, non dipende dal visualizzatore PDF del browser).

---

## v81 — 2026-06-27 `988651f`
- Form intervento uniformi: aggiunti KM+Fornitore al Risolto, KM al nuovo-da-planner. Layout coppie campi (date, chiusura) uniformato a due label sopra/due campi sotto in tutti i form.

---

## v80 — 2026-06-27 `59b62c1`
- Scheda check nello storico: lista interventi collegati (qualsiasi stato) con badge e link, sempre rintracciabili dal check a prescindere dall ordine in timeline.

---

## v79 — 2026-06-26 `f8bb67b`
- Coerenza annullati: un intervento annullato non conta piu come anomalia/segnalazione gestita ne blocca la ricreazione (15 punti allineati al planner). Annullati restano visibili e eliminabili nello storico.

---

## v78 — 2026-06-26 `a5082e4`
- Fix pulsante Risolto nel planner (apriva la dialog ma la seppelliva riaprendo la modale anomalie sopra). Storico: saveIntervention/saveChiusura ora usano refreshAll cosi gli interventi creati/chiusi compaiono subito.

---

## v77 — 2026-06-26 `d4b2214`
- Interventi chiusi: rosso fino al giorno prima della chiusura, verde mezza-cella sfumata (mezzo disponibile) sul giorno di chiusura. Risoluzione in giornata = solo verde. Anomalia/segnalazione gestite in giornata non mostrano piu arancio/giallo di attesa.

---

## v76 — 2026-06-26 `c7a0184`
- Barra attesa: altezza 6px e lunghezza dimezzata centrata (evita effetto linea continua).

---

## v75 — 2026-06-26 `307a614`
- Attesa come sottile barra rossa centrale (10px, eventi sotto visibili). Intervento aperto: rosso pieno da apertura fino a oggi (prosegue fino a chiusura), niente piu estensione infinita nei mesi futuri.

---

## v74 — 2026-06-26 `096f0fe`
- Doppia data intervento: dataProgrammazione + dataApertura. Tratteggiata rossa dal gap programmazione->intervento; taglio giallo/arancio anomalia+segnalazione alla data programmazione. Aggiunto campo in 4 form (anomalia, segnalazione, planner, modifica) con fallback retrocompatibile.

---

## DB Editor (`vcp-db-editor.html`) — 2026-06-29 / 2026-06-30
- 2026-06-29 `b15a7d5` — Aggiunge vcp-db-editor.html — DB Editor completo (manipolazione totale localStorage + IndexedDB: edit per-record/JSON, documenti binari, foto, azzeramenti protetti). Attiva il link in Impostazioni.
- 2026-06-29 `9416b09` — DB Editor: editor a celle per ogni dato (no JSON a mano). Campi tipizzati, interruttori booleani, anteprima immagini, gruppi per oggetti/array annidati con +campo/+elemento e rimozione singola. Ricerca senza perdita di focus.
- 2026-06-30 `b480326` — DB Editor in tabella: colonne=campi, righe=record, icona cestino per riga, celle modificabili in linea (autosave), +Riga/+Campo. Valori annidati e immagini gestiti senza JSON. Tabelle anche per IDB documenti/foto.
- 2026-06-30 `93c2b8f` — DB Editor: riga intestazione (label) fissa durante lo scroll verticale; prima colonna fissa in orizzontale. Tabella scrollabile in un riquadro.

---

## v60–v73 — 2026-06-26 (commit senza numero di versione)
- `8db2ac5` — pulsante Modifica check visibile nello storico veicolo (mod avanzata)
- `0627dce` — creazione intervento da anomalia planner — apre form per configurare
- `d618260` — ripristina checkbox spazzolePost e lavavetriPost nella scheda veicolo
- `bf86605` — icona spazzole posteriori + filtro voci check per dispositivi ritenzione
- `da953b2` — icona SVG tergicristallo per badge spazzole posteriori (dashboard + scheda)
- `0bc7cc0` — NON PRESENTE su voci check non in dotazione (form, viewer, stampa HTML e modulo)
- `343f422` — planner fasi intervento - tratteggiata attesa (createdAt-dataApertura) + rosso pieno lavorazione, giallo anomalia coesiste fino a giorno prima intervento, rimosso todayStr da colorazione interventi
- `60ceb98` — refreshAll() dopo eliminazione record - aggiorna dashboard, alerts, planner e riapre storico
- `25a71b1` — refreshAll riapre una sola vista corretta (storico o planner) dopo eliminazione, evita modal sovrapposte
- `9e8c387` — listener accumulati su modal anomalie causavano creazione multipla interventi (clone nodo + flag consumed)
- `8678ac1` — campo KM/data form intervento da anomalia non-inline per mobile + closeModal prima di aprire form, evita listener accumulati
- `e7834d2` — campo KM spostato sotto a tutta larghezza nel form intervento da anomalia (compilabile su mobile)
- `6a09d7f` — secondo overlay modal-2 per dettagli planner (planner resta visibile), ripristinati pulsanti +Intervento e Risolto nel modal anomalie
- `390bfb5` — colore intervento nel planner — dataApertura impostata alla data anomalia
- `38e1c65` — verifica integrità funzioni planner e interventi
- `8c46546` — planner scompare dopo salvataggio — usa closeModalSmart() per chiudere giusta modal
- `71815ee` — casella KM visibile nel form intervento da anomalia planner
- `9e8c30b` — campi intervento a riga nuova — rimuove inline per mobile usability
- `3ca7e58` — rimuove inline da TUTTI i campi intervento — mobile usability
- `ad10055` — alert anomalie — usa includes invece di startsWith per confronto descrizione
- `4d9c498` — verifica tutti gli alert — revisioni, anomalie, segnalazioni, gomme
- `36baf22` — alert anomalie — confronta checkId per riconoscere interventi gestiti
- `e51bceb` — planner mantiene il mese visualizzato dopo apertura intervento

---

## v59 — 2026-06-26 `6b9afd26d5`
### Modifica check da storico/viewer/lista (modalità avanzata)
- `openCheckForm` accetta ora un parametro `editCheckId` opzionale per caricare i dati di un check esistente
- `saveCheck` gestisce sia la creazione di un nuovo check che la modifica di uno esistente (aggiorna i dati senza creare duplicati)
- Aggiunto pulsante **✏️ Modifica** visibile solo in modalità avanzata in:
  - `openCheckViewer` (sotto il pulsante Stampa)
  - Storico veicolo (accanto ad "Apri check")
  - Lista check nella dashboard/tab gestione

---

## v58 — 2026-06-26 `657b4b8708`
### Fumetti planner → modal centrate
- Il click sulle barre intervento nel planner non apre più un fumetto posizionato ma una modal centrata con:
  - Stato, targa, nome veicolo, descrizione, fornitore, date apertura/chiusura
  - Pulsanti **✅ Chiudi**, **✕ Annulla**, **✏️ Modifica** (solo se non chiuso/annullato)
- Il click sulle barre gomme apre modal con data programmata, note e pulsante **✏️ Edita cambio gomme**
- Rimosso codice fumetto (bubble) per interventi e gomme

---

## v57 — 2026-06-26 `d12094d8eb`
### Revert a versione stabile con elimina storico
- Ripristino del commit `d1cb1767e9` dopo instabilità introdotta in v56
- Versione stabile con gestione avanzata, elimina record storico, senza corsie complesse

---

## v56 — 2026-06-26 `2c653af5f6` ⚠️ INSTABILE — REVERTATO
- Tentativo barra unica planner con priorità colore check — rotto colori e click

---

## v55 — 2026-06-25 `d1cb1767e9`
### Pulsante Elimina su tutti i record dello storico (modalità avanzata)
- Aggiunto pulsante **🗑️ Elimina** visibile solo in modalità avanzata su:
  - Check mensili nello storico
  - Interventi nello storico
  - Segnalazioni nello storico
  - Cambi gomme nello storico
- Aggiunta funzione `eliminaSegnalazione` (le altre esistevano già)
- `openHistory` legge il flag `gestioneAvanzata` per mostrare/nascondere i pulsanti

---

## v54 — 2026-06-25 `f87c46ea94`
### Revert a 9737f43aa1 — senza piste, con gestione avanzata
- Ripristino del commit pre-corsie con tutte le funzionalità avanzate intatte

---

## v53 — 2026-06-25 `59c4a31439` ⚠️ INSTABILE — REVERTATO
- Ripristino parziale a1e9519f38 — aveva ancora le lane, revertato

---

## v52 — 2026-06-25 `8ea7ace83a`
### Fix corsie planner + colore intervento
- Corsie fisse per veicolo: ogni storia riceve un indice lane stabile per tutto il mese
- Targa mostrata solo sulla lane 0 (non su ogni corsia del veicolo)
- Colore intervento cambiato da `#f87171` a `#dc2626` (rosso più saturo)

---

## v51 — 2026-06-24 `71175653a7`
### Fix gradiente chiusura intervento
- Gradiente trasparente→verde applicato solo sull'ultima cella (giorno di chiusura) via overlay div CSS
- Barre su settimane precedenti rimangono rosse solide senza sfumatura

---

## v50 — 2026-06-24 `1a352efff0`
### Fix targa su continuazione settimana
- La targa viene mostrata su ogni segmento che inizia a `colStart=0` (inizio settimana) o è il primo segmento della storia
- Posizionamento targa corretto sulla lane giusta

---

## v49 — 2026-06-24 `70e7e8d05c`
### Interval scheduling globale corsie planner
- Corsie assegnate tramite interval scheduling su coordinate assolute (row×7+col)
- Ogni storia mantiene la stessa corsia per tutta la durata, anche su settimane diverse
- Targa mostrata a inizio settimana su ogni continuazione

---

## v48 — 2026-06-24 `d2385419a4`
### Refresh planner automatico alla chiusura di modal-2
- Il planner si aggiorna automaticamente quando si chiude una modal secondaria (modal-overlay-2)

---

## v47 — 2026-06-24 `f7e2d5c15f`
### Fix interval scheduling corsie tra settimane
- Interval scheduling globale per veicolo con `absStart/absEnd` calcolati sull'intera durata
- `n` (numero lane) calcolato come massimo globale per storia, costante tra settimane

---

## v46 — 2026-06-24 `c7f03b80b3`
### Fix gradiente chiusura su isLast
- Gradiente rosso→verde applicato solo sul segmento `isLast` dell'intervento
- Funziona correttamente sia per interventi aperti che chiusi

---

## v45 — 2026-06-24 `e017f29deb`
### Corsie planner con interval scheduling
- Introdotte corsie (lane) per gli interventi: più interventi sullo stesso veicolo occupano corsie separate
- Gradiente rosso→verde sul giorno di chiusura intervento
- Interval scheduling per assegnare la corsia minima libera ad ogni storia

---

## v44 — 2026-06-19 `a1e9519f38`
### Fix NON PRESENTE in stampaCheckModulo
- Override `NON PRESENTE` applicato correttamente anche in `stampaCheckModulo`

---

## v43 — 2026-06-19 `040e649a3c`
### Fix NON PRESENTE in stampa (check pregressi inclusi)
- Override `NON PRESENTE` esteso anche ai check salvati prima dell'introduzione dei flag veicolo

---

## v42 — 2026-06-19 `6ed8bc84a1`
### Override NON PRESENTE nel preview check
- `NON PRESENTE` applicato nel viewer check anche per check salvati prima dei flag

---

## v41 — 2026-06-19 `ff5a4704dc`
### Override runtime NON PRESENTE in stampa check
- NON PRESENTE calcolato a runtime in base ai flag del veicolo, non salvato nel check

---

## v40 — 2026-06-19 `0d1218dd34`
### NON PRESENTE in stampa check HTML e PDF
- Le voci non pertinenti al veicolo mostrano "NON PRESENTE" nella stampa HTML e nel PDF

---

## v39 — 2026-06-19 `d9ff599290`
### Checkbox configurazione veicolo + NON PRESENTE in check
- Aggiunto checkbox **Spazzole posteriori** e **Lavavetri posteriori** nella scheda veicolo
- Voci non pertinenti al veicolo mostrano "NON PRESENTE" nel form check e nel viewer
- Aggiunto checkbox **Sollevatore** e **Pedana** nella configurazione veicolo
- Pulsanti Documenti/Storico/Gomme visibili nel tab gestione mezzi

---

## v38 — 2026-06-19 `42f7aa4354`
### Fix dashboard originale + pulsanti gestione solo in tab gestione
- Ripristinata dashboard originale senza modifiche al layout
- Pulsanti gestione avanzata visibili solo nel tab dedicato

---

## v37 — 2026-06-19 `5e91a852b6`
### Fix viewer immagini su PWA/mobile
- Modal immagini nascosta con `visibility:hidden` invece di `display:none` per evitare flash
- Z-index aumentato a 10000 per superare altri layer

---

## v36 — 2026-06-19 `6e0840ceb2`
### Fix toolbar viewer immagini su touch
- Pulsanti toolbar del viewer immagini non bloccati su dispositivi touch/PWA

---

## v35 — 2026-06-19 `0100270f05`
### Annullamento cambio gomme su planner e storico
- Cambio gomme annullato mostrato con stile diagonale nel planner
- Conferma prima dell'annullamento
- Visibile nello storico con stato "Annullato"

---

## v34 — 2026-06-18 `cd448f8962`
### Interventi annullati con stile diagonale
- Le barre degli interventi annullati mostrano un pattern diagonale rosso chiaro
- Distinti visivamente dagli interventi attivi

---

## v33 — 2026-06-18 `dc2135d184`
### Pulsante Risolto anomalia dal planner
- Dal modal delle anomalie nel planner è possibile segnare direttamente una voce come risolta
- Stessa funzionalità disponibile anche dalla scheda intervento

---

## v32 — 2026-06-18 `429c6bc7ff`
### Interventi Gommista in blu nel planner
- Le barre dei cambi gomme programmati mostrate in blu (`#60a5fa`) nel planner
- Legenda aggiornata con voce Gomme

---

## v31 — 2026-06-18 `951e656b02`
### Ordinamento storico per data chiusura
- Lo storico degli interventi è ordinato per `dataChiusura` se disponibile, altrimenti per `dataApertura`
- Ordine cronologico corretto anche con interventi chiusi in date diverse dall'apertura

---

## v30 — 2026-06-17 `1a93d0f008`
### refreshAll() centralizzato
- Introdotta funzione `refreshAll()` che aggiorna planner, storico e dashboard dopo ogni salvataggio
- Eliminato codice duplicato di refresh sparso nelle varie funzioni

---

## v29 — 2026-06-17 `905dc582cb`
### Fix storico e planner dopo creazione intervento da anomalia
- Lo storico si riapre aggiornato dopo la creazione di un intervento da un'anomalia check
- Il planner si aggiorna automaticamente

---

## v28 — 2026-06-16 `5fa2a325de`
### Fix interventi annullati esclusi da controlli
- Gli interventi annullati non contano come gestiti per le anomalie check
- Esclusi dal controllo duplicati all'apertura di un nuovo intervento

---

## v27 — 2026-06-16 `8604a39671`
### Altezza fasce planner uniforme per mese
- Le fasce dei veicoli nel planner hanno altezza uniforme per tutto il mese
- Eliminato sfalzamento verticale delle barre tra settimane diverse

---

## v26 — 2026-06-16 `0e3fc2a87d`
### Dettaglio anomalie risolte nel planner
- Il modal delle anomalie dal planner mostra lo stato dell'intervento collegato
- Visibili data e stato anche per anomalie già risolte

---

## v25 — 2026-06-16 `cc189fa318`
### Bordo selezione su barre planner
- Bordo 1px evidenziato sul segmento cliccato nel planner
- Applicato anche su barre anomalia-check e segnalazione

---
