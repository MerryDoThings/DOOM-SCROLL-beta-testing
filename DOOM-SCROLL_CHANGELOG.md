# DOOM/SCROLL — Changelog completo
*Dalla v2.6 originale alla versione corrente*

---

## v2.6 — Punto di partenza
File originale caricato da Merry. Gioco funzionante con 5 finali, feed satirico italiano, sistema QI, cervello, ads. Tutto in un unico file HTML da 2438 righe.

---

## v2.7 — Distribuzione e UX base

**Meta e social**
- Titolo riscritto: `DOOM/SCROLL — un feed satirico che vuole il tuo QI`
- Meta description completa
- Open Graph tags completi (og:title, og:description, og:image, og:type, og:locale)
- Twitter Card (summary_large_image)
- Theme-color `#0d0d0d` per barra di stato iOS
- Color-scheme dark
- Favicon SVG inline (puntino rosso su nero, niente file extra)

**OG Image**
- Generata con Pillow (Python), 1200×630px
- Design replica l'interfaccia del gioco: header + tre stat card (QI/tempo/cose viste)
- Tagline "UN FEED SATIRICO ITALIANO" + CTA "SCOPRI I 5 FINALI →" in rosso

**Sottotitolo dinamico**
- Riga sotto il brand: "scrolla. il QI cala. X/5 finali da scoprire."
- Si aggiorna con i finali sbloccati: "2/5 finali sbloccati. ne mancano 3."
- Dopo tutti i 5: "tutti e 5 i finali sbloccati. ora scrolli per sport."
- Persiste tra sessioni via localStorage

**Tasto Esc**
- Chiude il popup del cervello (conta come "ignora", coerente col tema)
- Chiude l'overlay shop

**Pulsante "Condividi"**
- Presente su ogni schermata di finale
- Testo di condivisione personalizzato per finale
- Web Share API su mobile, fallback clipboard su desktop
- Stato "copiato" con feedback visivo

**Toast transizioni QI**
- Appaiono quando si cambia fase (cosciente → intontito → plastificato → cosmico → nirvana)
- Una stringa per fase (successivamente espanse a 3 varianti in v2.11)

---

## v2.8 — Contrasto e leggibilità

**Colori riscritti**
- `--text`: `#e8e8e8` → `#ffffff`
- `--text-dim`: `#888` → `#aaaaaa`
- `--text-muted`: `#555` → `#888888`
- `--text-faint`: `#3a3a3a` → `#666666`
- Tutti i grigi hardcoded nel CSS portati a valori leggibili

**Font size**
- Label statistiche, sorgenti notizie, tag, label quiz: da 9px a 11px
- Label promo card: da 8px a 10px
- Bottoni quiz: testo da `#b8b8b8` a `#cccccc`

---

## v2.9 — Refactoring architettura

**Estrazione JSON**
- `quizzes.json`: 24 quiz estratti dall'HTML, normalizzati in formato uniforme `{q, opts[]}`
- `content.json`: tutti i pool di notizie, ads, brain messages, fake comments estratti (1190+ item)
- Fetch parallelo all'avvio con `Promise.allSettled`
- Fallback su dati minimi se i fetch falliscono (gioco parte comunque)

**Riduzione HTML**
- Da 2488 righe a ~1021 righe (−59%)
- Da 111 KB a 61 KB

**Fix SOURCES e TIMES**
- Rimossi per errore con il blocco dati, re-inseriti come costanti inline

---

## v2.10 — Card Lercio

**Integrazione Lercio.it**
- `lercio.json`: 80 titoli (44 verificati da lercio.it + 36 scritti in stile Lercio)
- 5 titoli auto-referenziali che fungono da disclaimer implicito (es. "Studio: il 77% degli italiani non distingue satira da notizie reali, inclusa questa")
- Card visivamente distinta: bordo ambrato, background `#131108`, tag `SATIRA` in piccolo
- Source normale del pool (non attribuisce Lercio per singola card)
- Fetch parallelo insieme agli altri JSON

---

## v2.11 — Narrativa e progressione

**Meta card rimossa**
- Eliminato il disclaimer esplicito ("alcune notizie vengono da un sito satirico")
- Sostituito dai 5 titoli auto-referenziali nel pool Lercio

