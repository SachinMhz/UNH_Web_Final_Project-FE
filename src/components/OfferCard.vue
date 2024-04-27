<template>
  <div class="card-wrapper">
    <div class="details">
      <h3 class="offer-title">
        {{ offer.title }}
      </h3>
      <button class="btn">Shop Now</button>
    </div>
    <img class="offer-image" :src="offer.image" :alt="offer.imageText" />
  </div>
</template>
  
<script>
export default {
  name: "OfferCard",
  props: {
    offer: Object,
  },
};
</script>
  
<style scoped>
.card-wrapper {
  display: flex;
  height: 100%;
  width: 100%;
  box-shadow: 1px 1px 2px rgba(0, 0, 0, 0.4);
  border-radius: 16px;
  overflow: hidden;
  position: relative;
}

.card-wrapper:hover {
  cursor: pointer;
  box-shadow: 2px 2px 4px rgba(0, 0, 0, 0.4);
  background-color: var(--color-primary-light);
  color: black;
}

.offer-image {
  width: 100%;
  height: 100%;
  aspect-ratio: 1;
  box-shadow: 1px 1px 2px rgba(0, 0, 0, 0.4);
  object-fit: cover;
  border-radius: 12px;
  overflow: hidden;
}

.details {
  position: absolute;
  top: 0px;
  left: 0px;
  padding: 40px;
}

.offer-title {
  font-size: 1.5em;
  color: white;
  margin-bottom: 20px;
}

.btn {
  display: block;
  font-size: 16px;
  padding: 16px;
  color: black;
  box-shadow: 1px 1px 2px rgba(0, 0, 0, 0.4);
  background-color: rgba(216, 210, 210, 0.855);
  border: none;
  border-radius: 16px;
  overflow: hidden;
}

.btn:hover {
  cursor: pointer;
  box-shadow: 2px 2px 4px rgba(0, 0, 0, 0.4);
  background-color: white;
  color: black;
}

@media only screen and (max-width: 1480px) {
  .btn {
    padding: 12px;
  }

  .offer-title {
    font-size: 1.2em;
  }
}
</style>