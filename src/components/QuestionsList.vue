<template lang="html">
  <div id="questions-list">
    <ul>
      <question-item v-for="(question, index) in formattedAnswerQuestions" :key="index" :number="index" :question="question"/>
    </ul>
  </div>
</template>

<script>
import QuestionItem from './QuestionItem.vue'
import { eventBus } from '../main.js'

export default {
  name: 'questions-list',
  props: ['questions'],
  components: {
    'question-item': QuestionItem
  },
  computed: {
    formattedAnswerQuestions: function(){
      this.questions.forEach((question) => {
        const correctAnswerObj = {};
        correctAnswerObj['text'] = question.correct_answer;
        correctAnswerObj['selected'] = false;
        question.correct_answer = correctAnswerObj;

        const incorrectAnswerArray = []
        const incorrect_answers = question.incorrect_answers;
        incorrect_answers.forEach((answer) => {
          const incorrectAnswerObj = {};
          incorrectAnswerObj['text'] = answer;
          incorrectAnswerObj['selected'] = false;
          incorrectAnswerArray.push(incorrectAnswerObj);
        })
        question.incorrect_answers = incorrectAnswerArray;
      })
      return this.questions
    }
  },
  mounted(){
    eventBus.$on('answer-clicked', (result) => {
      this.questions[result.questionIndex].incorrect_answers.forEach((answer) => {
        if(answer.text === result.answer.text){
          answer.selected = true;
        } else {
          answer.selected = false;
        }
      })
    })
  }
}
</script>

<style lang="css" scoped>

#questions-list {
  padding: 20px;
  background-color: #fff2fe;
}

</style>
