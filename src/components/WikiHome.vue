<template>
    <!-- add a search box in the middle-->
    <div class="search-box">
        <input type="text" placeholder="Search" v-model="searchTerm" />
    </div>
    <!-- add a search button-->
    <div class="search-button">
        <button @click="search">Search</button>
    </div>
</template>

<script>
export default {
    name: "WikiHome",
    data() {
        return {
            searchTerm: ""
        };
    },
    methods: {
        search() {
            //route to the search page
            this.$router.push({ name: "Search", params: { searchTerm: this.searchTerm } });
        }
    }
};

</script>