<template lang="html">
  <div id="question-item">
    <p class="question-title">Question {{questionNumber}}</p>
    <p v-html="question.question"></p>
    <ul>
      <answer-item v-for="(answer, index) in answerArray" :key="index" :answer="answer" :number="number"/>
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
      let answerObjects = []
      answers.forEach((answer) => {
        let obj = {};
        obj['answer'] = answer;
        obj['selected'] = false;
        answerObjects.push(obj);
      })
      return answerObjects;
    }
  }
}
</script>

<style lang="css" scoped>

.question-title {
  font-family: 'Fugaz One', cursive;
  font-variant: small-caps;
  font-weight: bold;
  font-size: 28px;
}

#question-item {
  padding: 20px;
  font-size: 24px;
}

</style>
