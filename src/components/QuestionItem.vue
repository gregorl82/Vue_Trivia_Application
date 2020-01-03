<template lang="html">
  <div>
    <p>Question {{questionNumber}}</p>
    <p v-html="question.question"></p>
    <ul>
      <answer-item v-for="(answer, index) in answerArray" :key="index" :answer="answer"/>
    </ul>
  </div>
</template>

<script>
import AnswerItem from './AnswerItem.vue'

export default {
  name: 'question-item',
  props: ['question', 'number'],
  components: {
    'answer-item': AnswerItem
  },
  computed: {
    questionNumber: function(){
      let questionNumber = this.number + 1;
      return questionNumber;
    },
    answerArray: function(){
      let answers = this.question.incorrect_answers;
      let index = Math.floor(Math.random() * Math.floor(3));
      answers.splice(index, 0, this.question.correct_answer);
      return answers;
    }
  }
}
</script>

<style lang="css" scoped>
</style>
