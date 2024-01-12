<template>
  <div>
    <h2>Compteur</h2>
    <p>La valeur de count est : {{ count }}</p>
    <button @click="increment">Incrémenter</button>
    <button @click="decrement">Décrémenter</button>

    <h2>Calculatrice</h2>
    <input v-model="num1" type="number" placeholder="Entrez le premier nombre" />
    <input v-model="num2" type="number" placeholder="Entrez le deuxième nombre" />
    <button @click="add">Additionner</button>
    <button @click="subtract">Soustraire</button>
    <button @click="multiply">Multiplier</button>
    <button @click="divide">Diviser</button>
    <p>Résultat : {{ result }}</p>

    <h2>Changer la taille de la police</h2>
    <button @click="changeFontSize('increase')">Augmenter la taille</button>
    <button @click="changeFontSize('decrease')">Diminuer la taille</button>
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
</style>
