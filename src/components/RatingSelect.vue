<template>
  <ul class="rating">
    <li v-for="n in 10" :key="`rating-${n}`">
      <input
        type="radio"
        :id="`num ${n}`"
        name="rating"
        :value="n"
        :checked="selected === n"
        @change="selected = n"
      />
      <label :for="`num ${n}`">{{ n }}</label>
    </li>
  </ul>
</template>

<script setup>
import { ref, watch, defineProps, defineEmits } from "vue";

const { rating } = defineProps();
const emit = defineEmits();

const selected = ref(rating);

watch(selected, (newVal) => {
  emit("setRating", newVal);
});

watch(
  () => rating,
  (newVal) => {
    selected.value = newVal;
  }
);
</script>

<style scoped></style>

<!-- <template>
  <ul class="rating">
    <li v-for="n in 10" :key="`rating-${n}`">
      <input
        type="radio"
        :id="`num ${n}`"
        name="rating"
        :value="n"
        :checked="selected === n"
        v-model="selected"
      />
      <label :for="`num ${n}`">{{ n }}</label>
    </li>
  </ul>
</template>

<script>
export default {
  name: "RatingSelect",
  data() {
    return {
      selected: this.rating,
    };
  },
  props: {
    rating: {
      type: Number,
    },
  },
  watch: {
    selected(newVal) {
      this.$emit("setRating", newVal);
    },
    rating(newVal) {
      this.selected = newVal;
    },
  },
};
</script>

<style scoped></style> -->
