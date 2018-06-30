<template lang='pug'>
	#app
		.wrapper
			header-page.wrapper__header
			navigation
			content-page.wrapper__content
</template>

<script>
export default {
	name: 'App',
	components: {
		HeaderPage: () => import('@/components/Header'),
		Navigation: () => import('@/components/Navigation'),
		ContentPage: () => import('@/components/Content')
	}
}
</script>

<style lang="scss">
@import '@/assets/fonts/fonts.scss';
@import '@/assets/base.scss';
.wrapper__header, .wrapper__content {
	width: calc(100% - 240px);
	margin-left: auto;
}
</style>
