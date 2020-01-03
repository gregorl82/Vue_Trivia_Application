<template lang="html">
  <h3>You scored {{score}} out of 10!</h3>
</template>

<script>
export default {
  name: 'result-display',
  props: ['score']
}
</script>

<style lang="css" scoped>
</style>
