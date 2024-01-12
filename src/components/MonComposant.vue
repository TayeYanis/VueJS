<template>
  <div class="app-container">
    <h2>Compteur</h2>
    <p>La valeur de count est : {{ count }}</p>
    <button @click="increment">Incrémenter</button>
    <button @click="decrement">Décrémenter</button>

    <h2>Calculatrice</h2>
    <div class="calculator-inputs">
      <input v-model="num1" type="number" placeholder="Entrez le premier nombre" />
      <input v-model="num2" type="number" placeholder="Entrez le deuxième nombre" />
    </div>
    <div class="calculator-buttons">
      <button @click="add">Additionner</button>
      <button @click="subtract">Soustraire</button>
      <button @click="multiply">Multiplier</button>
      <button @click="divide">Diviser</button>
    </div>
    <p>Résultat : {{ result }}</p>

    <h2>Changer la taille de la police</h2>
    <div class="font-size-buttons">
      <button @click="changeFontSize('increase')">Augmenter la taille</button>
      <button @click="changeFontSize('decrease')">Diminuer la taille</button>
    </div>
    <p :style="{ fontSize: fontSize + 'px' }">Ce texte a une taille de police de {{ fontSize }}px.</p>
  </div>
</template>

<script setup>
import { ref } from 'vue'

const count = ref(0)
function increment() {
  count.value++
}
function decrement() {
  count.value--
}

const num1 = ref(0)
const num2 = ref(0)
const result = ref(0)

function add() {
  result.value = num1.value + num2.value
}
function subtract() {
  result.value = num1.value - num2.value
}
function multiply() {
  result.value = num1.value * num2.value
}
function divide() {
  if (num2.value !== 0) {
    result.value = num1.value / num2.value
  } else {
    alert('Division par zéro impossible!')
  }
}

const fontSize = ref(16)
function changeFontSize(action) {
  if (action === 'increase') {
    fontSize.value += 2
  } else if (action === 'decrease') {
    fontSize.value -= 2
  }
}
</script>
<style>
  img {
    width: 5%;
  }


  .app-container {
    max-width: 600px;
    margin: 0 auto;
    font-family: 'Arial', sans-serif;
  }

  h2 {
    color: #333;
  }

  button {
    background-color: #3498db;
    color: #fff;
    padding: 8px 12px;
    margin: 4px;
    cursor: pointer;
    border: none;
    border-radius: 4px;
  }

  button:hover {
    background-color: #2073b1;
  }

  .calculator-inputs {
    margin-bottom: 10px;
  }

  .calculator-buttons {
    display: flex;
    justify-content: space-between;
    margin-bottom: 10px;
  }

  .font-size-buttons button {
    margin-right: 10px;
  }
</style>
