<template>
  <div class="card" :class="{ reverse: reverseValue }">
    <slot />
  </div>
</template>

<script setup>
import { defineProps } from "vue";

const { reverse } = defineProps();
const reverseValue = reverse;
</script>

<style scoped>
.card {
  background: #fff;
  color: #212121;
}
.card.reverse {
  background: #212121;
  color: #fff;
}
</style>
