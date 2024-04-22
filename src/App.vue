<template>
  <div>
    <Header
      bookName="Game of Thrones"
      authorName="George RR Martins"
      yourName="Write your Name"
    />
    <div class="product-grid">
      <div
        class="product-wrapper"
        v-for="(product, index) in products"
        :key="index"
      >
        <ProductCard :product="product" />
      </div>
    </div>
  </div>
</template>

<script>
import Header from "./components/Header.vue";
import ProductCard from "./components/ProductCard.vue";

export default {
  name: "App",
  components: {
    Header,
    ProductCard,
  },
  data() {
    return {
      books: [],
      products: [],
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
        shippingDate: "2024-04-21",
        tags: ["Electronics", "Mobile Phones", "Gadgets"],
      };

      const numberOfProducts = 20; // Change this to generate more products

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
  },
  async created() {
    // this.books = await this.fetchbooks();
    this.books = [];
    this.generateProducts();
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

.product-grid {
  display: grid;
  grid-template-columns: repeat(5, 1fr);
  gap: 20px;
}
</style>
