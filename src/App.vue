<script setup>
import { ref } from "vue";
import Calc from "./components/calc-section/Calc.vue";
import Header from "./components/header/Header.vue";
import ResultSidebar from "./components/result-sidebar/ResultSidebar.vue";

const calculators = ref([{ id: 1 }, { id: 2 }]);

let nextId = 3;

const removeCalc = (id) => {
  calculators.value = calculators.value.filter((calc) => calc.id !== id);

  const lastItem = calculators.value[calculators.value.length - 1];

  if (calculators.value.length === 0) {
    nextId = 1;
    return;
  }

  nextId = lastItem.id + 1;
};

const addCalc = () => {
  calculators.value.push({ id: nextId++ });
};
</script>

<template>
  <div class="container">
    <Header @newCalc="addCalc" />

    <div class="wrapper relative">
      <div class="flex flex-col gap-4">
        <Calc
          v-for="item in calculators"
          :key="item.id"
          :id="item.id"
          :title="'Линия #' + item.id"
          @removeCalculator="removeCalc"
        />
      </div>
      <ResultSidebar />
    </div>
  </div>
</template>

<style lang="scss">
@import "./styles/index.scss";
</style>
