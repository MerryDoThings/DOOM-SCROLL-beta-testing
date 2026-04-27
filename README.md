# DOOM/SCROLL

**DOOM/SCROLL** è un piccolo gioco web satirico sul doomscrolling: un feed infinito che ti giudica mentre continui a scorrere.

L'obiettivo non è semplicemente "vincere", ma scoprire che tipo di finale meriti: puoi raggiungere il Nirvana perdendo completamente il QI, smettere davvero, fare il quit definitivo, cadere nel Brainrot™ o salvarti comprando troppe soluzioni wellness inutili.

## Demo

Quando pubblicato con GitHub Pages, il gioco sarà disponibile a un link simile:

```text
https://TUO-USERNAME.github.io/doomscroll/
```

## Caratteristiche

- Feed satirico in stile doomscrolling
- QI che cala lentamente durante l'esposizione al feed
- Sondaggi con risposte impulsive o consapevoli
- Sponsor wellness cliccabili con effetti personalizzati
- Popup del cervello che prova a salvarti
- Brainrot progressivo con glitch e riferimenti nonsense
- 5 finali sbloccabili
- Salvataggio dei finali ottenuti tramite `localStorage`
- File HTML standalone: nessun backend, nessuna installazione, nessuna dipendenza esterna

## Finali

1. **Nirvana** — perdi tutto il QI e raggiungi una falsa pace zen.
2. **Smetti davvero** — ascolti il cervello e chiudi il feed.
3. **Quit Definitivo** — usi bene pochi aiuti, ascolti il cervello e cambi davvero rapporto col feed.
4. **Brainrot™** — clicchi in modo compulsivo finché il linguaggio collassa.
5. **Capitalismo Spirituale** — provi a salvarti cliccando troppi sponsor wellness.

## Come pubblicarlo con GitHub Pages

### 1. Crea una repository

Vai su GitHub e crea una nuova repository pubblica, ad esempio:

```text
doomscroll
```

### 2. Carica i file

Carica nella repository questi file:

```text
index.html
README.md
```

Il file principale deve chiamarsi **index.html**, altrimenti GitHub Pages potrebbe non aprirlo automaticamente.

### 3. Attiva GitHub Pages

Nella repository:

1. Vai su **Settings**
2. Vai su **Pages**
3. In **Build and deployment**, scegli:
   - **Source:** Deploy from a branch
   - **Branch:** main
   - **Folder:** /root
4. Salva

Dopo qualche minuto GitHub mostrerà il link pubblico del sito.

## Sviluppo locale

Puoi aprire direttamente `index.html` nel browser.

In alternativa, puoi avviare un piccolo server locale:

```bash
python3 -m http.server 8000
```

Poi apri:

```text
http://localhost:8000
```

## Note

Il gioco è volutamente cinico, ma non vuole insultare chi ha problemi reali con il doomscrolling. L'idea è trasformare una cattiva abitudine in qualcosa di visibile, giocabile e un po' ridicolo.

## Licenza

Progetto personale/sperimentale. Puoi modificarlo, condividerlo e migliorarlo.
