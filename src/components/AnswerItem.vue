<template lang="html">
  <p v-html="answer"></p>
</template>

<script>
export default {
  name: 'answer-item',
  props: ['answer']
}
</script>

<style lang="css" scoped>
</style>
