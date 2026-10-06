<script setup>
import { ref, reactive, computed } from 'vue'

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

    const adults = computed(() => {
        return people.value.filter(person => person.age >= 18)
    })

    const totalPeople = computed(() => {
        return people.value.length
    })

    const numberOfChildren = computed(() => {
        return children.value.length
    })

</script>

<template>
  <button @click="incrementClicks">Klik mij!</button>
  <button @click="changeCountry('Nederland')">Nederland</button>
  <button @click="changeCountry('Belgie')">Belgie</button>
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
  
<h2>Alle personen</h2>
<ul>
  <li v-for="(person, index) in people" :key="index">
    {{ person.name }} - {{ person.age }} jaar
  </li>
</ul>

<h2>Kinderen</h2>
<ul>
  <li v-for="(child, index) in children" :key="index">
    {{ child.name }} - {{ child.age }} jaar
  </li>
</ul>

<h2>Volwassenen</h2>
<ul>
  <li v-for="(adult, index) in adults" :key="index">
    {{ adult.name }} - {{ adult.age }} jaar
  </li>
</ul>
<h2>Statistieken</h2>

<p>Totaal aantal personen: {{ totalPeople }}</p>
<p>Aantal kinderen: {{ numberOfChildren }}</p>

</template>