<template>
	<section class="modal">
		<section class="modal__content">
			<h1 class="modal__title">Delete comment</h1>
			<p>
				Are you sure you want to delete this comment? This will remove the
				comment and can't be undone.
			</p>
			<div>
				<button type="button" class="btn btn--cancel">no, cancel</button>
				<button type="button" class="btn btn--danger">yes, delete</button>
			</div>
		</section>
	</section>
</template>

<script setup>
defineProps({
  showModal: {
    type: Boolean,
    required: true
  }
});
</script>

<style scoped>
.modal {
	position: fixed;
	top: 0;
	left: 0;
	width: 100%;
	height: 100vh;

	display: flex;
	justify-content: center;
	align-items: center;
	padding: 1em;

	background-color: rgba(0, 0, 0, 0.2);
}
.modal__content {
	max-width: 330px;
	border-radius: 10px;
	background-color: var(--White);
	padding: 1.2em;
}
.modal__title {
	color: var(--Darkblue);
	font-size: 1.3rem;
	margin: 0.4em 0 0.6em;
}
.modal p {
	color: var(--GrayishBlue);
	line-height: 1.5;
	margin-bottom: 0.5em;
}
button {
	background-color: transparent;
	border: 0;
	cursor: pointer;
}
.btn {
	padding: 0.8em;
	color: var(--White);
	display: block;
	width: 100%;
	border-radius: 5px;
	text-transform: uppercase;
	font-weight: var(--fw-l);
	margin: 1em 0em 0;
	font-size: 0.9rem;
	transition: all 0.3s ease;
}
.btn:hover {
	transform: scale(1.04);
	box-shadow: 0px 1px 8px rgba(0, 0, 0, 0.3);
}
.btn--cancel {
	background-color: var(--GrayishBlue);
	margin-right: 0.7em;
}
.btn--danger {
	background-color: var(--SoftRed);
}
.showModal {
	/* display: none; */
}
@media (min-width: 341px) {
	.btn {
		font-size: 1rem;
		display: inline-block;
		width: initial;
    padding: 0.8em 1.1em;
	}
	.btn--cancel {
		background-color: var(--GrayishBlue);
		margin-right: 0em;
	}
  .modal__content div {
    display: flex;
    justify-content: space-between;
    align-items: center;
  }
}
</style>
