<template lang="html">
  <div id="results-display">
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

#results-display {
  font-size: 35px;
  font-weight: bold;
  text-align: center;
}

</style>
