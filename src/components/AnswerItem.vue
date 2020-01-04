<template lang="html">
  <p id="answer-item" :class="selectedClass" v-on:click="handleClick" v-html="answer.text"></p>
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
  },
  computed: {
    selectedClass: function(){
      return this.answer.selected ? "selected" : "not-selected"
    }
  }
}
</script>

<style lang="css" scoped>

.selected {
  background-color: grey;
}

.not-selected {
  background-color: white;
}

#answer-item {
  padding: 20px;
  border-radius: 5px;
  font-size: 20px;
}

#answer-item:hover {
  background-color: #ffffe6;
}

</style>
