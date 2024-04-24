<template>
  <nav>
    <img src="../assets/logo.png" alt="Online Shopping Site Logo" />

    <div class="nav-item">
      <span class="material-icons"> location_on </span>
      <span class="nav-label"> Deliver to John </span>
    </div>
    <div class="nav-item search-bar"><SearchBar /></div>
    <div class="nav-item">
      <span class="material-icons"> account_circle </span>
      <span class="nav-label"> Accounts </span>
    </div>
    <div class="nav-item">
      <span class="material-icons"> swap_horiz </span>
      <span class="nav-label"> Returns & Orders </span>
    </div>
    <div class="nav-item">
      <span class="material-icons"> shopping_cart </span>
      <span class="nav-label">Cart</span>
    </div>
  </nav>
</template>

<script>
import SearchBar from "./SearchBar.vue";
export default {
  // Exporting Default Object
  name: "Header",
  components: {
    SearchBar,
  },
  props: {
    authorName: String,
    bookName: String,
    yourName: String,
  },
};
</script>

<style scoped>
nav {
  position: fixed;
  width: 100%;
  padding: 12px;
  background-color: black;
  display: flex;
  color: white;
  justify-content: space-evenly;
  align-items: center;
  z-index: 1;
}

img {
  width: 140px;
  height: 40px;
  object-fit: contain;
}

.nav-item .material-icons {
  margin-right: 4px;
}

.nav-item {
  display: flex;
  justify-content: center;
  align-items: center;
  font-size: 18px;
  font-weight: bold;
}

.nav-label:hover {
  cursor: pointer;
  text-decoration: underline;
}

.search-bar{
  flex-grow: 0.4;
}
</style>