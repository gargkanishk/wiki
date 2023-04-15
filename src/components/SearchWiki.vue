<template>
    <div>
      <form @submit.prevent="searchWikipedia">
        <input type="text" v-model="searchQuery" />
        <button type="submit">Search</button>
      </form>
  
      <ul>
        <li v-for="result in searchResults" :key="result.pageid">
          <a :href="'https://en.wikipedia.org/wiki/' + result.title" target="_blank">{{ result.title }}</a>
          <p>{{ result.snippet }}</p>
        </li>
      </ul>
    </div>
  </template>

<script>
export default {
  name: "SearchWiki",
  data() {
    return {
      searchQuery: "",
      searchResults: []
    };
  },
    created() {
        this.searchQuery = this.$route.params.searchTerm;
        this.searchWikipedia();
    },
  methods: {
    searchWikipedia() {
      fetch(
        `https://en.wikipedia.org/w/api.php?action=query&list=search&origin=*&format=json&srsearch=${this.searchQuery}`
      )
        .then(response => response.json())
        .then(data => {
          this.searchResults = data.query.search;
        });
    }
  }
};
</script>