**Card Lercio semplificata**
- Rimosso click handler che dava +1 QI (troppo meta)
- Source normale, comportamento identico alle altre notizie

**"Carica altro" che degenera**
- Su due assi: velocità click (brainrot acuto) e totalLoadMore (stanchezza cronica)
- Scala: "carica altro (sì, davvero)" → "un altro po'" → "ancora" → "dai" → "pls" → "↓"

**Toast QI con 3 varianti per fase**
- 5 fasi × 3 messaggi = 15 stringhe totali, estratte a caso
- Chi rigioca non vede sempre lo stesso toast

**Varianti esposizione passiva (timer)**
- 12 messaggi rotanti invece della stringa fissa
- Shufflati all'inizio, ruotano in ordine

**Varianti scrolling volontario**
- 10 messaggi rotanti per la perdita QI da "carica altro"

**Cervello per fase QI**
- 4 pool distinti: sopra 70 (gentile), 40-70 (preoccupato), 20-40 (urgente), sotto 20 (rassegnato)
- 35% delle volte usa ancora i messaggi originali per varietà

**Frequenza Lercio adattiva**
- Sopra QI 60: ogni 5 load / 40-60: ogni 3 / 20-40: ogni 2 / sotto 20: quasi garantita

**Pool brainrot riscritto**
- Sigma/gigachad era, NPC/TikTok era, ratio/meme azione, italiano internet
- Brainrot italiano ridotto a ~20% del pool, solo nelle fasi finali

**Fix pool esauriti**
- `pickItem` ora fa auto-reset invece di fallback su REPEATABLE_NEWS

**Fix `undefined` nella card**
- Guard su `FAKE_COMMENTS` vuoto e item malformati

---

## v2.12 — Finali riprogettati

**5 finali completamente riscritti** (CSS + HTML)

**Nirvana** — sfondo quasi nero, numero "0" enorme e sbiadito. Frase chiave: "la pace che senti adesso non è tua. è assenza."

**Smetti** — estetica clinica, testo a sinistra come referto medico. Sequenza esatta fino alla ricaduta. Ultima riga in rosso: "punto a capo."

**Quit definitivo** — sfondo verde scurissimo, achievement card con emoji (poi rimpiazzate in v3.0.1). SVG grass procedurale.

**Capitalismo Spirituale** — layout da landing page wellness: stelle fake, price block, CTA arancione, fine print cinico.

**Brainrot** — 28 termini random salgono in background, frammenti di testo in primo piano. Diverso ogni volta.

**Rimosso** `spawnEmojis()` e floating emojis del vecchio nirvana

---

## v3.0 parziale — Feature major

**Splash screen** — prima visita vs ritorno, counter finali sbloccati

**Schermata pre-finale** — 1-3 frasi generate dai dati reali della sessione prima di ogni finale

**Pressione crescente nel loop** — soglie a 3/5/8 minuti che cambiano tono e comportamento

**Sesto finale segreto "santo"** — trigger: tutti i quiz cosciente + no ad + ascolta cervello la prima volta + no click Lercio. Override di "smetti". Estetica bianca minimale.

**Notifica diegetica** — "Ti ho cercato. Stai bene?" con scelta rispondi/ignora. Ferma il timer. Rispondere bene → trigger quit.

**Audio ambient diegetico** — Web Audio API. Si deteriora con il QI. Si ferma su nirvana e quit.

**Metamorfosi capitalismo** — dopo 2+ acquisti, body class `morph-N`, feed e colori virano verso crema/oro.

---

## v3.0.1 — Maxi audit + A1

**Bug fix**
- Modali non si chiudevano al restart (notifOverlay, convOverlay, prefinalOverlay)
- `purchaseGateStep` non si resettava al restart
- Animazione pre-finale: flash → fade scaglionato + clone DOM trick
- `playZenSound` syntax error
- Toast: 2.4s → 5s, font 12px → 13px

**A1 — Quit definitivo riprogettato**
- Rimosso design achievement card con emoji
- Nuovo design monumentale con costruzione progressiva:
  - Label "RICONOSCIMENTO RARO" (fade 0.3s)
  - Typing effect "QUIT DEFINITIVO" lettera per lettera (delay 1.2s)
  - Subtitle con fade (3.5s)
  - 5 righe del monument una alla volta (4.5s → 8.8s)
  - Lapide SCREEN TIME (10s)
  - Stats e bottoni (11s+)
