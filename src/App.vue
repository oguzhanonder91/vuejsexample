<script>
  import Search from './components/Search';
  import Preview from './components/Preview';

  export default {
    name: 'App',
    components: { Search, Preview },
    data() {
      return {
        gifts: [],
        isLoading: true,
      };
    },
    methods: {
      doQuery(url) {
        fetch(url)
          .then(res => res.json())
          .then((res) => {
            this.gifts = res.data;
            this.isLoading = false;
          });
      },
      handleSearch(query) {
        this.gifts = [];
        this.isLoading = true;
        const searchUrl = `http://api.giphy.com/v1/gifs/search?q=${query}&api_key=xzrulhqHRMjIE2fqaeVHwimLhe8FM5EE`;
        this.doQuery(searchUrl);
      },
    },
    created() {
      const url = 'http://api.giphy.com/v1/gifs/trending?api_key=xzrulhqHRMjIE2fqaeVHwimLhe8FM5EE';
      this.doQuery(url);
    },


  };
</script>

<template>
  <div id="app">
    <Search v-on:SearchRequested="handleSearch"></Search>
    <p v-if="isLoading">Loading</p>
    <Preview :gifts=gifts></Preview>
  </div>
</template>

<style>
  #app {
    font-family: 'Avenir', Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
  }
</style>
