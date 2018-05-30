<template lang="pug">
	section.page.recipes
		.columns.recipes__content
			.column.recipes__mob-filter
				.columns.is-mobile
					.column.is-three-quarters.field
						.control
							input.input.recipes__filter-item(type="text" placeholder="Основной ингредиент" data-recipes-filter="ingredient", @keyup="changeIngredient")
					.column.field
						.control
							button.button.button_search(@click="findCocktail")
								img(src="../assets/img/search-icon.png")
			.column.is-three-quarters-desktop.is-two-thirds-tablet.recipes__list-wrap
				.recipes__list-overflow
					cocktail-list(:list="list")
					//.recipes__list.columns.is-multiline
							a.recipes__item.column.is-one-third-desktop.is-half-tablet(v-for='item in list', :key='item.id', @click='goToCocktail(item)')
								.box
									.recipes__item-img(:style="{backgroundImage: `url(${item.image})`}")
									.recipes__item-title
										| {{item.title}}
					.recipes__show-more.button(v-if='!cocktail_model.last_page', @click="onClickShowMore") еще
			.column.recipes__right
				.recipes__filter
					.recipes__right-title
						| Поиск рецепта:
					.field
						.control
							.select.recipes__filter-item
								select(data-recipes-filter="level", @change="changeLevel")
									option(selected value="" disabled) Уровень
									option(value="new") Новичок
									option(value="boss") Любитель
									option(value="professional") Профессионал
					.field
						.control
							.select.recipes__filter-item
								select(data-recipes-filter="strong", @change="changeStrong")
									option(selected value="" disabled) Крепкость
									option(value="light") Ligth
									option(value="middle") Middle
									option(value="strong") Strong
					.field
						.control
							input.input.recipes__filter-item(type="text" placeholder="Основной ингредиент" data-recipes-filter="ingredient", @keyup="changeIngredient")
					.field
						.control
							button.button(@click="findCocktail") Найти

				.recipes__article
					.recipes__right-title
						| Интересное:
					.recipes__article-list
						article.media.recipes__article-item(v-for='article in articles', :key='article.id')
							.media-content
								nuxt-link.content(:to="{path: `/article/${article.slug}`}")
									p
										span.recipes__article-link
											| {{article.title}}
										br
										| {{article.short_description}}

				.recipes__event
					.recipes__right-title
						| События:
					a.recipes__event-item(href="#" target="_blank" rel="noopener")
						img(src="../assets/img/cocktail-party.jpg")
</template>

