<script setup>
import {ref, onMounted, watch} from 'vue'
import {jsx} from 'vue/jsx-dev-runtime'

const name = ref('')
const input_ingr = ref('')
const input_steps = ref('')

const myIngr = ref([])
const mySteps = ref([])


//function to add ingredients
const addIngredient = () =>{
  if(input_ingr.value.trim() === '' ){
    return
  }
  myIngr.value.push({
    content: input_ingr.value
  })
  input_ingr.value = ''
  
}
const addStep = () => {
  if (input_steps.value.trim() === '') {
    return
  }
  mySteps.value.push({
    content: input_steps.value
  })
  input_steps.value = ''
}

onMounted( () => {
  myIngr.value = JSON.parse(localStorage.getItem('myIngr')) || []
  mySteps.value = JSON.parse(localStorage.getItem('mySteps')) || []
})

</script>

<template>
  <main class="app">

  <section class="greeting">
    
    <h2 class="Maintitle">
      Create Your Recipe
      Hello Chef <input type="text" placeholder="Enter your name" v-model="name">
    </h2>

  </section>

  <section class="addIngredients">
    <h3>The ingredients are the most important prerequeisite to create a perfect recipe</h3>
    <form @submit.prevent = "addIngredient" >
      <h4>Insert your ingredients</h4>
      <input type="text" placeholder="e.g., 2 Eggs, tomatos, lettuce" v-model="input_ingr"/>
      <input  type="submit" value="Add Ingredient" />
    </form>

  </section>

  <section class="addSteps">
    <h3>The Steps of the recipe are as important as the ingredients, build the rest of the recipe</h3>
    <form @submit.prevent = "addStep" >
      <h4>Write the steps for the perfect dish</h4>
      <input type="text" placeholder="e.g., Mix the eggs in a bowl" v-model="input_steps"/>
      <input type="submit" value="Add Step"/>
    </form>
  </section>

  <section class="Recipe">
  <h2>Recipe</h2>
  <h3>Ingredients</h3>
    <ul>
      <li v-for="x in myIngr" :key="index">  
      {{x.content }}
      </li>
    </ul>

    <h3>Steps</h3>
    <ul>
      <li v-for="y, in mySteps" :key="index">  
      {{y.content }}
      </li>
    </ul>

  </section>
  </main>
  </template>
  



