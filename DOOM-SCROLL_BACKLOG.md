# DOOM/SCROLL — Backlog
*Documento di lavoro. Cancelliamo le voci man mano che vengono implementate con successo.*

---

## STATO ATTUALE

**Ultima sessione:** A2 + A4 + A5 + A6 + A9 + B1 + JSON consolidato + bugfix vari
**Versione corrente:** 3.2.0

---

## SEZIONE A — APPROVATE CON PIANO PRONTO

### A7. Rielaborazione header
**Sessione dedicata di design.** Riprogettare la zona sticky in alto, contenuto e grafica.
*Nota: i toast sono già stati spostati in `top` in v3.1.1 — la posizione finale dipende da questo redesign.*

### A8. Screenshot come ricompensa
Pulsante "salva un ricordo" su ogni finale. Canvas API → PNG. Design specifico per finale.

### A10. Il finale che non finisce (nirvana)
Dopo schermata nirvana, 3-4 card appaiono sotto. Restart bloccato 20s. Poi schermo nero vero.

### A11. Continuità tra partite
Localstorage estesa con statistiche cumulative. Card "bentornato dal [finale]". Sottotitolo "sessione N".

---

## SEZIONE B — APPROVATE MA DA PIANIFICARE

### B2. Modalità lettore / commentary mode
7 click su un glifo nascosto → ogni notizia mostra il pool di provenienza.

### B3. Chat con Giulia — revisione
La conversazione diegetica post-notifica è meh. Riscrivere tono, battute, scelte. Renderla più credibile e più narrativamente densa. Da pianificare insieme.

---

## SEZIONE C — DA PENSARE

### C1. La consapevolezza che peggiora le cose
Dopo card Lercio meta, il feed sa che tu sai. Notizie più assurde. Ma scrolli lo stesso.

### C2. La conferma di realtà
Notifiche "verifica anti-bot: sei umano? sì/no". "No" → feed surreale.

### C3. SISTEMA — ripensare il ruolo narrativo
Il SISTEMA come settima voce non funziona come narratore: sembra solo una presenza extra, non integrata nel ritmo del gioco. Da valutare: ridurne la frequenza? Cambiarne il trigger? Sostituirlo con qualcosa di più organico? Oppure eliminarlo e redistribuire i messaggi più efficaci altrove. Sessione dedicata.

---

## PROMEMORIA / NON-CODE

- **Finale segreto "santo"** — testare manualmente quando online. Trigger complesso, verificare che tutte le condizioni scattino correttamente in sessione reale.
- **Immagine lobotomia QI<5** — in attesa versione HD da DALL-E per sfondo feed a QI bassissimo.

---

## SEZIONE D — GIÀ FATTE

- ~~Splash screen iniziale~~ ✅
- ~~Sessione 2 di base~~ ✅
- ~~Pressione crescente nel loop~~ ✅
- ~~Riga pre-finale~~ ✅ (3.0.1)
- ~~Sesto finale segreto "santo"~~ ✅
- ~~Notifica diegetica + conversazione~~ ✅
- ~~Audio ambient con AudioContext~~ ✅
- ~~A1: Quit definitivo riprogettato~~ ✅ (3.0.1)
- ~~Trigger quit: opzione D~~ ✅ (3.1.0)
- ~~A3: Il SISTEMA come settima voce~~ ✅ (3.1.0)
- ~~Bugfix quit overlay (position:relative, overflow, width 11ch)~~ ✅ (3.1.0)
- ~~Toast: max 2, durata 3.5s, pulizia al finale, bottom fisso~~ ✅ (3.1.1)
- ~~A2: Feeling avvicinamento finali~~ ✅ (3.2.0) — nirvana 4 soglie QI, brainrot hint bottone, quit whisper nel feed
- ~~A4: Espansione card notizie~~ ✅ (3.2.0) — click → descrizione satirica + toast pool, -1 QI, degrada con QI
- ~~A5: Commenti strutturati~~ ✅ (3.2.0) — 57 commenti, autore + reazioni, "carica altri N" → toast sarcastico
- ~~A6: Filone antifascismo (34 titoli, 6 angolazioni)~~ ✅ (3.2.0)
- ~~A6: Sources rielaborate (27 giochi di parole)~~ ✅ (3.2.0)
- ~~A9: Timestamp che ti tradisce~~ ✅ (3.2.0) — salta dopo 5 min, card SISTEMA nel feed
- ~~B1: La X che non è un'opzione~~ ✅ (3.2.0) — toast rotanti, 7 varianti
- ~~JSON consolidato~~ ✅ (3.2.0) — tutti i pool in content.json, HTML usa fallback inline
- ~~Santo trigger fix: quizAnsweredCount >= 1~~ ✅ (3.2.0)
- ~~Flash feed → finale rimosso~~ ✅ (3.2.0)
- ~~Finale brainrot: position:relative rimosso~~ ✅ (3.2.0)
- ~~Quiz + promo card degradano con QI (opacity + blur)~~ ✅ (3.2.0)
- ~~Commenti degradano con QI (testo + struttura)~~ ✅ (3.2.0)


---

