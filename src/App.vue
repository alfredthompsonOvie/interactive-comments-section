<template>
  <BaseComments />
	<!-- <section
		class="commentsContainer"
		v-for="comment in comments"
		:key="comment.id"
	>

		<BaseComment :comment="comment" />

		<section class="replyContainer">
			<template v-for="reply in comment.replies" :key="reply.id">
				<BaseComment :comment="reply" />
			</template>
		</section>
		
		<section class="textArea">
			<form>
				<section class="form__control">
					<label for="addComment"></label>
					<textarea
						name="addComment"
						id="addComment"
						cols="30"
						rows="10"
						placeholder="Add a comment..."
					></textarea>
				</section>
				<img :src="``" alt="" />
				<button type="submit" class="submit">Send</button>
			</form>
		</section>
	</section>
	<div>
		<BaseDelete v-if="showModal" :show-modal="showModal" />
	</div> -->
</template>

<script setup>
// import { computed, ref } from "vue";
// import BaseDelete from "./components/BaseDelete.vue";
import BaseComments from "./components/comments/BaseComments.vue";
// import BaseComment from "./components/comments/BaseComment.vue";
// import data from "./data/data.json";

// console.log(data);
// console.log(data.comments);



// const showModal = ref(false);
</script>

<style lang="scss" scoped></style>
