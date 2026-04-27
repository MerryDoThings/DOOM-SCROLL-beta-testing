# DOOM/SCROLL — Backlog v3.0
*Documento di lavoro. Cancelliamo le voci man mano che vengono implementate con successo.*

---

## STATO ATTUALE

**Ultima sessione:** maxi audit + A1 (quit definitivo riprogettato)
**Versione corrente:** 3.0.1

---

## ⚠️ DA DECIDERE (urgente, prima di procedere)

### Trigger del finale "quit" controintuitivo
Adesso il quit scatta solo se hai comprato 2-4 ad e poi hai ascoltato il cervello 3 volte. La via "pulita" porta solo al finale "smetti".

**Possibili soluzioni:**
- A. Quit con ascolto x3, indipendente da ad
- B. Quit con ascolto x3 + scelta consapevole nella conversazione diegetica
- C. Tieni quit come "ricompensa per chi si è ripreso", logica più chiara

---

## SEZIONE A — APPROVATE CON PIANO PRONTO

### A2. Feeling di avvicinarsi ai finali
**Per nirvana:** sotto QI 30 i titoli si accorciano, sotto 15 frammenti, sotto 5 una parola.
**Per brainrot:** dopo soglie di click, una card del feed risponde: "ancora?" → "ancora." → "."
**Per quit:** tracker di ignoranze post-ascolto, cervello dice "lo so. ci risiamo." → "okay. quando sei pronto."

### A3. Il SISTEMA come settima voce
Messaggi monospace stile console, ti chiamano "utente_XXXX". 5-7 a sessione. Stile freddo, mai sarcastico esplicitamente.

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

---

## SEZIONE C — DA PENSARE

### C1. La consapevolezza che peggiora le cose
Dopo card Lercio meta, il feed sa che tu sai. Notizie più assurde. Ma scrolli lo stesso.

### C2. La conferma di realtà
Notifiche "verifica anti-bot: sei umano? sì/no". "No" → feed surreale.

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

---

## BUG FIX 3.0.1
- Modali (notifOverlay, convOverlay, prefinalOverlay) ora si chiudono al restart
- `purchaseGateStep` resettato al restart
- Animazione pre-finale corretta (no più flash)
- `playZenSound` syntax error fissato
- Toast da 2.4s a 5s + font 13px