## SEZIONE A — APPROVATE CON PIANO PRONTO

### A2. Feeling di avvicinarsi ai finali
**Per nirvana:** sotto QI 30 i titoli si accorciano, sotto 15 frammenti, sotto 5 una parola.
**Per brainrot:** dopo soglie di click, una card del feed risponde: "ancora?" → "ancora." → "."
**Per quit:** tracker di ignoranze post-ascolto, cervello dice "lo so. ci risiamo." → "okay. quando sei pronto."

### A4. Espansione card notizie
Click su card → si espande mostrando descrizione satirica. Costo -1 QI. Campo `expansion` nel JSON.

### A5. Sistema commenti articolato
Commento con autore + reazioni (👍 47 🤡 12). 1-3 per card. Toni diversi. "Carica altri 234 commenti" che non funziona.

### A6. Rielaborazione JSON
**Sessione dedicata.** Riscrivere/eliminare frasi deboli. Aggiungere espansioni A4 contestualmente.

**Nota di contenuto: filone satira anti-fascismo contemporaneo.**
Sotto-pool di titoli che satirizzano la normalizzazione del linguaggio neofascista/nostalgico nei feed italiani.
Angolazioni da scrivere insieme:
- Profili IG con estetiche "tradizionaliste" che superano i 100k follower
- Libri revisionisti pubblicati e recensiti come "lettura coraggiosa"
- Slogan rispuntati a manifestazioni "non politiche"
- Algoritmi che spingono certi contenuti perché generano interazione
- Dichiarazioni politiche moderne che riprendono retorica del ventennio
- Commemorazioni che diventano raduno

**Tono richiesto:** affilato, mostra il fenomeno senza rilegittimarlo. La satira sta nel mostrare *quanto è normalizzato* il fenomeno, non nel ripetere il linguaggio. Niente citazioni reali, niente termini ammirativi nemmeno in chiave satirica — il rischio screenshot fuori contesto è troppo alto.

### A7. Rielaborazione header
**Sessione dedicata di design.** Riprogettare la zona sticky in alto, contenuto e grafica.

### A8. Screenshot come ricompensa
Pulsante "salva un ricordo" su ogni finale. Canvas API → PNG. Design specifico per finale.

### A9. Il timestamp che ti tradisce
Dopo 5 minuti, una volta sola, il timer salta avanti senza preavviso (es. 05:14 → 12:47).

### A10. Il finale che non finisce (nirvana)
Dopo schermata nirvana, 3-4 card appaiono sotto. Restart bloccato 20s. Poi schermo nero vero.

### A11. Continuità tra partite
Localstorage estesa con statistiche cumulative. Card "bentornato dal [finale]". Sottotitolo "sessione N".

---

## SEZIONE B — APPROVATE MA DA PIANIFICARE

### B1. L'opzione "esci" che non è un'opzione
"X" nascosta → click → animazione → toast "abbiamo recuperato la tua sessione. bentornato."

### B2. Modalità lettore / commentary mode
7 click su un glifo nascosto → ogni notizia mostra il pool di provenienza.

### B3. Chat con Giulia — revisione
La conversazione diegetica post-notifica è meh. Riscrivere tono, battute, scelte. Renderla più credibile e più narrativamente densa. Da pianificare insieme.

---

## SEZIONE C — DA PENSARE

### C1. La consapevolezza che peggiora le cose
Dopo card Lercio meta, il feed sa che tu sai. Notizie più assurde. Ma scrolli lo stesso.

### C2. La conferma di realtà
Notifiche "verifica anti-bot: sei umano? sì/no". "No" → feed surreale.

### C3. SISTEMA — ripensare il ruolo narrativo
Il SISTEMA come settima voce non funziona come narratore: sembra solo una presenza extra, non integrata nel ritmo del gioco. Da valutare: ridurne la frequenza? Cambiarne il trigger? Sostituirlo con qualcosa di più organico? Oppure eliminarlo e redistribuire i messaggi più efficaci altrove. Sessione dedicata.

---

## PROMEMORIA / NON-CODE

- **Finale segreto "santo"** — testare manualmente quando online. Trigger complesso, verificare che tutte le condizioni scattino correttamente in sessione reale.

---

## SEZIONE D — GIÀ FATTE

- ~~Splash screen iniziale~~ ✅
- ~~Sessione 2 di base~~ ✅
- ~~Pressione crescente nel loop~~ ✅
- ~~Riga pre-finale~~ ✅ (bug fixato in 3.0.1)
- ~~Sesto finale segreto "santo"~~ ✅
- ~~Notifica diegetica + conversazione~~ ✅
- ~~Audio ambient con AudioContext~~ ✅
- ~~Toast più lunghi (5.5s)~~ ✅
- ~~A1: Quit definitivo riprogettato~~ ✅ (3.0.1)
- ~~Trigger quit: opzione D~~ ✅ (3.1.0)
- ~~A3: Il SISTEMA come settima voce~~ ✅ (3.1.0)
- ~~Bugfix quit overlay~~ ✅ (3.1.0)
- ~~Toast: sistema E (padding dinamico + max 2 + pulizia al finale)~~ ✅ (3.1.1)
