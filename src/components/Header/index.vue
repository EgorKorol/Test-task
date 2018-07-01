<template lang="pug">
	header.header
		.header__menu-btn
			button.hamburger(type='button', @click="$emit('toggleMenu')")
				span.hamburger__line
		.header__content
			.header__user-info
				.header__user-title Users List
				.header__user-number 874 users
			.header__search
				input.header__search-input(type='search')
			button.header__table-filter(type='button', @click='') Table filter
			.header__user-action
				button.header__user-btn(type='button', @click='')
					span.header__user-name Dale McCormick
					img.header__user-arrow(src='@/assets/img/Header/arrow.png')
</template>

<script>
export default {
	name: 'Header'
}
</script>

<style lang="scss" scoped>
.header {
	display: flex;
	align-items: center;
	background-color: var(--brandOrange);
	max-height: 90px;
}
.header__menu-btn {
	padding: 20px 15px;
}
.hamburger {
	border: 0;
	background: 0;
	position: relative;
	width: 31px;
	height: 24px;
	padding: 5px;
	--burgerColor: #242430;
	&:hover {
		--burgerColor: #fff;
	}
}
.hamburger__line {
	background-color: var(--burgerColor);
	height: 2px;
	display: block;
	width: 21px;
	&::before, &::after {
		content: '';
		display: block;
		height: 2px;
		width: 21px;
		background-color: var(--burgerColor);
		position: absolute;
	}
	&::before {
		top: 5px;
	}
	&::after {
		bottom: 5px;
	}
}
.header__content {
	padding: 20px 15px;
	display: flex;
	width: 100%;
	align-items: center;
	justify-content: space-between;
}
.header__user-info {
	color: var(--textColor);
}
.header__user-title {
	font-size: 22px;
	font-weight: 700;
	line-height: 35px;
}
.header__user-number {
	font-size: 14px;
}
.header__search {
	position: relative;
	&::before {
		content: url('../../assets/img/Header/search.png');
		display: block;
		position: absolute;
		left: 5px;
		top: 8px;
	}
}
.header__search-input {
	border-radius: 10px;
	background-color: rgba(#fff, .3);
	border: 0;
	padding: 8px 10px 8px 30px;
	font-family: 'Open Sans', sans-serif;
	font-size: 14px;
	min-width: 270px;
}
.header__table-filter {
	box-shadow: 0 2px 4px rgba(230, 230, 232, 0.3);
	border-radius: 4px;
	border: 1px solid #c59b46;
	background-color: #fff;
	color: var(--brandOrange);
	font-size: 14px;
	text-transform: uppercase;
	padding: 15px 12px;
	transition: .2s;
	&:hover, &:active, &:focus {
		background-color: var(--brandBlueLigten);
		color: #fff;
	}
}
.header__user-btn {
	background: 0;
	border: 0;
	font-size: 14px;
	display: flex;
	align-items: center;
}
.header__user-name {
	margin-right: 10px;
}

</style>
