<template lang="html">
  <div>
    <div>
      <app-title :title="title"/>
      <category-selector :categories="categories"/>
    </div>
    <div v-if="questions">
      <questions-list :questions="questions"/>
      <button>Submit Answers</button>
      <button v-on:click="handleRestart">Restart Quiz</button>
    </div>
  </div>
</template>

<script>
import AppTitle from './components/AppTitle.vue';
import CategorySelector from './components/CategorySelector.vue';
import QuestionsList from './components/QuestionsList.vue'
import { eventBus } from './main.js'

export default {
  name: 'app',
  components: {
    'app-title': AppTitle,
    'category-selector': CategorySelector,
    'questions-list': QuestionsList
  },
  data(){
    return {
      title: "Qwizzr",
      categories: [],
      questions: null
    }
  },
  methods: {
    handleRestart: function(){
      this.questions = null
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
