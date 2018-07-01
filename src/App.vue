<template lang='pug'>
	#app
		.wrapper(:class="isShowMenu ? '' : 'wrapper--close-menu'")
			header-page.wrapper__header(@toggleMenu='toggleMenu')
			navigation.wrapper__aside(:class="isShowMenu ? '' : 'wrapper__aside--hidden'" )
			content-page.wrapper__content
</template>

<script>
export default {
	name: 'App',
	components: {
		HeaderPage: () => import('@/components/Header'),
		Navigation: () => import('@/components/Navigation'),
		ContentPage: () => import('@/components/Content')
	},
	data () {
		return {
			isShowMenu: true
		}
	},
	methods: {
		toggleMenu () {
			console.log(111)
			this.isShowMenu = !this.isShowMenu
		}
	}
}
</script>

<style lang="scss">
@import '@/assets/fonts/fonts.scss';
@import '@/assets/base.scss';
.wrapper__header, .wrapper__content {
	margin-left: auto;
	width: calc(100% - 240px);
	transition: .2s ease;
}
.wrapper__aside {
	position: absolute;
	top: 0;
	left: 0;
	width: 240px;
	height: 100%;
	transition: .2s ease;
	&--hidden {
		transform: translateX(-100%);
	}
}
.wrapper--close-menu {
	.wrapper__header, .wrapper__content {
		width: 100%;
	}
}
</style>
