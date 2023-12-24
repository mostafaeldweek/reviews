<template>
  <Card>
    <button class="close" @click="store.deleteReview(item)">
      <i class="fa fa-times"></i>
    </button>
    <button class="edit" @click="store.editReview(item)">
      <i class="fa fa-edit"></i>
    </button>
    <div class="num-display">
      {{ item.rating }}
      
    </div>
    <div class="text-display">
      {{ item.text }}
    </div>
  </Card>
</template>

<script setup>
import { defineProps } from "vue";
import Card from "./shared/Card.vue";
import { useReviewsStore } from "../stores/reviews";

const store = useReviewsStore();
defineProps({
  item: {
    type: Object,
  },
});
</script>

<style scoped></style>
