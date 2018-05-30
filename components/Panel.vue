<template lang="pug">
	.left
		nuxt-link.left__item.left__logo(to="/")
			img(src="../assets/img/logo.png")
		.left__item
			.left__part
				| Рецепты
			.left__nav
				nuxt-link.left__nav-item(:to="{path: '/admin/recepies/edit/'}")
					| Добавить рецепт
				nuxt-link.left__nav-item(:to="{path: '/admin/recepies/list'}")
					| Все рецепты
		.left__item
			.left__part
				| Статьи
			.left__nav
				nuxt-link.left__nav-item(:to="{path: '/admin/articles/edit/'}")
					| Добавить статью
				nuxt-link.left__nav-item(:to="{path: '/admin/articles/list'}")
					| Все статьи

		.left__item
			.left__part
				| Ингредиенты
			.left__nav
				nuxt-link.left__nav-item(:to="{path: '/admin/ingredients/edit/'}")
					| Добавить и
				nuxt-link.left__nav-item(:to="{path: '/admin/ingredients/list'}")
					| Все ингредиенты

		.left__item
			.left__part
				| Оборудование
			.left__nav
				nuxt-link.left__nav-item(:to="{path: '/admin/equipments/edit/'}")
					| Добавить о
				nuxt-link.left__nav-item(:to="{path: '/admin/equipments/list'}")
					| Все оборудование


</template>




<script>
  /* eslint-disable */
  export default {
    data () {
      return {
        isMobileMenuOpen: false
      }
    },
	methods: {

	}
  }
</script>

<style lang="sass" scoped>
	@import '../assets/css/vars.sass'

	.left
		position: fixed
		width: 260px
		height: 100%
		left: 0
		top: 0
		background-color: $gray--dark
		color: $white
		padding: 20px

		&__logo
			display: block
			height: 60px

			img
				display: block
				height: 100%
				margin: 0 auto

		&__part
			margin-top: 20px
			font-size: 18px

		&__nav
			padding: 0 20px

		&__nav-item
			display: block
			color: $white
			cursor: pointer

			//&.nuxt-link-active
			&.nuxt-link-exact-active
				color: $blue


</style>