<script setup>
import Button from "./components/Button.vue";
import Stat from "./components/Stat.vue";
const data = {
  label: "Влажность",
  stat: "90%",
};
</script>

<template>
  <main class="main">
    <Stat v-bind="data" />
    <Button>Сохранить</Button>
  </main>
</template>

<style scoped>
.main {
  background: var(--color-bg-main);
  padding: 60px 50px;
  border-radius: 25px;
}
</style>
