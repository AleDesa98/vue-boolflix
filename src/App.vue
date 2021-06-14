<template>
  <div id="app">
    <SearchBar @search="searchResults" />
    <Main :ricerca="text" />
  </div>
</template>

<script>
import SearchBar from './components/SearchBar.vue'
import Main from './components/Main.vue'

export default {
  name: 'App',
  data() {
    return {
      text: ""
    }
  },
  components: {
    SearchBar,
    Main
  },
  methods: {
    searchResults: function(searchText) {
      this.text = searchText
    }
  }
}
</script>

<style lang="scss">
* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}
</style>
