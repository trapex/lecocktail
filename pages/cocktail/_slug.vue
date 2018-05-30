<template lang="pug">
	section.page.cocktail(v-if="cocktail", :key="cocktail.id")
		.cocktail__item
			.cocktail__item-title {{cocktail.title}}
			.cocktail__image-wrap
				.cocktail__image(:style="{backgroundImage: `url(${cocktail.image})`}")
			.cocktail__content
				.content.columns
					.column.cocktail__ingredients.is-tablet.is-desktop
						h4 Ингредиенты:
						| {{cocktail.ingredients}}
					.column.cocktail__equipment.is-tablet.is-desktop
						h4 Оборудование:
						| {{cocktail.equipment}}
				.content.cocktail__item-description
					h4 Инструкция:
					p(v-html="cocktail.description")
					//| {{cocktail.description}} #[br] #[small Cocktail with id: {{cocktail.id}}]


</template>

<script>
  /* eslint-disable */

  import _ from 'underscore'
  import axios from 'axios'

  axios.defaults.baseURL = 'http://localhost:3000/data/'

  export default {
    head () {
      return {
        title: 'Cocktail in Le cocktail'
      }
    },
    data () {
      return {
		cocktail: {
          id: 1,
		  slug: 'cocktail_1',
          title: "This is cocktail #1",
          description: "This is descriptoin of cocktail #1<br>Шаг1:<br>Смешиваем это и это<br>Шаг2:<br>Добавляем щепотку поганок и каблук башмака",
          image: require('../../assets/img/cocktail2.jpg'),
          icon: require('../../assets/img/cocktail-martini-icon.png'),
          time: '40',
          level: '',
          ingredients: 'Ingredients Lorem ipsum [1] dolor sit amet, consectetur adipiscing elit. Nulla accumsan',
		  equipment: 'Equipment Lorem ipsum [1] dolor sit amet, consectetur adipiscing elit. Nulla accumsan Lorem ipsum [1] dolor sit amet, consectetur adipiscing elit. Nulla accumsan',
		}
      }
    },
//    asyncData (context) {
//      return axios.get('cocktail.json')
//        .then((response) => {
//          let cocktail = _.findWhere(response.data, {id: parseInt(context.params.id)});
//          cocktail.image = require(cocktail.image);
//          return {cocktail}
//        })
//    }
  }
</script>

<style lang="sass" scoped>
	@import '~assets/css/vars.sass'

	.cocktail
		margin: 0 auto

		&__item
			margin: 20px auto

			@media #{$mobile}
				width: 90%
				max-width: 440px

			@media #{$tabletdesk}
				max-width: 1280px
				min-height: 400px

		&__image-wrap
			width: 100%
			height: 250px
			margin-top: 10px

			@media #{$mobile}
				padding: 0

			@media #{$tabletdesk}
				height: 500px

			@media #{$desktop}
				padding: 0

		&__image
			width: 100%
			height: 100%
			background-size: cover
			background-repeat: no-repeat
			background-position: center

		&__item-description


		&__ingredients

			@media #{$mobile}
				border-bottom: 1px solid $blue

		&__equipment

			@media #{$mobile}
				border-bottom: 1px solid $blue

		&__item-title
			@include font(400)

			@media #{$mobile}
				font-size: 24px

			@media #{$tabletdesk}
				padding: 0 calc(0.75em/2)
				font-size: 36px

			//@media #{$desktop}
				padding: 0 0.75em

		&__content
			margin-top: 20px

			@media #{$tablet}
				padding: 0 0.75em
				/*padding: 0 20px*/

			@media #{$desktop}
				margin-top: 40px
				padding: 0 0.75em
				/*margin-left: 20px*/

		.button
			display: block

			@media #{$mobile}
				margin: 20px auto 0 auto
				@include customBtn(150px, 40px, $blue, $white)

			@media #{$tablet}
				margin: 30px auto 0 auto
				@include customBtn(150px, 40px, $blue, $white)

			@media #{$desktop}
				margin: 30px auto 0 auto
				@include customBtn(150px, 40px, $blue, $white)


</style>
