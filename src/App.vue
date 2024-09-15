<script setup>
import {ref} from 'vue'

const name = ref('')

const addIngredient = () =>{
  if(input_ingr.value.trim() === '' ){
    return
  }

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
    </form>

  </section>

  <section class="addSteps">
    <h3>The Steps of the recipe are as important as the ingredients, build the rest of the recipe</h3>
    <form @submit.prevent = "addStep" >
      <h4>Write the steps for the perfect dish</h4>
      <input type="text" placeholder="e.g., Mix the eggs in a bowl" v-model="input_steps"/>
    </form>

  </section>

  </main>
</template>

<style scoped>


</style>
