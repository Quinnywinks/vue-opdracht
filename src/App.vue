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

    const people = ref([
        { name: 'Jan', age: 12 },
        { name: 'Piet', age: 20 }
    ])

    const newName = ref('')
    const newAge = ref(0)

    function addPerson() {
        people.value.push({
        name: newName.value,
        age: newAge.value
        })

        newName.value = ''
        newAge.value =  ''
    }

    const children = computed(() => {
        return people.value.filter(person => person.age < 18)
        })

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
      <button @click="toggleTask(task)">Toggle</button>
    </li>
  </ul>
  <input type="text" v-model="newName">
  <input type="number" v-model.number="newAge">
  <button @click="addPerson">Toevoegen</button>
  <ul>
  <li v-for="(person, index) in people" :key="index">
    {{ person.name }} - {{ person.age }} jaar
  </li>
</ul>
</template>