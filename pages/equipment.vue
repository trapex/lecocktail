<template lang="pug">
	section.page.equipment
		.columns.equipment__content
			.column.is-three-quarters-desktop.is-two-thirds-tablet.equipment__list-wrap
				.equipment__list-overflow
					.equipment__title
						| Оборудование:
					.content
						//h2 Second level
						p
							|Curabitur accumsan turpis pharetra&nbsp;
							strong augue tincidunt
							| &nbsp;blandit. Quisque condimentum maximus mi, sit amet commodo arcu rutrum id.
							| Proin pretium urna vel cursus venenatis. Suspendisse potenti.
							| Etiam mattis sem rhoncus lacus dapibus facilisis. Donec at dignissim dui.
							| Ut et neque nisl.
						ul
							li In fermentum leo eu lectus mollis, quis dictum mi aliquet.
							li Morbi eu nulla lobortis, lobortis est in, fringilla felis.
							li Aliquam nec felis in sapien venenatis viverra fermentum nec lectus.
							li Ut non enim metus.
						h3 Third level
						p
							|Curabitur accumsan turpis pharetra&nbsp;
							strong augue tincidunt
							| &nbsp;blandit. Quisque condimentum maximus mi, sit amet commodo arcu rutrum id.
							| Proin pretium urna vel cursus venenatis. Suspendisse potenti.
							| Etiam mattis sem rhoncus lacus dapibus facilisis. Donec at dignissim dui.
							| Ut et neque nisl.
			.column.equipment__right
				.equipment__article
					.equipment__right-title
						| Интересное:
					.equipment__article-list
						article.media.equipment__article-item(v-for='article in articles', :key='article.id')
							.media-content
								.content
									p
										span.equipment__article-link(@click='goToArticle(article)')
											| {{article.title}}
										br
										| {{article.short_description}}

				.equipment__event
					.equipment__right-title
						| События:
					a.equipment__event-item(href="#" target="_blank" rel="noopener")
						img(src="../assets/img/cocktail-party.jpg")
</template>

<script>
/* eslint-disable */
import _ from 'underscore'
import axios from '~/plugins/axios'

export default {
	async asyncData() {
//		let {data} = await axios.get('/api/users')
//		return {users: data}
//	  return axios.get('http://localhost:3000/data/cocktail.json')
//		.then(response => {
//			return {list: response.data};
//		})
//		.catch(error => {
//		  console.log(error)
//		});
	},
	head() {
		return {
			title: 'Оборудование Le cocktail'
		}
	},
  data () {
    return {
	  articles: [
		{
		  id: 1,
		  slug: 'articles_1',
		  title: 'Articles #1',
		  short_description: 'Short description of Article #1'
		},
        {
          id: 2,
          slug: 'articles_2',
          title: 'Articles #2',
          short_description: 'Short description of Article #2'
        },
        {
          id: 3,
          slug: 'articles_3',
          title: 'Articles #3',
          short_description: 'Short description of Article #3'
        }
	  ]
    }
  },
  methods: {
    goToArticle: function (item) {
      this.$router.push(`/article/${item.slug}`);
    }
  }
}
</script>

<style lang="sass" scoped>
	@import '~assets/css/vars.sass'

	.equipment

		&__title
			@include font(400)
			color: $blue

			@media #{$mobile}
				font-size: 24px

			@media #{$tablet}
				font-size: 36px

			@media #{$desktop}
				font-size: 36px

		&__content

			@media #{$mobile}
				background-color: $white
				padding-top: 20px

			@media #{$tablet}
				margin: 20px 0

			@media #{$desktop}
				max-width: 1280px
				min-height: 600px
				margin: 20px auto

		&__list-wrap
			padding: 0

			@media #{$tablet}
				margin-right: 20px

			@media #{$desktop}
				margin-right: 20px

		&__list-overflow
			background-color: $white
			border-radius: 5px
			box-shadow: 0 15px 15px rgba(0,0,0,0.15)
			padding: .75em
			min-height: 600px

			@media #{$mobile}
				padding: 20px .75em

		&__list

		&__mob-filter
			display: none

			@media #{$mobile}
				display: block
				width: 90%
				margin: 0 auto
				padding-bottom: 0


		&__right
			height: auto
			padding: 0
			margin: 0

			@media #{$mobile}
				width: 100%
				background-color: $white
				padding-bottom: 20px

		&__filter
			@media #{$mobile}
				display: none

		&__article

			@media #{$mobile}
				border-top: 1px solid $gray--light
				border-bottom: 1px solid $gray--light

		&__event


		&__article,
		&__event
			width: 100%
			padding: 0.75em
			background-color: $white
			margin-bottom: 20px

			@media #{$mobile}
				width: 90%
				margin: 0 auto
				padding: 20px 0.75em

			@media #{$tablet}
				border-radius: 5px
				box-shadow: 0 15px 15px rgba(0,0,0,0.15)

			@media #{$desktop}
				border-radius: 5px
				box-shadow: 0 15px 15px rgba(0,0,0,0.15)

		&__right-title
			margin-bottom: 10px
			@include font(400)
			color: $blue
			font-size: 22px

			@media #{$mobile}
				font-size: 18px

		&__item

			@media #{$mobile}
				width: 90%
				margin: 0 auto


			.box
				padding: 20px
				border-radius: 0

		&__item-img
			width: 100%
			height: 200px
			background-size: contain
			background-position: center
			background-repeat: no-repeat

		&__item-title
			margin-top: 20px
			height: 45px
			overflow: hidden

		&__item-link
			display: block
			margin: 20px auto 0 auto

			@media #{$mobile}
				@include customBtn(150px, 40px, $blue, $white)

			@media #{$tablet}
				@include customBtn(120px, 40px, $blue, $white)

			@media #{$desktop}
				@include customBtn(150px, 40px, $blue, $white)

		&__article-link
			position: relative
			cursor: pointer
			@include font(500)

			&:after
				content: ''
				position: absolute
				bottom: -1px
				left: 0
				width: 100%
				height: 1px
				background-color: $gray--font

				@media #{$desktop}
					visibility: visible
					transition: transform 0.3s ease-out
					transform: scaleX(0)

			&:hover

				&:after
					@media #{$desktop}
						visibility: visible
						transition: transform 0.3s ease-in
						transform: scaleX(1)


		&__event-item


		.button
			display: block

			@media #{$mobile}
				margin: 20px auto 0 auto
				@include customBtn(150px, 40px, $blue, $white)

			@media #{$tablet}
				margin: 20px auto 0 auto
				@include customBtn(140px, 40px, $blue, $white)

			@media #{$desktop}
				margin: 20px auto 0 auto
				@include customBtn(150px, 40px, $blue, $white)

			&:focus,
			&:active
				box-shadow: none

			&_search
				@media #{$mobile}
					margin: 0
					@include customBtn(100%, 40px, $blue, $white)

				img
					display: block
					height: 24px
					margin: 8px auto


</style>
