<template lang="html">
  <div>
    <ul>
      <question-item v-for="(question, index) in questions" :key="index" :question="question"/>
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
</style>
