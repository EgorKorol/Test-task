<template lang='pug'>
	#app
		.wrapper
			header-page.wrapper__header
			navigation
</template>

<script>
export default {
	name: 'App',
	components: {
		HeaderPage: () => import('@/components/Header'),
		Navigation: () => import('@/components/Navigation')
	}
}
</script>

<style lang="scss">
@import '@/assets/fonts/fonts.scss';
@import '@/assets/base.scss';
.wrapper__header {
	width: calc(100% - 240px);
	margin-left: auto;
}
</style>
