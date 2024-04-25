<template>
  <div class="card-wrapper">
    <div class="img-wrapper">
      <button class="favorite btn" title="Favorite Item">
        <span class="material-icons"> favorite_border </span>
      </button>
      <img
        class="product-img"
        :src="product.image"
        :alt="product.imageText"
      />
      <button class="cart btn" title="Add to Cart">
        <span class="material-icons"> add_shopping_cart </span>
      </button>
    </div>
    <div class="details">
      <div class="price-wrapper">
        <p class="current-price price">$ {{ product.price }}</p>
        <p class="old-price price">$ {{ product.oldPrice }}</p>
      </div>
      <h3 class="title">
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
  height: 100%;
}

.card-wrapper:hover {
  cursor: pointer;
  box-shadow: 2px 2px 4px rgba(0, 0, 0, 0.4);
  color: black;
}

.img-wrapper {
  position: relative;
}

.product-img {
  width: 100%;
  height: 100%;
  box-shadow: 1px 1px 2px rgba(0, 0, 0, 0.4);
  object-fit: cover;
  border-radius: 12px;
  aspect-ratio: 1;
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

.title {
  font-size: 18px;
  margin: 4px 0px;
  font-weight: bold;
}

.cart {
  bottom: -20px;
  padding: 12px;
  border-radius: 12px;
  background-color: rgba(255, 255, 255, 0.86);
}

.favorite {
  top: 12px;
  border-radius: 40px;
  padding: 8px;
  background-color: rgba(255, 255, 255, 0.74);
}

.btn {
  position: absolute;
  right: 12px;
  box-shadow: 1px 1px 2px rgba(0, 0, 0, 0.4);
  border: none;
  display: flex;
  justify-content: center;
  align-items: center;
}

.btn:hover {
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
  font-size: 14px;
}
</style>