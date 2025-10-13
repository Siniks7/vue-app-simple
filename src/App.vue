<!-- eslint-disable no-undef -->
<script setup>
import { provide, ref } from "vue";
import PaneRight from "./components/PaneRight.vue";

const API_ENDPOINT = "https://api.weatherapi.com/v1";

let data = ref();
let error = ref();
let activeIndex = ref(0);
let city = ref("Красноярск");
provide("city", city);

watch(city, () => {
  getCity(city.value);
});

onMounted(() => {
  getCity(city.value);
});

async function getCity(city) {
  const params = new URLSearchParams({
    q: city,
    lang: "ru",
    key: "1a8ac117722f4714875154057251409",
    days: 3,
  });
  const res = await fetch(`${API_ENDPOINT}/forecast.json?${params.toString()}`);
  if (res.status != 200) {
    error.value = await res.json();
    data.value = null;
    return;
  }
  error.value = null;
  data.value = await res.json();
}
</script>

<template>
  <main class="main">
    <div class="left"></div>
    <div class="right">
      <PaneRight
        :data
        :error
        :active-index="activeIndex"
        @select-index="(i) => (activeIndex = i)"
      />
    </div>
  </main>
</template>

<style scoped>
.main {
  display: flex;
  align-items: center;
  justify-content: center;
}
.left {
  width: 500px;
  height: 680px;
  border-radius: 30px;
  background-image: url("/bg.png");
  background-repeat: no-repeat;
  background-size: cover;
}
.right {
  background: var(--color-bg-main);
  padding: 60px 50px;
  border-radius: 0 25px 25px 0;
}
</style>