<template lang="pug">
	section.page.article(v-if="article", :key="article.id")
		.article__item
			.article__image-wrap
				.article__image(:style="{backgroundImage: `url(${article.image})`}")
			.article__content
				.content
					//.article__item-title {{article.title}}
					.article__item-description(v-html="article.html")
					//.article__item-description {{article.description}} #[br] #[small Cocktail with id: {{article.id}}]
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
        title: 'Welcome to Le cocktail2!',
        subtitle: 'Готовьте коктейли дома вместе с Le Cocktail!',
		article: {
          id: 1,
          slug: 'articles_1',
          title: 'Articles #1',
          short_description: 'Short description of Article #1',
          description: 'Full description of Article #1 Full description of Article #1 Full description of Article #1',
          html: '<div class="content">\n' +
          '  <h1>Hello World</h1>\n' +
          '  <p>Lorem ipsum<sup><a>[1]</a></sup> dolor sit amet, consectetur adipiscing elit. Nulla accumsan, metus ultrices eleifend gravida, nulla nunc varius lectus, nec rutrum justo nibh eu lectus. Ut vulputate semper dui. Fusce erat odio, sollicitudin vel erat vel, interdum mattis neque. Sub<sub>script</sub> works as well!</p>\n' +
          '  <h2>Second level</h2>\n' +
          '  <p>Curabitur accumsan turpis pharetra <strong>augue tincidunt</strong> blandit. Quisque condimentum maximus mi, sit amet commodo arcu rutrum id. Proin pretium urna vel cursus venenatis. Suspendisse potenti. Etiam mattis sem rhoncus lacus dapibus facilisis. Donec at dignissim dui. Ut et neque nisl.</p>\n' +
          '  <ul>\n' +
          '    <li>In fermentum leo eu lectus mollis, quis dictum mi aliquet.</li>\n' +
          '    <li>Morbi eu nulla lobortis, lobortis est in, fringilla felis.</li>\n' +
          '    <li>Aliquam nec felis in sapien venenatis viverra fermentum nec lectus.</li>\n' +
          '    <li>Ut non enim metus.</li>\n' +
          '  </ul>\n' +
          '  <h3>Third level</h3>\n' +
          '  <p>Quisque ante lacus, malesuada ac auctor vitae, congue <a href="#">non ante</a>. Phasellus lacus ex, semper ac tortor nec, fringilla condimentum orci. Fusce eu rutrum tellus.</p>\n' +
          '  <ol>\n' +
          '    <li>Donec blandit a lorem id convallis.</li>\n' +
          '    <li>Cras gravida arcu at diam gravida gravida.</li>\n' +
          '    <li>Integer in volutpat libero.</li>\n' +
          '    <li>Donec a diam tellus.</li>\n' +
          '    <li>Aenean nec tortor orci.</li>\n' +
          '    <li>Quisque aliquam cursus urna, non bibendum massa viverra eget.</li>\n' +
          '    <li>Vivamus maximus ultricies pulvinar.</li>\n' +
          '  </ol>\n' +
          '  <blockquote>Ut venenatis, nisl scelerisque sollicitudin fermentum, quam libero hendrerit ipsum, ut blandit est tellus sit amet turpis.</blockquote>\n' +
          '  <p>Quisque at semper enim, eu hendrerit odio. Etiam auctor nisl et <em>justo sodales</em> elementum. Maecenas ultrices lacus quis neque consectetur, et lobortis nisi molestie.</p>\n' +
          '  <p>Sed sagittis enim ac tortor maximus rutrum. Nulla facilisi. Donec mattis vulputate risus in luctus. Maecenas vestibulum interdum commodo.</p></div>',
          image: require('../../assets/img/article_1.jpg')
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

	.article
		margin: 0 auto

		&__item
			margin: 0 auto 20px auto

			@media #{$mobile}
				max-width: 440px

			@media #{$tabletdesk}
				max-width: 1280px
				min-height: 400px

		&__image-wrap
			height: 250px
			padding: 0

			@media #{$desktop}
				height: 300px

		&__image
			width: 100%
			height: 100%
			background-size: cover
			background-repeat: no-repeat
			background-position: center

		&__item-description
			@include font(400)
			font-size: 16px

		&__item-title
			@include font(400)

			@media #{$mobile}
				font-size: 24px

			@media #{$tabletdesk}
				font-size: 36px

		&__content

			@media #{$mobile}
				width: 90%
				margin: 20px auto 0 auto

			@media #{$tabletdesk}
				padding: 0
				margin: 20px


</style>
