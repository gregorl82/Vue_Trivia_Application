<template lang="html">
  <div>
    <h3>You scored {{results.correct}} out of 10!</h3>
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
