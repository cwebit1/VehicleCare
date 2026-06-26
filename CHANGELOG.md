# VehicleCare — Changelog

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
