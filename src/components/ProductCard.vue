<template>
  <div class="card-wrapper">
    <div class="img-wrapper">
      <button class="favorite" title="Add to Cart">
        <span class="material-icons"> favorite_border </span>
      </button>
      <img
        src="https://www.cnet.com/a/img/resize/9624241ec6785ab68e2092e9656bc16c73d75cb1/hub/2023/01/21/ec79d7fc-9235-4830-8fc1-77db12800b97/apple-macbook-pro-16-2023-3214.jpg?auto=webp&fit=crop&height=1200&width=1200"
        alt="Image from Google"
      />
      <button class="cart" title="Add to Cart">
        <span class="material-icons"> add_shopping_cart </span>
      </button>
    </div>
    <div class="details">
      <div class="price-wrapper">
        <p class="current-price price">$ {{ product.price }}</p>
        <p class="old-price price">$ {{ product.oldPrice }}</p>
      </div>
      <h3>
        {{ product.name }}
      </h3>

      <Reviews
        :ratings="product.ratings"
        :numberOfReviews="product.numberOfReviews"
      />
      <div class="description">
        {{ product.description }}
      </div>
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
  color: black;
}

.img-wrapper {
  position: relative;
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

.cart {
  bottom: -20px;
  padding: 12px;
  border-radius: 12px;
}

.favorite {
  top: 12px;
  border-radius: 40px;
  padding:8px;
  background-color: rgba(255, 255, 255, 0.74);
}

button {
  position: absolute;
  right: 12px;
  background-color: white;
  box-shadow: 1px 1px 2px rgba(0, 0, 0, 0.4);
  border: none;
  display: flex;
  justify-content: center;
  align-items: center;
}

button:hover {
  cursor: pointer;
  background-color: white;
  box-shadow: 2px 2px 4px rgba(0, 0, 0, 0.4);
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

.description {
  font-size: 13px;
}
</style>