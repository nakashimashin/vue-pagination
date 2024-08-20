<script setup>
import { ref } from 'vue'

const page = ref(1)
</script>

<template>
  <main>
    <v-pagination
      :length="4"
      active-color="red"
    ></v-pagination>
  </main>
</template>

<style scoped>
</style>