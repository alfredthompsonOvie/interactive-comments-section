<template>
  <section 
  class="commentsContainer"
  v-for="comment in comments"
  :key="comment.id"
  >
    <BaseComments
      :comment="comment"
    />
  </section>
	<div>
		<BaseDelete v-if="showModal" :show-modal="showModal" />
	</div>
</template>

<script setup>
import { computed, ref } from "vue";
import BaseDelete from "./components/BaseDelete.vue";
import BaseComments from "./components/comments/BaseComments.vue";
import data from "./data/data.json";

// console.log(data);
console.log(data.comments);

const comments = computed(() => data.comments);

const showModal = ref(false);
</script>

<style lang="scss" scoped></style>