- Sfondo `#050a05` con pulsazione lenta verso `#081208`
- SVG grass procedurale in basso

---

## v3.1.0 — Trigger D + A3 SISTEMA + bugfix + polish

**Trigger quit — Opzione D**
- Vecchia logica: `usefulAdClicks >= 2 && adClicks < 5` + brain x3 → quit
- Nuova logica: `everIgnored || adClicks >= 1` + brain x3 → quit
- "smetti" resta la via pulita (mai ignorato, mai comprato nulla)
- "santo" resta subset corretto di "smetti" — condizioni invariate

**A3 — Il SISTEMA come settima voce**
- 18 messaggi monospace, tono freddo, mai sarcastico esplicitamente
- ID sessione `utente_XXXX` (4 cifre random, reset al restart)
- Max 7 per sessione (`SISTEMA_MAX`)
- Trigger: 2° load-more (prima comparsa), ogni 4° load-more, primo acquisto ad, 2° ignore cervello, timer idle 90s
- Non conta come newsCount, non resetta cardsSinceInterruption
- CSS: `.sistema-card` — `#0b0b0b` bg, testo `#888888`, bordo sinistro `#404040`, `box-shadow` doppio per contrasto, label `SISTEMA` a 8px sopra

**Bugfix quit overlay** *(tre bug pre-esistenti scoperti giocando)*
- `position:relative` su `.ending-overlay.ending-quit` sovrascriveva `position:fixed` della base → overlay finiva nel flow del documento in fondo al feed. **Rimosso.**
- `overflow:hidden` clippava il contenuto su schermi piccoli. **Cambiato in `overflow-y:auto`.**
- `width:11ch` per titolo "QUIT DEFINITIVO" (15 caratteri) → testo troncato a "QUIT DEFINI". **Corretto a `15ch`**, steps da 20 a 15.

**Timing quit riequilibrato**
- Prima versione (originale): troppo lento, sembrava rotto (pulsanti a 12s+)
- Seconda versione (dimezzata): troppo veloce per leggere con calma
- Versione finale: label 0.3s → titolo 1.2s → subtitle 3.4s → righe monument ogni ~1s (4.5s→8.2s) → tombstone 9.2s → stats 10.2s → pulsanti 11.2s

