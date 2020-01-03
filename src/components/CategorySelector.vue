<template lang="html">
  <div class="">
    <label for="category-select">Pick a category: </label>
    <select v-model="categoryId" name="category-select">
      <option disabled value="">Please select one</option>
      <option v-for="category in categories" :value="category.id">{{category.name}}</option>
    </select>
    <label for="difficulty-select">Select difficulty: </label>
    <select v-model="difficulty" name="difficulty-select">
      <option value="easy">Easy</option>
      <option value="medium">Medium</option>
      <option value="hard">Hard</option>
    </select>
    <button v-on:click="handleClick">Start Quiz</button>
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
      difficulty: null,
      questions: []
    }
  },
  methods: {
    handleClick: function(){
      fetch(`https://opentdb.com/api.php?amount=10&category=${this.categoryId}&difficulty=${this.difficulty}&type=multiple`)
      .then(response => response.json())
      .then((data) => {
        data.results.forEach((item) => {
          item['selectedAnswer'] = null;
        })
        this.questions = data.results;
        eventBus.$emit('category-selected', this.questions)
      })
    }
  }
}
</script>

<style lang="css" scoped>
</style>
