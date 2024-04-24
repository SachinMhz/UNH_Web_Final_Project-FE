<template>
  <div class="review-row">
    <span v-for="(_, index) in maxStars" :key="index">
      <span v-if="index < ratings" class="material-icons"> star </span>
      <span v-else class="material-icons"> star_border </span>
    </span>
    <span class="reviews-number">{{ numberOfReviews }}</span>
  </div>
</template>

<script>
export default {
  name: "Reviews",
  props: {
    ratings: Number,
    numberOfReviews: Number,
  },
  data() {
    return {
      maxStars: [1, 2, 3, 4, 5],
    };
  },
};
</script>

<style scoped>
.review-row {
  display: flex;
  align-items: center;
}

.reviews-number{
  margin-left: 4px;
}
</style>
