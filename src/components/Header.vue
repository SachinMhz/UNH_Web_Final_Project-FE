<template>
  <nav>
    <div class="nav-menu">
      <img
        class="logo"
        src="../assets/logo.png"
        alt="Online Shopping Site Logo"
      />

      <div class="nav-item">
        <span class="material-icons"> location_on </span>
        <span class="nav-label"> Deliver to John </span>
      </div>
      <div class="nav-item search-bar">
        <SearchBar :searchProducts="searchProducts" />
      </div>
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

      <div class="mobile-nav" @click="toggleMenu">
        <span class="material-icons"> menu </span>
      </div>
    </div>
    <div class="maximized-nav">
      <div class="maximized-nav-item">
        <span class="material-icons"> location_on </span>
        <span class="nav-label"> Deliver to John </span>
      </div>
      <div class="maximized-nav-item">
        <span class="material-icons"> account_circle </span>
        <span class="nav-label"> Accounts </span>
      </div>
      <div class="maximized-nav-item">
        <span class="material-icons"> swap_horiz </span>
        <span class="nav-label"> Returns & Orders </span>
      </div>
      <div class="maximized-nav-item">
        <span class="material-icons"> shopping_cart </span>
        <span class="nav-label">Cart</span>
      </div>
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
    searchProducts: Function,
  },
  methods: {
    toggleMenu() {
      let navList = document.querySelector(".maximized-nav");
      console.log("clicked");
      if (navList.className === "maximized-nav") {
        navList.className += " display-flex";
      } else {
        navList.className = "maximized-nav";
      }
    },
  },
};
</script>

<style scoped>
nav {
  position: fixed;
  width: 100%;
  z-index: 1;
}
.nav-menu {
  padding: 12px;
  background-color: black;
  display: flex;
  color: white;
  justify-content: space-evenly;
  align-items: center;
}

.maximized-nav {
  display: none;
  background-color: black;
  flex-direction: column;
  color: white;
  text-align: center;
}
.maximized-nav-item {
  display: flex;
  width: 200px;
  margin: 8px auto;
}

.logo {
  width: 140px;
  height: 40px;
  object-fit: contain;
}

.material-icons {
  margin-right: 6px;
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

.search-bar {
  flex-grow: 0.4;
}

.mobile-nav {
  display: none;
  justify-content: center;
  align-items: center;
  color: rgba(238, 243, 243, 0.768);
}

.mobile-nav:hover {
  cursor: pointer;
  color: white;
}

@media only screen and (max-width: 1150px) {
  .nav-item {
    display: none;
  }

  .nav-item.search-bar {
    display: block;
  }

  .mobile-nav {
    display: block;
  }

  .maximized-nav.display-flex {
    display: flex;
  }
}

@media only screen and (max-width: 700px) {
  .logo {
    width: 100px;
    height: 30px;
  }
}
</style>