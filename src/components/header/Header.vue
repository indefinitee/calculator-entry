<script setup>
const emits = defineEmits(['newCalc'])

const addCalc = () => {
  emits('newCalc')
}
</script>

<template>
  <header class="header">
    <div class="container">
      <h1 class="header__title">Пожтехкабель</h1>
      <button @click="addCalc" class="btn header__btn">Новый расчет</button>
    </div>
  </header>
</template>
