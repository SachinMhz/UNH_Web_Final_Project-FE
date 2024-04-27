<template>
  <Header
    bookName="Game of Thrones"
    authorName="George RR Martins"
    yourName="Write your Name"
    :searchProducts="searchProducts"
  />
  <main>
    <img
      class="spinner"
      v-if="isLoading"
      src="./assets/loader.gif"
      alt="Spinner Image"
    />
    <div v-else>
      <div class="offer-grid" v-if="!isOffersHidden">
        <div class="offer" v-for="(offer, index) in offers" :key="index">
          <OfferCard :offer="offer" />
        </div>
      </div>
      <h2 class="product-title">Products Listing</h2>

      <div class="product-grid">
        <div
          class="product"
          v-for="(product, index) in filteredProducts"
          :key="index"
        >
          <ProductCard :product="product" />
        </div>
      </div>
      <img
        v-if="filteredProducts.length == 0"
        class="no-product-image"
        src="./assets/No_Product_Found.png"
        alt="No Product Found image"
      />
    </div>
  </main>
  <Footer />
</template>

<script>
import Header from "./components/Header.vue";
import ProductCard from "./components/ProductCard.vue";
import OfferCard from "./components/OfferCard.vue";
import Footer from "./components/Footer.vue";

const BASE_URL = "https://sachin-unh-web-be.onrender.com/api";

export default {
  name: "App",
  components: {
    Header,
    ProductCard,
    OfferCard,
    Footer,
  },
  data() {
    return {
      isLoading: false,
      products: [],
      offers: [],
      filteredProducts: [],
      isOffersHidden: false,
    };
  },
  methods: {
    // Method to fetch products from the database.
    async fetchProducts() {
      const res = await fetch(`${BASE_URL}/products`);
      return await res.json();
    },
    // Method to fetch Offers from the database.
    async fetchOffers() {
      const res = await fetch(`${BASE_URL}/offers`);
      return await res.json();
    },
    searchProducts(searchText) {
      this.filteredProducts = this.products.filter((product) =>
        product.name.toLowerCase().includes(searchText.toLowerCase())
      );

      this.isOffersHidden = !!searchText; // Converting String to boolean with double bang (!!)
    },
  },
  async created() {
    this.isLoading = true;
    this.products = await this.fetchProducts();
    this.filteredProducts = this.products;

    this.offers = await this.fetchOffers();
    this.isLoading = false;
  },
};
</script>


<style >
@import url("https://fonts.googleapis.com/css2?family=Montserrat:wght@300&display=swap");
@import url("https://fonts.googleapis.com/icon?family=Material+Icons");
* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}

body {
  font-family: "Montserrat", sans-serif;
}

main {
  padding: 90px 140px;
  min-height: 80vh;
}

.product-grid {
  display: grid;
  grid-template-columns: repeat(5, 1fr);
  gap: 20px;
}

.offer-grid {
  display: grid;
  grid-template-columns: repeat(4, 1fr);
  gap: 20px;
}

.offer:nth-child(2) {
  grid-column: span 2;
  grid-row: span 2;
}
.offer:nth-child(4) {
  grid-row: span 2;
}
.offer:nth-child(5) {
  grid-row: span 2;
}

.product-title {
  font-size: 28px;
  font-weight: bolder;
  margin: 16px 0px 8px 0px;
}

.no-product-image {
  height: 300px;
  aspect-ratio: 1;
}

.spinner {
  display: block;
  width: 150px;
  aspect-ratio: 1;
  margin: 200px auto;
}

@media only screen and (max-width: 1600px) {
  main {
    padding: 90px 100px;
  }
}

@media only screen and (max-width: 1400px) {
  main {
    padding: 90px 80px;
  }

  .product-grid {
    grid-template-columns: repeat(4, 1fr);
    gap: 20px;
  }
}

@media only screen and (max-width: 1300px) {
  mains {
    padding: 90px 60px;
  }

  .offer-grid {
    grid-template-columns: repeat(3, 1fr);
  }
}

@media only screen and (max-width: 1150px) {
  .product-grid {
    grid-template-columns: repeat(3, 1fr);
  }
}

@media only screen and (max-width: 1020px) {
  .offer-grid {
    grid-template-columns: repeat(2, 1fr);
  }
  .offer:nth-child(2) {
    grid-column: span 1;
    grid-row: span 1;
  }
  .offer:nth-child(3) {
    grid-column: span 2;
    grid-row: span 2;
  }
  .offer:nth-child(4) {
    grid-row: span 1;
  }
  .offer:nth-child(5) {
    grid-row: span 1;
  }
}

@media only screen and (max-width: 900px) {
  .product-grid {
    grid-template-columns: repeat(2, 1fr);
  }
}

@media only screen and (max-width: 720px) {
  .offer-grid {
    display: none;
  }

  .product-title {
    margin-top: 0px;
  }
}
@media only screen and (max-width: 640px) {
  .product-grid {
    grid-template-columns: repeat(1, 1fr);
  }
}
</style>
