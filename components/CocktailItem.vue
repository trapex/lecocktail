<template lang="pug">

	//.item.column.is-one-third-desktop.is-half-tablet(v-for='item in latestList', :key='item.id', @click='goToCocktail(item)')

	.box
		.item__img(:style="{backgroundImage: `url(${item.image})`}")
		.item__content
			.item__title
				| {{item.title}}
				br
			.item__bottom
				.item__info
					.item__icon
					.item__time
						svg(width='18px', height='19px', viewbox='0 0 18 19', data-reactid='495')
							g#Symbols(stroke='none', stroke-width='1', fill='none', fill-rule='evenodd', stroke-linecap='round', stroke-linejoin='round', data-reactid='496')
								g(id='Block-/-1:3-/-Recepie-Preview', transform='translate(-237.000000, -317.000000)', stroke='#59595b', data-reactid='497')
									g(id='Icon-20-/-Gray-/-Clock', transform='translate(233.000000, 313.000000)', data-reactid='498')
										ellipse#Oval-41(cx='12.9807692', cy='13.5', rx='8.17307692', ry='8.5', data-reactid='499')
										path#Line(d='M12.4699519,14.03125 L16.5564904,14.03125', data-reactid='500')
										path#Line(d='M12.4699519,7.65625 L12.4699519,14.03125', data-reactid='501')
						.item__time-text 40 мин
				.item__link
		.item__hover
			.item__hover-title
				| Ингредиенты
			.item__hover-ingrefients
				| {{item.description}}

</template>

<script>
  export default {
    props: ['item'],
    data() {
      return {

      }
    },
    methods: {

	}
  }
</script>

<style lang="sass" scoped>
	@import '~assets/css/vars.sass'

	.item
		position: relative
		cursor: pointer

		@media #{$mobile}
			margin: 0 auto
			max-width: 450px

		&:before
			content: ''
			position: absolute
			top: 0
			left: 0
			width: 100%
			height: calc(100% + 147px)
			background-color: $white
			box-shadow: 0 8px 20px rgba(0,0,0,0.1)
			visibility: hidden

		.box
			position: relative
			padding: 0
			border-radius: 0
			box-shadow: 0 8px 20px rgba(0,0,0,0.1)

		&:hover

			@media #{$desktop}
				box-shadow: 0 8px 20px rgba(0,0,0,0.1)

				&:before
					visibility: visible

				.box
					box-shadow: none

				.item__hover
					visibility: visible

		&__img
			width: 100%
			height: 270px
			background-size: cover
			background-position: center
			background-repeat: no-repeat

		&__content
			padding: 20px

		&__title
			font-weight: 500
			text-transform: uppercase

		&__bottom
			margin-top: 10px
			display: flex
			justify-content: space-between

		&__info
			display: flex
			justify-content: flex-start
			align-items: center
			width: 50%

		&__icon
			/*background-image: url(../assets/img/cocktail-icon.png)*/
			width: 22px
			height: 30px
			background-size: contain
			background-position: center
			background-repeat: no-repeat

		&__time
			margin-left: 20px
			display: flex
			justify-content: flex-start
			align-items: center

			svg
				display: block


		&__time-text
			margin-left: 5px

			@media #{$mobile}
				font-size: 10px

			@media #{$tabletdesk}
				font-size: 12px

		&__link
			display: block
			width: 50%
			margin: 20px auto 0 auto

		&__hover
			position: absolute
			width: calc(100% + 1.5rem)
			left: -0.75rem
			padding: 20px
			background-color: $white
			visibility: hidden
			z-index: 2

			&:before
				content: ''
				position: absolute
				top: 0
				left: 5%
				width: 90%
				height: 1px
				background-color: $gray--light

		&__hover-title
			font-size: 16px
			font-weight: 500

		&__hover-ingredients

</style>