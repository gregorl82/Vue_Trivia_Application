<template lang="html">
  <div>
    <app-title :title="title"/>
  </div>
</template>

<script>
import AppTitle from './components/AppTitle.vue'

export default {
  name: 'app',
  components: {
    'app-title': AppTitle
  },
  data(){
    return {
      title: "Quizzical"
    }
  }
}
</script>

<style lang="css" scoped>
</style>
