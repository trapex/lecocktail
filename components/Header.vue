<template lang="pug">
	header.header
		.columns.is-mobile.header__list
			nuxt-link.column.header__item.header__logo(to="/")
				img(src="../assets/img/logo.png")
			.column.is-three-quarters.header__item.header__nav(:class="isMobileMenuOpen ? 'header__nav_open' : ''")
				nav.columns
					nuxt-link.column(to="/recipes")
						| Коктейли
					nuxt-link.column(to="/articles")
						| Интересное
					nuxt-link.column(to="/equipment")
						| Оборудование
					nuxt-link.column(to="/equipment")
						| Технологии
					.column.header__mob-login
						| Войти
			.column.header__item.header__login Войти
			//.column.header__item.header__auth Войти
			.column.header__item.header__burger.js-header-menu-burger(@click='targetBurger' v-if="isMobileMenuOpen")
				img(src="../assets/img/close.png")
			.column.header__item.header__burger.js-header-menu-burger(@click='targetBurger' v-else)
				img(src="../assets/img/burger.png")
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
      targetBurger: function(event) {
        this.isMobileMenuOpen = !this.isMobileMenuOpen;
	  }
	}
  }
</script>

<style lang="sass" scoped>
	@import '../assets/css/vars.sass'

	.header
		width: 100%
		background-color: $gray--dark
		color: $white

		@media #{$mobile}
			position: fixed
			height: 79px
			padding: 20px 30px
			z-index: 100

		@media #{$tabletdesk}
			padding: 15px 20px

		&__logo
			color: $white

			img
				width: 35px
				vertical-align: middle

		&__list
			display: flex
			flex-direction: row
			justify-content: space-between
			align-items: center

		&__login
			display: none

			@media #{$tabletdesk}
				display: block
				text-align: right
				cursor: pointer

		&__mob-login
			display: block
			text-align: center

			@media #{$tabletdesk}
				display: none

		&__item

			@media #{$mobile}
				padding: 10px 0

		&__burger

			@media #{$mobile}
				display: block
				padding: 10px 0 10px 5px
				background-position: right center
				text-align: right

			@media #{$tabletdesk}
				display: none

			img
				width: 35px
				margin: 0 0 0 auto

		&__nav

			nav

				@media #{$mobile}
					display: none
					padding: 15px 0
					margin: 0

				a
					display: block
					position: relative
					color: $white

					@media #{$mobile}
						box-sizing: border-box
						padding: 5px
						text-align: center

					@media #{$tabletdesk}
						padding: 10px



			&_open

				nav
					@media #{$mobile}
						display: block
						position: absolute
						width: 100%
						top: 79px
						left: 0
						background-color: $gray--dark
						z-index: 100



</style>