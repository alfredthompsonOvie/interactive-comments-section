<template>
	<!-- <BaseComment /> -->
	<section class="commentWrapper">
		<section class="profile">
			<img
				:src="`${getImageUrl(comment.user.image.png)}`"
				:alt="`${comment.user.username}`"
				class="avatar"
			/>
			<p class="profileName">{{ comment.user.username }}</p>
			<p class="createdAt">{{ comment.createdAt }}</p>
		</section>
		<p class="comment__content">{{ comment.content }}</p>

		<section class="counter">
			<button type="button" @click.prevent="score++" class="btn">
				<img src="@/assets/images/icon-plus.svg" alt="decrease score" />
			</button>
			<p class="score">{{ score }}</p>
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
				<button type="button" class="btn btn--reply">
					<img src="@/assets/images/icon-reply.svg" alt="" />
					<span> reply </span>
				</button>
			</div>
		</section>
	</section>
</template>

<script setup>
import { computed, ref } from "vue";
// import BaseComment from "./BaseComment.vue";

const props = defineProps({
	comment: {
		type: Object,
		required: true,
	},
});
const score = ref(props.comment.score);
const reply = ref(true);
const currentUser = ref("juliusomo");

function getImageUrl(name) {
	return new URL(`/src/assets/${name}`, import.meta.url).href;
}
// function decreaseCount() {}
</script>

<style scoped>
.commentWrapper {
	display: grid;
	grid-template-columns: repeat(2, 1fr);
	grid-template-rows: repeat(3, auto);
	/* justify-content: start; */
	color: var(--GrayishBlue);
}
.profile {
	grid-column: 1/-1;
	grid-row: 1;
	display: flex;
	align-items: center;
	gap: 0.5em;
}
.avatar {
	height: 2em;
}
.profileName {
	color: var(--Darkblue);
	font-weight: var(--fw-l);
}
.createdAt {
}
.comment__content {
	grid-column: 1/-1;
	grid-row: 2;
	margin: 1em 0;
}
.counter {
	grid-column: 1;
	grid-row: 3;
	justify-self: start;
	background-color: var(--VeryLightGray);
	/* padding: .5em; */
	display: inline-flex;
	align-items: center;
	gap: 0.5em;
	border-radius: 6px;
	/* width: 4.5em; */
}
.btn {
	padding: 0.8em;
	/* position: relative; */
	text-transform: uppercase;
	font-weight: var(--fw-l);
	color: var(--ModerateBlue);
}
.btn--minus img {
	display: flex;
}
.score {
	color: var(--ModerateBlue);
}
.modifyCommentBtns {
	grid-column: 2;
	grid-row: 3;
	/* align-self: end; */
	/* justify-self: end; */
	/* margin-right: auto; */
	display: inline-flex;
	justify-content: space-between;
}
.editAndDeleteWrapper {
}
.btn--delete {
	color: var(--SoftRed);
}
.btn--edit {
}
.btn--replyWrapper {
	margin-left: auto;
}
.btn--reply {
	display: inline-flex;
	align-items: center;
	gap: 0.4em;
	/* text-transform: uppercase; */
	/* font-weight: var(--fw-l); */
}
@media (min-width: 580px) {
	.commentWrapper {
		display: grid;
		grid-template-columns: 3em 1fr 4em;
		grid-template-rows: repeat(2, auto);
		/* justify-content: start; */
		color: var(--GrayishBlue);
	}

	.counter {
		grid-column: 1;
		grid-row: 1/-1;
		justify-self: start;
		align-self: start;
		/* padding: .5em; */
		display: inline-flex;
		flex-direction: column;
		align-items: center;

		/* width: 4.5em; */
	}

	.profile {
		grid-column: 2;
		grid-row: 1;
	}
	.comment__content {
	grid-column: 2/-1;
	grid-row: 2;
	/* margin: 1em 0; */
}
.modifyCommentBtns {
	grid-column: 3;
	grid-row: 1;
	/* align-self: end; */
	/* justify-self: end; */
	/* margin-right: auto; */
	display: inline-flex;
	justify-content: space-between;
}
}
</style>
