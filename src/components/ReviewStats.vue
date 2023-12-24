<template>
  <div class="feedback-stats">
    <h4>{{ store.reviewsCount ? store.reviewsCount : "" }}</h4>
    <h4>
      Avarage Rating{{ isNaN(store.avarageRating) ? 0 : store.avarageRating }}
    </h4>
  </div>
</template>

<script setup>
import { useReviewsStore } from "../stores/reviews";

const store = useReviewsStore();
</script>

<style scoped></style>
