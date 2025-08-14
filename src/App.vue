<script setup>
import CitySelect from "./components/CitySelect.vue";
import Stat from "./components/Stat.vue";
const data = {
  label: "Влажность",
  stat: "90%",
};
function getCity(city) {
  // eslint-disable-next-line no-undef
  console.log(city);
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
