<template lang="html">
  <div>
    <app-title :title="title"/>
    <category-selector :categories="categories"/>
  </div>
</template>

<script>
import AppTitle from './components/AppTitle.vue';
import CategorySelector from './components/CategorySelector';
import { eventBus } from './main.js'

export default {
  name: 'app',
  components: {
    'app-title': AppTitle,
    'category-selector': CategorySelector
  },
  data(){
    return {
      title: "Quizzical",
      categories: [],
      questions: []
    }
  },
  mounted(){
    fetch("https://opentdb.com/api_category.php")
    .then(response => response.json())
    .then((data) => {
      this.categories = data.trivia_categories;
    })

    eventBus.$on('category-selected', (questions) => {
      this.questions = questions
    })
  }
}
</script>

<style lang="css" scoped>
</style>