<script>
/* eslint-disable */
import _ from 'underscore'
import axios from '~/plugins/axios'
import CocktailList from '@/components/CocktailList';

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
			title: 'Recipes of Le cocktail'
		}
	},
  data () {
    return {
      filter_model: {
        level: '',
		strong: '',
        ingredient: ''
	  },
      cocktail_model: {
        offset: 0,
		per: 8,
		total_count: null,
		last_page: false
	  },
      list: [
        {
          id: 1,
          slug: 'cocktail_1',
          title: 'Cocktail #1 Cocktail #1 Cocktail #1 Cocktail #1',
          description: 'Lorem ipsum dolor sit amet, consectetur adipiscing elit. Aenean efficitur sit amet massa fringilla egestas. Nullam condimentum luctus turpis.',
          image: require('../assets/img/cocktail1.jpg'),
          icon: require('../assets/img/cocktail-vine-icon.png'),
          time: '20',
          level: '',
          url: '@johnsmith',
        },
        {
          id: 2,
          slug: 'cocktail_2',
          title: 'Cocktail #2',
          description: 'Lorem ipsum dolor sit amet, consectetur adipiscing elit. Aenean efficitur sit amet massa fringilla egestas. Nullam condimentum luctus turpis.',
          image: require('../assets/img/cocktail2.jpg'),
          icon: require('../assets/img/cocktail-shot-icon.png'),
          time: '30',
          level: '',
          url: '@paulsmith',
        },
        {
          id: 3,
          slug: 'cocktail_3',
          title: 'Cocktail #3',
          description: 'Lorem ipsum dolor sit amet, consectetur adipiscing elit. Aenean efficitur sit amet massa fringilla egestas. Nullam condimentum luctus turpis.',
          image: require('../assets/img/cocktail3.jpg'),
          icon: require('../assets/img/cocktail-martini-icon.png'),
          time: '10',
          level: '',
          url: '@mikesmith',
        },
        {
          id: 4,
          slug: 'cocktail_4',
          title: 'Cocktail #4',
          description: 'Lorem ipsum dolor sit amet, consectetur adipiscing elit. Aenean efficitur sit amet massa fringilla egestas. Nullam condimentum luctus turpis.',
          image: require('../assets/img/cocktail4.jpg'),
          icon: require('../assets/img/cocktail-martini-icon.png'),
          time: '15',
          level: '',
          url: '@alexsmith',
        },
        {
          id: 5,
          slug: 'cocktail_5',
          title: 'Cocktail #5',
          description: 'Lorem ipsum dolor sit amet, consectetur adipiscing elit. Aenean efficitur sit amet massa fringilla egestas. Nullam condimentum luctus turpis.',
          image: require('../assets/img/cocktail5.jpg'),
          icon: require('../assets/img/cocktail-glass-icon.png'),
          time: '20',
          level: '',
          url: '@alexsmith',
        },
        {
          id: 6,
          slug: 'cocktail_6',
          title: 'Cocktail #6',
          description: 'Lorem ipsum dolor sit amet, consectetur adipiscing elit. Aenean efficitur sit amet massa fringilla egestas. Nullam condimentum luctus turpis.',
          image: require('../assets/img/cocktail2.jpg'),
          icon: require('../assets/img/cocktail-vine-icon.png'),
          time: '10',
          level: '',
          url: '@mikesmith',
        },
        {
          id: 7,
          slug: 'cocktail_7',
          title: 'Cocktail #7',
          description: 'Lorem ipsum dolor sit amet, consectetur adipiscing elit. Aenean efficitur sit amet massa fringilla egestas. Nullam condimentum luctus turpis.',
          image: require('../assets/img/cocktail4.jpg'),
          icon: require('../assets/img/cocktail-shot-icon.png'),
          time: '40',
          level: '',
          url: '@alexsmith',
        },
        {
          id: 8,
          slug: 'cocktail_8',
          title: 'Cocktail #8',
          description: 'Lorem ipsum dolor sit amet, consectetur adipiscing elit. Aenean efficitur sit amet massa fringilla egestas. Nullam condimentum luctus turpis.',
          image: require('../assets/img/cocktail3.jpg'),
          icon: require('../assets/img/cocktail-vine-icon.png'),
          time: '10',
          level: '',
          url: '@alexsmith',
        },
        {
          id: 9,
          slug: 'cocktail_9',
          title: 'Cocktail #9',
          description: 'Lorem ipsum dolor sit amet, consectetur adipiscing elit. Aenean efficitur sit amet massa fringilla egestas. Nullam condimentum luctus turpis.',
          image: require('../assets/img/cocktail5.jpg'),
          icon: require('../assets/img/cocktail-martini-icon.png'),
          time: '20',
          level: '',
          url: '@mikesmith',
        },
        {
          id: 10,
          slug: 'cocktail_10',
          title: 'Cocktail #10',
          description: 'Lorem ipsum dolor sit amet, consectetur adipiscing elit. Aenean efficitur sit amet massa fringilla egestas. Nullam condimentum luctus turpis.',
          image: require('../assets/img/cocktail1.jpg'),
          icon: require('../assets/img/cocktail-glass-icon.png'),
          time: '15',
          level: '',
          url: '@alexsmith',
        },
        {
          id: 11,
          slug: 'cocktail_11',
          title: 'Cocktail #11',
          description: 'Lorem ipsum dolor sit amet, consectetur adipiscing elit. Aenean efficitur sit amet massa fringilla egestas. Nullam condimentum luctus turpis.',
          image: require('../assets/img/cocktail3.jpg'),
          icon: require('../assets/img/cocktail-vine-icon.png'),
          time: '10',
          level: '',
          url: '@alexsmith',
        },
      ],
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
  components: {
    'cocktail-list': CocktailList,
//      'item': CocktailItem
  },
  methods: {
//    goToCocktail: function (item) {
//      this.$router.push(`/cocktail/${item.slug}`);
//    },
//    goToArticle: function (item) {
//      this.$router.push(`/article/${item.slug}`);
//    },
    changeLevel: function (event) {
		this.filter_model.level = event.target.value;
    },
    changeStrong: function (event) {
      this.filter_model.strong = event.target.value;
    },
    changeIngredient: function (event) {
      this.filter_model.ingredient = event.target.value;
	},
    findCocktail: function(event) {
		debugger;
		//send server request (this.filter_model)
	  axios.get({url: '/', data: this.filter_model})
		.then(response => {
		  debugger;
		})
		.catch(er => {
		  debugger;
		});
	},
    onClickShowMore: function() {
      debugger;
	}
  }
}
</script>

<style lang="sass" scoped>
	@import '~assets/css/vars.sass'

	.recipes

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

			@media #{$tabletdesk}
				margin-right: 20px

		&__list-overflow
			background-color: $white
			border-radius: 5px
			box-shadow: 0 15px 15px rgba(0,0,0,0.15)

			@media #{$mobile}
				padding: 20px .75em

			@media #{$tabletdesk}
				padding: .75em

		&__list

		&__mob-filter

			@media #{$mobile}
				width: 90%
				margin: 0 auto
				padding-bottom: 0

			@media #{$tabletdesk}
				display: none


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


		&__filter,
		&__article,
		&__event
			background-color: $white

			@media #{$mobile}
				width: 90%
				margin: 0 auto
				padding: 20px 0.75em

			@media #{$tabletdesk}
				width: 100%
				padding: 0.75em
				margin-bottom: 20px
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

		&__filter-item
			width: 100%

			@media #{$mobile}
				height: 40px


			&.input
				&:focus,
				&:active
					border-color: $blue
					box-shadow: 0 0 0 0.125em rgba(46, 148, 137, .25)

			&.select

				select
					&:focus,
					&:active
						border-color: $blue
						box-shadow: none
						/*box-shadow: 0 0 0 0.125em rgba(46, 148, 137, .25)*/

			select,
			input
				width: 100%

			&:after
				border-color: $blue

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
