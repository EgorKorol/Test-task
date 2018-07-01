<template lang="pug">
	transition(name='modal')
		.modal-overlay(@click.self="$emit('closeModal')")
			.modal(@click.self="$emit('closeModal')")
				slot(name='header')
				slot(name='body')
				slot(name='footer')
</template>

<script>
export default {
	name: 'Modal'
}
</script>

<style lang="scss" scoped>
.modal-overlay {
	position: fixed;
	z-index: 9998;
	top: 0;
	left: 0;
	width: 100%;
	height: 100%;
	background-color: transparent;
	transition: opacity .3s ease;
	display: flex;
	align-items: center;
	justify-content: center;
	background-color: rgba(#000, .3);
}

.modal {
	width: 100%;
	max-width: 885px;
	color: var(--textColor);
	border-radius: 5px;
	transition: all .3s ease;
	height: auto;
	max-height: 100%;
	overflow: auto;
	box-shadow: 0 7px 8px rgba(0, 0, 0, 0.16);
	border-radius: 5px;
	border: 1px solid rgba(223, 223, 230, 0.8);
}

.modal-leave-active, .modal-enter {
	opacity: 0;
}

.modal-enter .modal-container,
.modal-leave-active .modal-container {
	transform: scale(1.1);
}
</style>
