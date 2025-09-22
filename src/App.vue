<script setup>
import { reactive, ref } from "vue";
import CitySelect from "./components/CitySelect.vue";
import Stat from "./components/Stat.vue";

let savedCity = ref("Moscow");
let data = reactive({
  label: "Влажность",
  stat: "90%",
});

function getCity(city) {
  savedCity.value = city;
  data.stat = "20%";
}
</script>

<template>
  <main class="main">
    <Stat v-bind="data" />
     <CitySelect @select-city="getCity" />
  </main>
</template>

<style scoped>
.main {
  background: var(--color-bg-main);
  padding: 60px 50px;
  border-radius: 25px;
}
</style>
