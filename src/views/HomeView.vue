<script setup>
import ReviewsForm from "@/components/ReviewsForm.vue";
import ReviewStats from "@/components/ReviewStats.vue";
import ReviewList from "@/components/ReviewList.vue";
</script>

<template>
  <div class="home">
    <div class="container">
      <!-- reviews-form -->
      <ReviewsForm />
      <!-- reviews-stats -->
      <ReviewStats />
      <!-- reviews-List1 -->
      <ReviewList />
    </div>
  </div>
</template>
