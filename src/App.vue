<template>
  <Header
    bookName="Game of Thrones"
    authorName="George RR Martins"
    yourName="Write your Name"
  />
  <main>
    <div class="offer-grid">
      <div class="offer" v-for="(offer, index) in offers" :key="index">
        <OfferCard :offer="offer" />
      </div>
    </div>
    <h2 class="product-title">Products Listing</h2>
    <div class="product-grid">
      <div class="product" v-for="(product, index) in products" :key="index">
        <ProductCard :product="product" />
      </div>
    </div>
  </main>
  <Footer />
</template>

<script>
import Header from "./components/Header.vue";
import ProductCard from "./components/ProductCard.vue";
import OfferCard from "./components/OfferCard.vue";
import Footer from "./components/Footer.vue";

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
      products: [],
      offers: [],
    };
  },
  methods: {
    // Method to fetch products from the database.
    async fetchProducts() {
      const res = await fetch("http://localhost:9523/api/products");
      return await res.json();
    },
    // Method to fetch Offers from the database.
    async fetchOfferss() {
      const res = await fetch("http://localhost:9523/api/offers");
      return await res.json();
    },
  },
  async created() {
    this.products = await this.fetchProducts();
    this.offers = await this.fetchOfferss();
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
