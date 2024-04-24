<template>
  <div class="search-bar">
    <input
      class="search-input"
      type="text"
      v-model="serachText"
      placeholder="Search..."
      @keyup.enter="search"
    />
    <div class="search-icon">
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
  methods: {
    search() {
      console.log("Searching for:", this.searchText);
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
  background-color: #9fa8ed;
}
</style>