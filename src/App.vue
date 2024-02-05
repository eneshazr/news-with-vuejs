<template>
  <div id="app">
    <h1>HABER ARAMA MOTORU</h1>
    <search v-on:SearchRequest="handleSearch"></search>
    <div class="loading">
      <img class="" v-if="isLoading" :src="loadingImage">
    </div>
    <contents :kartlar=kartlar></contents>
  </div>
</template>
<!--  v-bind:kartlar veya :kartlar -->


<script>
  import contents from './components/contents.vue'
  import search from './components/search.vue'
  import loadingImage from './assets/katu.gif';

  export default {
    name: "app",
    components: { search, contents },
    data () {
      return {
        isLoading: true,
        kartlar: [],
        loadingImage,
      }
    },
    methods: {
      handleSearch(query) {
        if (!query) return;
        this.kartlar = [];
        this.isLoading = true
        fetch(`https://newsapi.org/v2/everything?language=tr&q=${query}&sortBy=publishedAt&apiKey=${import.meta.env.VITE_API_KEY}`)
          .then((res) => {return res.json()})
          .then((res) => {
            this.kartlar = res.articles;
            this.isLoading = false
          })
      }
    },
    created() {
      fetch(`https://newsapi.org/v2/top-headlines?country=tr&apiKey=${import.meta.env.VITE_API_KEY}`)
      .then((res) => {return res.json()})
      .then((res) => {
        this.kartlar = res.articles;
        this.isLoading = false
      })
    }
  }
</script>


<style>
h1 {
  margin-top: 55px;
  margin-bottom: 55px;
}
  .loading {
    display: flex;
    justify-content: center;
  }

  h1 {
    text-align: center;
    font-family: Impact, Haettenschweiler, 'Arial Narrow Bold', sans-serif;
  }

</style>
