<template>
  <div class="search-container">
    <div class="search">
    <input type="text" v-model="query" @keypress.enter="handleSearch"/>
    <button @:click="handleSearch">Search</button> 
  </div>
</div>
</template>
<!-- v-on:click yada @:click -->

<script>
  export default {
    data() {
      return {
        query: "",
      }
    },
    methods: {
      handleSearch() {
        this.$emit("SearchRequest", this.query)
      }
    }
  }
</script>

<style>
  .search-container {
    display: flex;
    justify-content: center;
  }
  .search input {
    height: 43px;
    padding: 5px;
    font-size: large;
    border-radius: 10px;
    margin-right: 5px;
  }

  .search button {
    height: 54px;
    width: 100px;
    border-radius: 10px;
    font-size: large;
    background-color: #fff;
  }

  .search button:hover {
    background-color: aliceblue;
    cursor: pointer;
  }

</style>
