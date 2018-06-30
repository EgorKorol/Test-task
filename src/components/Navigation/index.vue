<template lang="pug">
	aside.aside
		.aside__logo
			a.aside__logo-link(href='#')
				img.aside__logo-img(src='@/assets/img/Menu/logo.png')
				span.aside__logo-text Open Circles
		nav.nav
			ul.nav__list
				li.nav__item(v-for='item in menuItems', :key='item.text')
					a.nav__link(:href='item.href')
						img.nav__img(:src='pathToIcon(item.icon)')
						span.nav__text {{item.text}}
</template>

<script>
export default {
	name: 'Navigation',
	data () {
		return {
			menuItems: [
				{
					text: 'Users List',
					icon: 'user-list',
					href: '#'
				},
				{
					text: 'Daily',
					icon: 'daily',
					href: '#'
				},
				{
					text: 'Brainstorm',
					icon: 'brainstorm',
					href: '#'
				},
				{
					text: 'Course',
					icon: 'course',
					href: '#'
				},
				{
					text: 'Leveling system',
					icon: 'leveling-system',
					href: '#'
				},
				{
					text: 'Live streams',
					icon: 'live-streams',
					href: '#'
				},
				{
					text: 'Advanced',
					icon: 'advanced',
					href: '#'
				},
				{
					text: 'Video analytics',
					icon: 'video-analytics',
					href: '#'
				}
			]
		}
	},
	methods: {
		pathToIcon (icon) {
			return require('@/assets/img/Menu/' + icon + '.png')
		}
	}
}
</script>

<style lang="scss" scoped>
.aside {
	background-color: var(--brandBlue);
	position: absolute;
	top: 0;
	left: 0;
	width: 240px;
	height: 100%;
}
.aside__logo {
	width: 100%;
	background-color: var(--brandBlueLigten);
	display: flex;
	justify-content: center;
	align-items: center;
	padding: 20px 15px;
	min-height: 90px;
}
.aside__logo-link {
	display: flex;
	align-items: center;
	text-decoration: none;
}
.aside__logo-img {
	margin-right: 20px;
}
.aside__logo-text {
	color: #ffffff;
	font-size: 18px;
}
.nav__item {
	padding: 22px 18px;
	position: relative;
	opacity: .7;
	transition: .2s;
	&:hover {
		&::before {
			content: '';
			background-color: #fff;
			height: 100%;
			width: 3px;
			display: block;
			position: absolute;
			left: 0;
			top: 0;
		}
		opacity: 1;
	}
}
.nav__link {
	text-decoration: none;
	color: #ffffff;
	display: flex;
	align-items: center;
}
.nav__img {
	filter: invert(100%) brightness(200%);
	margin-right: 20px;
}
.nav__text {
	font-family: 'SFUID', sans-serif;
	font-size: 14px;
	text-transform: uppercase;
}
</style>
