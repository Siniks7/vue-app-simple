<script setup>
import { onMounted, ref } from "vue";
import IconLocation from "../icons/IconLocation.vue";
import Button from "./Button.vue";
import Input from "./input.vue";

const emit = defineEmits({
  selectCity(payload) {
    return payload;
  },
});

let city = ref("Moscow");
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