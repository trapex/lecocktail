<template lang="pug">
	section.index
		.index__banner
			h1.index__title.title.is-1 {{ msg }}
			nuxt-link.button.is-primary(to="/recipes") Recipes
		.columns.is-multiline
			.column
				h2.subtitle.is-3 Latest
				.box(v-for='latestItem in latestList', :key='latestItem.id')
					article.media
						.media-left
							figure.image.is-64x64
								img(src='../assets/img/watermark-image.png', alt='Image')
						.media-content
							.content
								p
									strong {{latestItem.title}}
									small {{latestItem.email}}
									br
									| {{latestItem.description}}
								a(@click='goToCocktail(latestItem)').button.is-primary подробнее
			.column.is-one-quarter
				h2.subtitle.is-3 Top 10
				.box(v-for='latestItem in latestList', :key='latestItem.id')
					article.media
						.media-left
							figure.image.is-64x64
								img(src='../assets/img/watermark-image.png', alt='Image')
						.media-content
							.content
								p
									strong {{latestItem.title}}
									a(@click='goToCocktail(latestItem)').button.is-primary подробнее
</template>

<script>
  /* eslint-disable */
  import axios from '~/plugins/axios'

  export default {
//    async asyncData () {
//      let {data} = await axios.get('/api/users')
//      return {users: data}
//    },
    head () {
      return {
        title: 'Le cocktail'
      }
    },
    data () {
      return {
        msg: 'Welcome to Le cocktail!',
        latestList: [
          {
            id: 1,
            title: 'Cocktail #1',
            description: 'Lorem ipsum dolor sit amet, consectetur adipiscing elit. Aenean efficitur sit amet massa fringilla egestas. Nullam condimentum luctus turpis.',
            image: '',
            url: '@johnsmith',
          },
          {
            id: 2,
            title: 'Cocktail #2',
            description: 'Lorem ipsum dolor sit amet, consectetur adipiscing elit. Aenean efficitur sit amet massa fringilla egestas. Nullam condimentum luctus turpis.',
            image: '',
            url: '@paulsmith',
          },
          {
            id: 3,
            title: 'Cocktail #3',
            description: 'Lorem ipsum dolor sit amet, consectetur adipiscing elit. Aenean efficitur sit amet massa fringilla egestas. Nullam condimentum luctus turpis.',
            image: '',
            url: '@mikesmith',
          },
          {
            id: 4,
            title: 'Cocktail #4',
            description: 'Lorem ipsum dolor sit amet, consectetur adipiscing elit. Aenean efficitur sit amet massa fringilla egestas. Nullam condimentum luctus turpis.',
            image: '',
            url: '@alexsmith',
          },
        ]
      }
    },
    methods: {
      goToCocktail: function (item) {
        this.$router.push(`/cocktail/${item.id}`);
	  }
    }
  }
</script>

<style lang="sass" scoped>
	.index

		&__banner
			width: 100%
			height: 400px
			padding: 100px 0
			background-color: #e1e1e1

		&__title
			text-align: center

		.button
			display: block
			width: 150px
			margin: 50px auto 0 auto


</style>
