<template lang="html">
  <div>
    <h3>You scored {{results.correct}} out of 10!</h3>
    <p>Start a new quiz by selecting a new category above!</p>
  </div>
</template>

<script>
export default {
  name: 'result-display',
  props: ['results']
}
</script>

<style lang="css" scoped>
</style>
