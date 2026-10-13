<script setup>
const message = defineModel('message')
</script>

<template>
  <h2>Kindcomponent</h2>

  <input type="text" v-model="message">

  <p>Waarde in kind: {{ message }}</p>
</template>