<template>
  <div class="card-wrapper">
    <div class="img-wrapper">
      <img
        src="https://www.cnet.com/a/img/resize/9624241ec6785ab68e2092e9656bc16c73d75cb1/hub/2023/01/21/ec79d7fc-9235-4830-8fc1-77db12800b97/apple-macbook-pro-16-2023-3214.jpg?auto=webp&fit=crop&height=1200&width=1200"
        alt="Image from Google"
      />
    </div>
    <div class="details">
      <div class="price-wrapper">
        <p class="current-price price">$ 19.23</p>
        <p class="old-price price">$ 24.23</p>
      </div>
      <h3>
        {{ product.name }}
      </h3>

      <Reviews
        :ratings="product.ratings"
        :numberOfReviews="product.numberOfReviews"
      />
    </div>
  </div>
</template>

<script>
import Reviews from "./Reviews.vue";

export default {
  name: "ProductCard",
  components: {
    Reviews,
  },
  props: {
    product: Object,
  },
};
</script>

<style scoped>
.card-wrapper {
  margin: auto;
  padding: 8px;
  box-shadow: 1px 1px 2px rgba(0, 0, 0, 0.4);
  border-radius: 12px;
  overflow: hidden;
}

.card-wrapper:hover {
  cursor: pointer;
  box-shadow: 2px 2px 4px rgba(0, 0, 0, 0.4);
  background-color: var(--color-primary-light);
  color: black;
}

img {
  width: 100%;
  height: 100%;
  box-shadow: 1px 1px 2px rgba(0, 0, 0, 0.4);
  object-fit: cover;
  border-radius: 12px;
  overflow: hidden;
}

.details {
  margin-top: 12px;
  padding: 0px 8px;
}

.price-wrapper {
  font-size: larger;
  display: flex;
  align-items: center;
}

h3 {
  font-size: 18px;
  margin: 4px 0px;
}

.current-price {
  font-size: 20px;
  color: green;
  margin-right: 8px;
  font-weight: bold;
  line-height: 4px;
}

.old-price {
  font-size: 16px;
  text-decoration: line-through;
}
</style>