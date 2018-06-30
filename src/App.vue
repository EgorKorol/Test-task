<template lang='pug'>
	#app
		.wrapper
			header-page
</template>

<script>
export default {
	name: 'App',
	components: {
		HeaderPage: () => import('@/components/Header')
	}
}
</script>

<style lang="scss">
@import '@/assets/fonts/fonts.scss';
@import '@/assets/base.scss';

</style>
