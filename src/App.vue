<script setup>
import { RouterLink, RouterView } from "vue-router";
import Header from "./components/Header.vue";
import { useReviewsStore } from "./stores/reviews";
import { onMounted } from "vue";
const store=useReviewsStore()
onMounted(() => {
  store.fetchReviews();
});
</script>

<template>
  <div>
    <Header />

    <RouterView />
  </div>
</template>

<style scoped></style>
