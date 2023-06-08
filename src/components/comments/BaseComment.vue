<template>
	<section class="commentWrapper mainComment">
		<section class="profile">
			<img
				:src="`${getImageUrl(comment.user.image.png)}`"
				:alt="`${comment.user.username}`"
				class="avatar"
			/>
			<p class="profileName">{{ comment.user.username }}</p>
      <p class="currentUser"
      v-if="currentUser === comment.user.username"
      >you</p>
			<p class="createdAt">{{ comment.createdAt }}</p>
		</section>
		<p class="comment__content">{{ comment.content }}</p>
    <form action="">
      
    </form>
		<section class="counter">
			<button type="button" @click.prevent="score++" class="btn">
				<img src="@/assets/images/icon-plus.svg" alt="decrease score" />
			</button>
			<p class="score">{{ comment.score }}</p>
			<button type="button" @click.prevent="score--" class="btn btn--minus">
				<img src="@/assets/images/icon-minus.svg" alt="decrease score" />
			</button>
		</section>

		<section class="modifyCommentBtns">
			<div
				v-if="comment.user.username === currentUser"
				class="editAndDeleteWrapper"
			>
				<button type="button" class="btn btn--delete">
					<img src="@/assets/images/icon-delete.svg" alt="" />
					<span> Delete </span>
				</button>
				<button type="button" class="btn btn--edit">
					<img src="@/assets/images/icon-edit.svg" alt="" />
					<span> edit </span>
				</button>
			</div>
			<div v-else class="btn--replyWrapper">
				<button 
				type="button" 
				class="btn btn--reply"
				@click.prevent="showTextArea"
				>
					<img src="@/assets/images/icon-reply.svg" alt="" />
					<span> reply </span>
				</button>
			</div>
		</section>
	</section>
</template>

<script setup>
import { computed, ref } from "vue";
import data from "@/data/data.json";

const props = defineProps({
	comment: {
		type: Object,
		required: true,
	},
});

const emit = defineEmits(['showTextArea'])

const currentUser = computed(() => data.currentUser.username);



function getImageUrl(name) {
	return new URL(`/src/assets/${name}`, import.meta.url).href;
}
const showTextArea = () => {
	emit('showTextArea')
}
</script>

<style scoped></style>
