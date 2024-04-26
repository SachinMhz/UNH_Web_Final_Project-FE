<template>
  <div class="search-bar">
    <input
      class="search-input"
      type="text"
      v-model="searchText"
      placeholder="Search..."
      @keyup.enter="handleSearch"
    />
    <div class="search-icon" @click="handleSearch">
      <span class="material-icons"> search </span>
    </div>
  </div>
</template>
    
    <script>
export default {
  name: "SearchBar",
  data() {
    return {
      searchText: "",
    };
  },
  props: {
    searchProducts: Function,
  },
  methods: {
    handleSearch() {
      this.searchProducts(this.searchText);
    },
  },
};
</script>
    
<style scoped>
.search-bar {
  display: flex;
  width: 100%;
  border-radius: 24px;
  overflow: hidden;
}
.search-input {
  flex: 1;
  padding-left: 12px;
}
.search-icon {
  padding: 12px 16px;
  display: flex;
  justify-content: center;
  align-items: center;
  background-color: #9fa8edd6;
}
.search-icon:hover{
  cursor: pointer;
  background-color: #9fa8ed;
}

@media only screen and (max-width: 700px) {
  .search-icon {
    padding: 6px 8px;
  }
}
</style>