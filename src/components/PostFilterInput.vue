<script setup>
const model = defineModel();
defineProps({
  placeholder: {
    type: String,
  },
});
</script>

<template>
  <input type="text" v-model="model" class="input" :placeholder="placeholder" />
</template>

<style scoped>
.input {
  width: 100%;
  padding: 8px;
}
</style>
