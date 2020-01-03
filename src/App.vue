<template lang="html">
  <div>
    <app-title :title="title"/>
    <category-selector :categories="categories"/>
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
  },
  mounted(){
    fetch("https://opentdb.com/api_category.php")
    .then(response => response.json())
    .then((data) => {
      this.categories = data.trivia_categories;
    })
  }
}
</script>

<style lang="css" scoped>
</style>
