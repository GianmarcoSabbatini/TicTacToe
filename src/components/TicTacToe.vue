<template>
  <section class="game-container">
    <div class="game-status">
      <span v-if="vinto">Vince: {{ vinto }}</span>
      <span v-else-if="pareggio">Pareggio!</span>
      <span v-else>Turno: {{ giocatoreCorrente }}</span>
    </div>

    <div class="grid">
      <button
        v-for="(cell, idx) in board"
        :key="idx"
        class="cell"
        :class="{ 
          filled: !!cell, 
          x: cell === 'X', 
          o: cell === 'O'
        }"
        :disabled="!!cell || !!vinto"
        @click="makeMove(idx)"
      >
        {{ cell }}
      </button>
    </div>

    <div class="buttons">
      <button class="btn-reset" @click="resetGame">Nuova partita</button>
    </div>
  </section>
</template>

<script setup>
import { ref, computed } from 'vue'


const board = ref(Array(9).fill(''))
const turnoX = ref(true)


const giocatoreCorrente = computed(() => turnoX.value ? 'X' : 'O')


const combinazioneVincente = [
  [0,1,2],[3,4,5],[6,7,8], // righe
  [0,3,6],[1,4,7],[2,5,8], // colonne
  [0,4,8],[2,4,6]          // diagonali
]

// Controlla vincitore
const vinto = computed(() => {
  for (const [a, b, c] of combinazioneVincente) {
    const cellValue = board.value[a]
    if (cellValue && cellValue === board.value[b] && cellValue === board.value[c]) {
      return cellValue
    }
  }
  return null
})

// Controlla pareggio
const pareggio = computed(() => !vinto.value && board.value.every(cell => cell !== ''))

// Effettua una mossa
function makeMove(cellIndex) {
  if (board.value[cellIndex] || vinto.value) return
  
  board.value[cellIndex] = giocatoreCorrente.value
  turnoX.value = !turnoX.value
}

// Reset partita
function resetGame() {
  board.value = Array(9).fill('')
  turnoX.value = true
}
</script>

<style scoped>
.game-container {
  max-width: 400px;
  margin: 0 auto;
  font-family: 'Roboto', sans-serif;
}

.game-status {
  text-align: center;
  margin-bottom: 1rem;
  font-size: 1.2rem;
  font-weight: 600;
}

.grid {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 3px;
  background: #ddd;
  padding: 3px;
  border-radius: 6px;
  margin-bottom: 1rem;
}

.cell {
  aspect-ratio: 1;
  border: none;
  background: white;
  font-size: 2rem;
  font-weight: bold;
  cursor: pointer;
  border-radius: 3px;
  transition: background 0.2s;
}

.cell:hover:not(:disabled) {
  background: #f0f0f0;
}

.cell.filled {
  cursor: default;
}

.cell.x {
  color: #007bff;
}

.cell.o {
  color: #dc3545;
}

.cell:disabled {
  cursor: not-allowed;
  opacity: 0.6;
}

.buttons {
  text-align: center;
}

.btn-reset {
  padding: 0.5rem 1rem;
  border: none;
  border-radius: 4px;
  background: #6c757d;
  color: white;
  font-weight: 600;
  cursor: pointer;
}

.btn-reset:hover {
  background: #5a6268;
}
</style>
