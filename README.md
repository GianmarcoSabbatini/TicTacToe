# Tic Tac Toe

Un semplice gioco di Tic Tac Toe (Tris) sviluppato con Vue 3 e Vite.

## Come funziona

- Griglia 3x3 interattiva
- X inizia sempre per primo
- I giocatori si alternano cliccando sulle celle
- Vince chi fa tre simboli in fila (orizzontale, verticale o diagonale)
- Reset per iniziare una nuova partita

## Requisiti

- Node.js 16 o superiore
- npm

## Installazione e avvio

```bash
# Installa le dipendenze
npm install

# Avvia il server di sviluppo
npm run dev
```

Apri il browser su `http://localhost:5173`

## Build per produzione

```bash
npm run build
npm run preview
```

## Tecnologie

- Vue 3 (Composition API)
- Vite
- CSS3

## Requisiti
- Node.js 18+
- npm 9+

## Avvio in sviluppo (PowerShell)
```powershell
npm install
npm run dev
```
Apri l'URL mostrato in console (tipicamente `http://localhost:5173`).

## Build produzione
```powershell
npm run build
npm run preview
```

## Funzionalità
- Griglia 3x3 interattiva
- Alternanza turni X/O
- Blocco celle già giocate
- Rilevazione vincitore e pareggio
- Reset partita

Struttura principale:
- `src/components/TicTacToe.vue` – logica e UI del gioco
- `src/App.vue` – shell applicativa
- `src/main.js` – bootstrapping Vue

