<script setup>
import { ref, computed } from 'vue'

const caselle = ref([
  null, null, null,
  null, null, null,
  null, null, null,
])

const giocatoreAttuale = ref('X')

const combinazioniVincenti = [
  [0, 1, 2],
  [3, 4, 5],
  [6, 7, 8],
  [0, 3, 6],
  [1, 4, 7],
  [2, 5, 8],
  [0, 4, 8],
  [2, 4, 6],
]

const vincitore = computed(() => {
  for (const [a, b, c] of combinazioniVincenti) {
    const simbolo = caselle.value[a]

    if (
      simbolo !== null &&
      simbolo === caselle.value[b] &&
      simbolo === caselle.value[c]
    ) {
      return simbolo
    }
  }

  return null
})

const pareggio = computed(() => {
  return (
    vincitore.value === null &&
    caselle.value.every((casella) => casella !== null)
  )
})

function nuovaPartita() {
  caselle.value = Array(9).fill(null)
  giocatoreAttuale.value = 'X'
}

function gioca(indice) {
  if (
  caselle.value[indice] !== null ||
  vincitore.value !== null
) {
  return
}

  caselle.value[indice] = giocatoreAttuale.value

  giocatoreAttuale.value =
    giocatoreAttuale.value === 'X' ? 'O' : 'X'
}
</script>

<template>
  <main class="gioco">
    <h1>Tris</h1>
    <p>Gioca con un amico!</p>

    <p v-if="vincitore">
    Ha vinto {{ vincitore }}!
    </p>

    <p v-else-if="pareggio">
    Pareggio!
    </p>

    <p v-else>
    Turno di: {{ giocatoreAttuale }}
    </p>

    <div class="tabellone">
      <button
        v-for="(casella, indice) in caselle"
        :key="indice"
        type="button"
        class="casella"
        :aria-label="'Casella ' + (indice + 1)"
        @click="gioca(indice)"
        :disabled="casella !== null || vincitore !== null"
      >
        {{ casella }}
      </button>
    </div>
  <button
  type="button"
  class="nuova-partita"
  @click="nuovaPartita"
  > 
  Nuova partita
  </button>
  </main>
</template>

<style scoped>
.gioco {
  max-width: 320px;
  margin: 40px auto;
  text-align: center;
  font-family: system-ui, sans-serif;
}

.tabellone {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 8px;
}

.casella {
  aspect-ratio: 1;
  border: 2px solid #334155;
  border-radius: 10px;
  background: white;
  color: #0f172a;
  font-size: 40px;
}

.nuova-partita {
  margin-top: 20px;
  padding: 12px 20px;
  border: none;
  border-radius: 8px;
  background: #334155;
  color: white;
  font: inherit;
  cursor: pointer;
}

.nuova-partita:hover {
  background: #1e293b;
}

.nuova-partita:focus-visible {
  outline: 3px solid #2563eb;
  outline-offset: 3px;
}
</style>