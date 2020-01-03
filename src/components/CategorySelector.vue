<template lang="html">
  <div class="">
    <label for="category-select">Pick a category: </label>
    <select v-model="categoryId" name="category-select">
      <option disabled value="">Please select one</option>
      <option v-for="category in categories" :value="category.id">{{category.name}}</option>
    </select>
    <button v-on:click="handleClick">Get Questions</button>
  </div>
</template>

<script>
import { eventBus } from '../main.js'

export default {
  name: 'category-selector',
  props: ['categories'],
  data(){
    return {
      categoryId: null,
      questions: []
    }
  },
  methods: {
    handleClick: function(){
      fetch(`https://opentdb.com/api.php?amount=10&category=${this.categoryId}&difficulty=medium&type=multiple`)
      .then(response => response.json())
      .then((data) => {
        this.questions = data.results;
        eventBus.$emit('category-selected', this.questions)
      })
    }
  }
}
</script>

<style lang="css" scoped>
</style>
