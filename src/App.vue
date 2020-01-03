<template lang="html">
  <div>
    <app-title :title="title"/>
    <category-selector />
  </div>
</template>

<script>
import AppTitle from './components/AppTitle.vue';
import CategorySelector from './components/CategorySelector';

export default {
  name: 'app',
  components: {
    'app-title': AppTitle,
    'category-selector': CategorySelector
  },
  data(){
    return {
      title: "Quizzical",
      categories: []
    }
  }
}
</script>

<style lang="css" scoped>
</style>
