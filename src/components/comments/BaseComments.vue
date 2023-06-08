<template>
	<section
		class="commentsContainer"
		v-for="comment in comments"
		:key="comment.id"
	>

		<BaseComment :comment="comment" />

		<!-- <section class="replyContainer">
			<section class="replyContainerContnents">
				<template v-for="reply in comment.replies" :key="reply.id">
					<BaseComment :comment="reply" />
				</template>
			</section>
		</section> -->
		
		<ul class="replyContainer">
			<li
			class="replyContainerContnents"
			v-for="reply in comment.replies" :key="reply.id"
			>
			<BaseComment :comment="reply" />
		</li>
		</ul>

    <!-- v-if="showAddComment" -->
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
		<DeleteCommentModal v-if="showModal" />
	</div>
</template>

<script setup>
import { computed, ref } from "vue";
import data from "@/data/data.json";
import BaseComment from "./BaseComment.vue";
import DeleteCommentModal from "@/components/DeleteCommentModal.vue"


const comments = computed(() => data.comments);
// const score = ref(data.comment.score);
// const reply = ref(true);
// const currentUser = ref("juliusomo");
// const showAddComment = ref(false);
const showModal = ref(false);

const replies = computed(() => data.comment.replies);

// console.log(props.comment);
// console.log(replies.value);

function getImageUrl(name) {
	return new URL(`/src/assets/${name}`, import.meta.url).href;
}
// function decreaseCount() {}
</script>

<style scoped>

</style>
