<script setup>
import { inject, onMounted, ref } from "vue";
import IconLocation from "../icons/IconLocation.vue";
import Button from "./Button.vue";
import Input from "./input.vue";

const emit = defineEmits({
  selectCity(payload) {
    return payload;
  },
});

const value = inject("num");
// eslint-disable-next-line no-undef
console.log(value);

let city = ref("Красноярск");
let isEdited = ref(false);

function select() {
   isEdited.value = false;
   emit("selectCity", city.value);
}

function edit() {
  isEdited.value = true;
}

onMounted(() => {
  emit("selectCity", city.value);
});

</script>

<template>
  <div class="city-select">
    <div v-if="isEdited" class="city-input">
       <Input
        v-model="city"
        v-focus
        placeholder="Введите город"
        @keyup.enter="select()"
      />
      <Button @click="select()">Сохранить</Button>
    </div>
    <Button v-else @click="edit()">
      <IconLocation />
      Изменить город
    </Button>
  </div>
</template>

<style scoped>
.city-input {
  display: flex;
  flex-direction: column;
  gap: 10px;
  width: 100%;
}
.city-input input {
  width: 100%;
}
</style>