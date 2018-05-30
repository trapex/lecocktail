<template lang="pug">
	section.page.articles
		.columns.articles__content
			.column.is-three-quarters-desktop.is-two-thirds-tablet.articles__list-wrap
				.articles__list-overflow
					.articles__list.columns.is-multiline
							a.articles__item.column.is-half-desktop.is-full-tablet(v-for='item in articles', :key='item.id', @click='goToArticle(item)')
								.articles__item-wrap(:style="{backgroundImage: `url(${item.image})`}")
									.articles__item-content
										.articles__item-title
											| {{item.title}}
										.articles__item-description
											| {{item.short_description}}
					.articles__show-more.button(v-if='!articles_model.last_page', @click="onClickShowMore") еще
			.column.articles__right
				.articles__recipes
					.articles__right-title
						| Топ коктейли:
					.articles__article-list
						article.media.articles__recipe-item(v-for='recipe in recipes', :key='recipe.id')
							.media-content
								.content
									p
										span.articles__recipe-link(@click='goToCocktail(recipe)')
											| {{recipe.title}}
										br
										| {{recipe.short_description}}

				.articles__event
					.articles__right-title
						| События:
					a.articles__event-item(href="#" target="_blank" rel="noopener")
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
			title: 'Статьи Le cocktail'
		}
	},
  data () {
    return {
      articles_model: {
        offset: 0,
        per: 8,
        total_count: null,
        last_page: false
      },
      recipes: [
        {
          id: 1,
          slug: 'cocktail_1',
          title: 'Cocktail #1 Cocktail #1 Cocktail #1 Cocktail #1',
          short_description: 'Aenean efficitur sit amet massa fringilla egestas. Nullam condimentum luctus turpis.',
          image: require('../assets/img/article1.jpg'),
          url: '@johnsmith',
        },
        {
          id: 2,
          slug: 'cocktail_2',
          title: 'Cocktail #2',
          short_description: 'Lorem ipsum dolor sit amet, consectetur adipiscing elit. .',
          image: require('../assets/img/article2.jpg'),
          url: '@paulsmith',
        },
        {
          id: 3,
          slug: 'cocktail_3',
          title: 'Cocktail #3',
          short_description: 'Lorem ipsum dolor sit amet, consectetur adipiscing elit.',
          image: require('../assets/img/article2.jpg'),
          url: '@mikesmith',
        }
      ],
	  articles: [
		{
		  id: 1,
		  slug: 'articles_1',
		  title: 'Articles #1',
          image: require('../assets/img/article1.jpg'),
		  short_description: 'Short description of Article #1'
		},
        {
          id: 2,
          slug: 'articles_2',
          title: 'Articles #2',
          image: require('../assets/img/article2.jpg'),
          short_description: 'Short description of Article #2'
        },
        {
          id: 3,
          slug: 'articles_3',
          title: 'Articles #3',
          image: require('../assets/img/article2.jpg'),
          short_description: 'Short description of Article #3'
        },
        {
          id: 4,
          slug: 'articles_4',
          title: 'Articles #4',
          image: require('../assets/img/article1.jpg'),
          short_description: 'Short description of Article #3'
        },
        {
          id: 5,
          slug: 'articles_5',
          title: 'Articles #5',
          image: require('../assets/img/article1.jpg'),
          short_description: 'Short description of Article #3'
        },
        {
          id: 6,
          slug: 'articles_6',
          title: 'Articles #6',
          image: require('../assets/img/article2.jpg'),
          short_description: 'Short description of Article #3'
        },
        {
          id: 7,
          slug: 'articles_7',
          title: 'Articles #7',
          image: require('../assets/img/article2.jpg'),
          short_description: 'Short description of Article #3'
        },
        {
          id: 8,
          slug: 'articles_8',
          title: 'Articles #8',
          image: require('../assets/img/article1.jpg'),
          short_description: 'Short description of Article #3'
        },
        {
          id: 9,
          slug: 'articles_9',
          title: 'Articles #9',
          image: require('../assets/img/article1.jpg'),
          short_description: 'Short description of Article #3'
        },
        {
          id: 10,
          slug: 'articles_10',
          title: 'Articles #10',
          image: require('../assets/img/article2.jpg'),
          short_description: 'Short description of Article #3'
        },
        {
          id: 11,
          slug: 'articles_11',
          title: 'Articles #11',
          image: require('../assets/img/article2.jpg'),
          short_description: 'Short description of Article #3'
        }
	  ]
    }
  },
  methods: {
    goToCocktail: function (item) {
      this.$router.push(`/cocktail/${item.slug}`);
    },
    goToArticle: function (item) {
      this.$router.push(`/article/${item.slug}`);
    },
    onClickShowMore: function() {
      debugger;
	}
  }
}
</script>

<style lang="sass" scoped>
	@import '~assets/css/vars.sass'

	.articles

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

			@media #{$mobile}
				padding: 20px .75em

		&__list

		&__right
			height: auto
			padding: 0
			margin: 0

			@media #{$mobile}
				width: 100%
				background-color: $white
				padding-bottom: 20px

		&__event

		&__recipes

			@media #{$mobile}
				border-bottom: 1px solid $gray--light

		&__recipes,
		&__event
			background-color: $white
			margin-bottom: 20px

			@media #{$mobile}
				width: 90%
				margin: 0 auto
				padding: 20px 0.75em

			@media #{$tabletdesk}
				width: 100%
				padding: 0.75em
				border-radius: 5px
				box-shadow: 0 15px 15px rgba(0,0,0,0.15)

		&__right-title
			margin-bottom: 10px
			@include font(400)
			color: $blue

			@media #{$mobile}
				font-size: 18px

			@media #{$tabletdesk}
				font-size: 22px

		&__item
			color: $gray--font

			@media #{$mobile}
				width: 90%
				margin: 0 auto

			&:hover

				@media #{$desktop}
					.articles__item-wrap
						&:before
							background-color: rgba(0, 0, 0, 0.3)
							transition: background-color 0.3s ease-in

		&__item-wrap
			position: relative
			display: flex
			align-items: center
			padding: 20px
			border-radius: 0
			background-size: cover
			background-position: center
			background-repeat: no-repeat
			height: 320px
			border: 1px solid $gray--light

			&:before
				@media #{$desktop}
					content: ''
					position: absolute
					width: 100%
					height: 100%
					top: 0
					left: 0
					background-color: transparent
					transition: background-color 0.3s ease-out

		&__item-content
			position: relative
			height: 120px
			margin: 0 auto
			padding: 10px 0
			text-align: center
			background-color: rgba(255, 255, 255, 0.85)
			overflow: hidden

			@media #{$mobile}
				width: 97.5%

			@media #{$tablet}
				width: 85%

			@media #{$desktop}
				width: 75%

		&__item-title
			width: 80%
			margin: 0 auto
			height: 38px
			overflow: hidden
			text-transform: uppercase
			font-weight: 900
			font-size: 25px
			border-bottom: 1px solid $gray--dark

		&__item-description
			width: 80%
			margin: 5px auto 0 auto

		&__item-link
			display: block
			margin: 20px auto 0 auto

			@media #{$mobile}
				@include customBtn(150px, 40px, $blue, $white)

			@media #{$tablet}
				@include customBtn(120px, 40px, $blue, $white)

			@media #{$desktop}
				@include customBtn(150px, 40px, $blue, $white)

		&__recipe-link
			display: inline-block
			position: relative
			cursor: pointer
			height: 25px
			overflow: hidden
			text-overflow: ellipsis
			@include font(500)

			&:after
				content: ''
				position: absolute
				bottom: 0
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
