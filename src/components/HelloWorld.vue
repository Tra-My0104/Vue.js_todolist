<script setup>
import { ref, defineProps } from "vue";

defineProps({
  msg: String,
});

const hello = ref("");
const randomNumber = ref(Math.random()*1000);
const count = ref(0);
</script>

<template>
  <div>
    {{ hello }}
    <input type="text" v-model="hello" />
    <button @click="count++">Số đếm {{ count }}</button>
    <div v-if="randomNumber > 0.5">Tài {{ randomNumber }}</div>
    <div v-else>Xỉu {{ randomNumber }}</div>
    <button @click="randomNumber">Nhấn</button>
  </div>
</template>

<style scoped>
button {
  color: brown;
  border: 1px solid black;
}
</style>
