<template lang="html">
  <div id="app-title">
    <h1>{{title}}</h1>
  </div>
</template>

<script>
export default {
  name: 'app-title',
  props: ['title']
}
</script>

<style lang="css" scoped>

#app-title {
  font-family: 'Fugaz One', cursive;
  padding-top: 10px;
  font-size: 50px;
  text-align: center;
}

</style>
