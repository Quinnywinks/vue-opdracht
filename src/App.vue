<script setup>
import { ref, reactive } from 'vue'

    const clicks = ref(0)

    const person = reactive({
        firstName: '',
        country: ''
    })

    function incrementClicks() {
       clicks.value++ 
    }

    function changeCountry(newCountry) {
        person.country = newCountry
    }
</script>

<template>
  <button @click="incrementClicks">"Klik mij!"</button>
  <button @click="changeCountry('Nederland')">"Nederland"</button>
  <button @click="changeCountry('Belgie')">"Belgie"</button>
  <input type="text" v-model="person.firstName">
  <p>{{ clicks }}</p>
  <p>{{ person.firstName }}</p>
  <p>{{ person.country }}</p>
</template>