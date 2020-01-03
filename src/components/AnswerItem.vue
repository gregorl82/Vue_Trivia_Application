<template lang="html">
  <p v-on:click="handleClick" v-html="answer"></p>
</template>

<script>
import { eventBus } from '../main.js'

export default {
  name: 'answer-item',
  props: ['answer', 'number'],
  methods: {
    handleClick: function(){
      const result = {
        answer: this.answer,
        questionIndex: this.number
      }
      eventBus.$emit('answer-clicked', result);
      console.log(result);
    }
  }
}
</script>

<style lang="css" scoped>
</style>
