<template lang="html">
  <div>
    <div>
      <app-title :title="title"/>
      <category-selector :categories="categories"/>
    </div>
    <div v-if="questions">
      <questions-list :questions="questions"/>
      <button v-on:click="handleSubmit">Submit Answers</button>
      <button v-on:click="handleRestart">New Questions</button>
    </div>
    <div v-if="results.correct">
      <result-display :results="results"/>
      <button v-on:click="handleRestart">Start Again</button>
    </div>
  </div>
</template>

<script>
import AppTitle from './components/AppTitle.vue';
import CategorySelector from './components/CategorySelector.vue';
import QuestionsList from './components/QuestionsList.vue';
import ResultDisplay from './components/ResultDisplay.vue';
import { eventBus } from './main.js';

export default {
  name: 'app',
  components: {
    'app-title': AppTitle,
    'category-selector': CategorySelector,
    'questions-list': QuestionsList,
    'result-display': ResultDisplay
  },
  data(){
    return {
      title: "Qwizzr",
      categories: [],
      questions: null,
      results: {
        correct: null,
        incorrect: null
      }
    }
  },
  methods: {
    handleSubmit: function(){
      this.results.correct = 0;
      this.results.incorrect = 0;
      this.questions.forEach((question) => {
        if (question.correct_answer === question.selectedAnswer){
          this.results.correct += 1;
        } else {
          this.results.incorrect += 1;
        }
      });
      this.questions = null;
    },
    handleRestart: function(){
      this.questions = null,
      this.results = {
        correct: null,
        incorrect: null
      }
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

    eventBus.$on('answer-clicked', (answer) => {
      this.questions[answer.questionIndex].selectedAnswer = answer.answer
    })
  }
}
</script>

<style lang="css" scoped>
</style>
