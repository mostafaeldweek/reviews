<template>
  <Card>
    <form @submit.prevent="handleSubmit">
      <h2>How would you rate this service</h2>
      <!-- Rating -->

      <RatingSelect :rating="rating" @setRating="setRating" />

      <div class="input-group">
        <input type="text" placeholder="ririri" v-model="text" />
        <button type="submit" class="btn btn-primary" :disabled="btnDisabled">
          Add
        </button>
      </div>
      <div class="message" v-if="message != ''">{{ message }}</div>
    </form>
  </Card>
</template>

<script setup>
import { ref, watch } from "vue";
import Card from "../components/shared/Card.vue";
import RatingSelect from "./RatingSelect.vue";
import { useReviewsStore } from "../stores/reviews";
import { storeToRefs } from "pinia";

const store = useReviewsStore();
const text = ref("");
const btnDisabled = ref(false);
const message = ref("");
const rating = ref(10);

const { editedContent } = storeToRefs(store);

watch(editedContent, (newData) => {
  if (newData.editable) {
    text.value = newData.item.text;
    rating.value = newData.item.rating;
  }
});
watch(text, (newVal) => {
  if (newVal.trim().length <= 10) {
    btnDisabled.value = true;
    message.value = "text must be more than 10 char";
  } else {
    btnDisabled.value = false;
    message.value = "";
  }
});
const handleSubmit = () => {
  const newReview = {
    text: text.value,
    rating: rating.value,
  };
  if (!store.editedContent.editable) {
    store.addReview(newReview);
  } else {
    store.updateReview({
      ...newReview,
      id: store.editedContent.item.id,
    });
  }
};

const setRating = (val) => {
  rating.value = val;
  console.log(val);
};
</script>

<style lang="scss" scoped></style>
