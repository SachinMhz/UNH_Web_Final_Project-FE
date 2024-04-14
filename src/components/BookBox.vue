<template>
  <div v-for="book of books" :key="book.id">
    <SingleBook :book="book" />
  </div>
</template>

<script>
import SingleBook from "./SingleBook.vue";

export default {
  name: "BookBox",
  props: {
    books: Array,
  },
  components: {
    SingleBook,
  },
};

// if ((req = "localhost:/")) send("html", "CSS");
// else if ((req = "localhost:/api")) send("db.json");
// else send("404");
</script>
<style scoped>
</style>

