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
      <input  type="submit" value="Add Ingredient" @click.prevent="addIngredient"/>
    </form>

  </section>

  <section class="addSteps">
    <h3>The Steps of the recipe are as important as the ingredients, build the rest of the recipe</h3>
    <form @submit.prevent = "addStep" >
      <h4>Write the steps for the perfect dish</h4>
      <input type="text" placeholder="e.g., Mix the eggs in a bowl" v-model="input_steps"/>
      <input type="submit" value="Add Step" @click.prevent="addStep"/>
    </form>
  </section>

  <section class="Recipe">
  <h3>Recipe</h3>
  <h2>ingredients</h2>
    <ul>
      <li v-for="(ing, index) in myIngr" :key="index">  
      {{ingr.content }}
      </li>
    </ul>

    <h2>Steps</h2>
    <ul>
      <li v-for="(step, index) in mySteps" :key="index">  
      {{ingr.content }}
      </li>
    </ul>
    
  </section>
  </main>
  </template>
  



