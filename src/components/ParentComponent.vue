<script setup>
import { ref } from 'vue'
import ChildComponent from './ChildComponent.vue'

const message = ref('Hallo vanuit de ouder')
</script>

<template>
  <h1>Oudercomponent</h1>

  <p>Waarde in ouder: {{ message }}</p>

  <ChildComponent v-model:message="message" />
</template>
