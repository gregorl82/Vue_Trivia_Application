<template lang="html">
  <p id="answer-item" v-on:click="handleClick" v-html="answer.text"></p>
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
    }
  }
}
</script>

<style lang="css" scoped>

#answer-item {
  padding: 20px;
  background-color: white;
  border-radius: 5px;
  font-size: 20px;
}

#answer-item:hover {
  background-color: grey;
}

</style>
