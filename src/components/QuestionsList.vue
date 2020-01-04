<template lang="html">
  <div id="questions-list">
    <ul>
      <question-item v-for="(question, index) in questions" :key="index" :number="index" :question="question"/>
    </ul>
  </div>
</template>

<script>
import QuestionItem from './QuestionItem.vue'

export default {
  name: 'questions-list',
  props: ['questions'],
  components: {
    'question-item': QuestionItem
  }
}
</script>

<style lang="css" scoped>

#questions-list {
  padding: 20px;
  background-color: #fff2fe;
}

</style>