**Toast riposizionati**
- Da `bottom:18px` a `top:158px` (sotto l'header sticky)
- Non si accumulano più sopra il bottone "carica altro"

---

## v3.2.0 — A2 + A4 + A5 + A6 + A9 + B1 + JSON

**A2 — Feeling di avvicinarsi ai finali**

*Nirvana — 4 soglie di degrado progressivo del feed:*
- QI < 50: titoli a 7 parole + `…`, fonte e tag sbiaditi (`nirvana-1`)
- QI < 30: titoli a 3 parole + `…`, tag sparisce, testo grigio (`nirvana-2`)
- QI < 15: 2 parole, niente fonte/tag/orario, card quasi vuota (`nirvana-3`)
- QI < 5: 1 parola casuale, card trasparente, testo quasi invisibile (`nirvana-4`)
- Degrado applicato a news card, Lercio card, quiz card (opacity+blur), promo card (opacity+blur), espansioni e commenti
- Quiz e promo card a nirvana-3/4: `pointer-events: none`

*Brainrot — hint bottone:*
- 3–11 click veloci: sotto il bottone compare `più veloce succede qualcosa →`
- 12+ click veloci pre-degrado: `qualcosa sta succedendo.`
- Si cancella quando il degrado vero inizia

*Quit — whisper nel feed:*
- Appare dopo ogni `ignoreBrain()` se `brainListened >= 1`
- Testo centrato monospace verde scurissimo, niente bordi
- Sequenza: `ci risiamo.` → `lo so.` → `okay.` → `quando sei pronto.` → `.`

**A4 — Espansione card notizie**
- Click su qualsiasi card → si allarga mostrando descrizione satirica contestuale al tag
- 10 categorie × 5 varianti + pool default per tag non mappati
- Toast al click: 10 varianti rotanti casuali ("hai aperto la notizia. ora ne sai di più. cambia qualcosa? no." ecc.)
- Costo -1 QI per espansione
- Espansione una volta sola per card, degrada con QI come il resto del feed

**A5 — Commenti strutturati**
- 57 commenti nel pool, divisi per tono: polarizzazione automatica, falsa familiarità, capro espiatorio, Dunning-Kruger, non sequitur, bot/spam, fuori tempo massimo, risponde a nessuno, autocensore, maiuscolo totale, filosofo da bar
- Struttura: autore (20 nomi italiani) + testo + reazioni 👍 🤡 con numeri fissi
- 2-3 per espansione; a QI < 30 → 1; a QI < 15 → 0
- Testo commento degradato con `degradeTitle()` al QI corrente
- "Carica altri N commenti" → toast sarcastico (6 varianti, N random 47-847)

**A6 — Contenuto**

*Filone antifascismo (34 titoli, 6 angolazioni):*
- Profili IG "tradizionalisti", libri revisionisti, algoritmi, manifestazioni "non politiche", dichiarazioni politiche, commemorazioni
- Tono: mostra la normalizzazione senza rilegittimarla; niente nomi reali, niente termini ammirativi
- Mergiato in `NEWS_INTERESTING` shufflato

*Sources rielaborate:*
- Da 8 a 27 sources, tutti con giochi di parole (ANSIA, CORRIERE DELLA SEGA, LA RIPUBBLICA, IL SOLE 8-16 ORE, RAINAUSEA, LELLO, SUCCEDERE, LO IERI ecc.)

**A9 — Il timestamp che ti tradisce**
- Esattamente al minuto 5, il timer salta avanti di 7-10 minuti casuali. Una volta sola per sessione.
- Nessun avviso, nessun toast — succede e basta
- Subito dopo: card SISTEMA nel feed (`[TIMESTAMP] utente_XXXX — anomalia registrata. / tempo di sessione non corrisponde al tempo percepito. / nessuna azione richiesta.`)
- Reset al restart

**B1 — La X che non è un'opzione**
- `×` nell'header, quasi invisibile (`#2a2a2a`), hover leggermente più visibile
- Click → toast da pool di 7 varianti rotanti
- Nessuna animazione, niente shake — solo il toast

**JSON consolidato**
- Tutte le nuove chiavi aggiunte a `content.json`: `sources`, `times`, `news_antifascismo`, `comment_authors`, `comment_pool`, `expansion_descs`, `expansion_default`, `expansion_toasts`, `fake_close_msgs`
- HTML: pool convertiti da `const` a `let`, valori inline restano come fallback se il fetch fallisce
- `applyContent()` sovrascrive i fallback con i valori dal JSON se presenti

**Bugfix 3.2.0**
- `quizAnsweredCount >= 1` aggiunto alla condizione finale santo — non si triggerava più senza aver risposto a nessun quiz
- `app.style.visibility = 'hidden'` in `triggerEnding` — rimosso il flash del feed tra prefinal e finale
- `position:relative` su `.ending-brainrot` rimosso — stesso bug del quit, overlay finiva in fondo al feed
- Chiave `'Politica':` caduta da `EXPANSION_DESCS` durante str_replace — ripristinata


---

## v3.1.1 — Toast system

**Problema:** i toast si accumulavano sopra il load-more button bloccando la vista, comparivano sopra le schermate di finale (z-index 300 > overlay 200), e duravano troppo.

**Soluzione E — padding dinamico**
- `ResizeObserver` su `#toastWrap`: quando ci sono toast attivi, aggiunge `padding-bottom` dinamico a `#app` pari all'altezza dei toast + 28px di margine. Quando i toast spariscono, torna a 20px. Il load-more button è sempre visibile sopra i toast, senza overlap.
- `#app` padding-bottom rimosso da hardcoded 80px → gestito interamente dal ResizeObserver

**Fix**
- `z-index` toast: 300 → 190 (sotto tutti gli overlay di finale a 195-200)
- `clearToasts()` chiamata all'avvio di ogni finale — nessun toast sopravvive alla schermata di fine
- Max 2 toast contemporanei: se ne arriva un terzo, rimuove il più vecchio
- Durata: 5.5s → 3.5s (CSS delay `5s` → `3s`, JS timeout `5600` → `3600`)
