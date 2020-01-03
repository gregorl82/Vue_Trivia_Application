<template lang="html">
  <div>
    <p>Question {{questionNumber}}</p>
    <p>{{question.question}}</p>
    <ul>
      <li v-for="answer in answerArray">{{answer}}</li>
    </ul>
  </div>
</template>

<script>
export default {
  name: 'question-item',
  props: ['question', 'number'],
  computed: {
    questionNumber: function(){
      let questionNumber = this.number + 1;
      return questionNumber;
    },
    answerArray: function(){
      let answers = this.question.incorrect_answers;
      let index = Math.floor(Math.random * Math.floor(3));
      answers.splice(index, 0, this.question.correct_answer);
      return answers;
    }
  }
}
</script>

<style lang="css" scoped>
</style>
