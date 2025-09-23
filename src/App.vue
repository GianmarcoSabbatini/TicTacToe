<template>
  <main class="card">
    <header class="header">
      <h1 class="title">Tic Tac Toe (Tris)</h1>
      <p class="subtitle">Gioca con un amico, inizia sempre la X</p>
    </header>
    <TicTacToe />
  </main>
</template>

<script setup>
import { onMounted } from 'vue'
import TicTacToe from './components/TicTacToe.vue'

onMounted(() => {
  document.title = 'Tic Tac Toe (Tris)'
})
</script>

<style scoped>
main.card {
  width: min(92vw, 520px);
  margin: 3rem auto;
  padding: 1.25rem;
  border-radius: 12px;
  background: #fff;
  box-shadow: 0 8px 24px rgba(0,0,0,0.08);
}

.header { 
  text-align: center; 
  margin-bottom: 0.75rem; 
}

.title { 
  margin: 0 0 0.25rem; 
  line-height: 1.1;
  color: #2c3e50;
}

.subtitle { 
  margin: 0; 
  color: #555; 
  font-size: 0.95rem;
}

@media (prefers-color-scheme: dark) {
  main.card {
    background: #1a1a1a;
    box-shadow: 0 8px 24px rgba(0,0,0,0.35);
  }
  
  .title { 
    color: #f8f9fa; 
  }
  
  .subtitle { 
    color: #bbb; 
  }
}
</style>
