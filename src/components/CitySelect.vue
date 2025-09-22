<script setup>
import { ref } from "vue";
import IconLocation from "../icons/IconLocation.vue";
import Button from "./Button.vue";

const emit = defineEmits({
  selectCity(payload) {
    return payload;
  },
});

let isEdited = ref(false);

function select() {
   isEdited.value = false;
   emit("selectCity", "Питер");
}

function edit() {
  isEdited.value = true;
}
</script>

<template>
  <Button v-if="!isEdited" @click="edit()">
    <IconLocation />
    Изменить город
  </Button>
 <div v-if="isEdited">
    <input />
    <Button @click="select()">Сохранить</Button>
  </div>
</template>