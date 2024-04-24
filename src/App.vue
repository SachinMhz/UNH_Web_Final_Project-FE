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
    //promoises
    async fetchbooks() {
      const res = await fetch("http://localhost:9523/books ");
      const data = await res.json();
      console.log(data);
      return data;
    },

    generateProducts() {
      const productTemplate = {
        id: 1,
        name: "Smartphone X",
        price: 699.99,
        ratings: 4,
        oldPrice: 799.99,
        numberOfReviews: 500,
        description:
          "This is a small description about the produt. loresm ipsum, yo tyo . Yesto usto huncha product.",
        shippingDate: "2024-04-21",
        tags: ["Electronics", "Mobile Phones", "Gadgets"],
      };

      const numberOfProducts = 10; // Change this to generate more products

      for (let i = 0; i < numberOfProducts; i++) {
        // Deep copy the product template to avoid reference issues
        const newProduct = JSON.parse(JSON.stringify(productTemplate));
        // You can modify each product here if needed
        // For example, you can change the name or price dynamically
        newProduct.name = `${productTemplate.name} ${i + 1}`;
        newProduct.id = productTemplate.id + i;
        newProduct.price += i * 10; // Example: Increment price for each product

        // Push the new product to the products array
        this.products.push(newProduct);
      }
    },

    generateOffers() {
      const productTemplate = {
        id: 1,
        title: "Find the perfect gifts for Mom",
        image: "https://calbizjournal.com/wp-content/uploads/2021/01/gift.jpg",
        imageText: "Gift for Mom",
        tags: ["Electronics", "Mobile Phones", "Gadgets"],
      };

      const numberOfProducts = 7; // Change this to generate more products

      for (let i = 0; i < numberOfProducts; i++) {
        // Deep copy the product template to avoid reference issues
        const newProduct = JSON.parse(JSON.stringify(productTemplate));
        // You can modify each product here if needed
        // For example, you can change the name or price dynamically
        newProduct.title = `${productTemplate.title} ${i + 1}`;
        newProduct.id = productTemplate.id + i;

        // Push the new product to the products array
        this.offers.push(newProduct);
      }
    },
  },
  async created() {
    // this.books = await this.fetchbooks();
    this.books = [];
    this.generateProducts();
    this.generateOffers();
  },

  // data() => this.data books
  // method => this.method => fetchbook
  // life cycle hooks created() => call our method here
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
</style>
