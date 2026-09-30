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

    const tasks = ref([
        {name: 'Boodschappen doen', completed: false},
        {name: 'Afwassen', completed: true},
        {name: 'Hond uitlaten', completed: false}
    ])

    function toggleTask(task) {
        task.completed = !task.completed
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
  <ul>
    <li v-for="(task, index) in tasks" :key="index">
      {{ task.name }}
      {{ task.completed ? '(voltooid)' : '(niet voltooid)' }}
    </li>
  </ul>
</template>