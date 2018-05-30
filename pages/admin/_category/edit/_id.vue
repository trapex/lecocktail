<template lang="pug">
	.item(:class="`item_${category}`")
		.item__title {{$route.params.id ? `Редактирование элемента: ${category} id= ${$route.params.id}`: `Добавление элемента: ${category}`}}
		.item__edit.item__edit_recepies
			.item__field.field
				label Название
				.control
					input.input(type="text", :value="$route.params.id? item.title: ''", @change="changeInput(item, $event)")
			.item__field.field
				label Slug
				.control
					input.input(type="text", :value="$route.params.id? item.slug: ''")
			.item__field.field
				label Level
				.control
					.select
						select
							option(value="new" selected) Новичок
							option(value="boss") Любитель
							option(value="professional") Профессионал
			.item__field.field
				label Крепкость
				.control
					.select
						select
							option(value="light" selected) Ligth
							option(value="middle") Middle
							option(value="strong") Strong
			.item__field.field
				label Картинка
				.control
					.file.has-name
						label.file-label
							input.file-input(type="file" name="image")
							span.file-cta
								span.file-icon
									i.fas.fa-upload
								span.file-label Choose a file…
							span.file-name
								| Screen Shot 2017-07-29 at 15.54.25.png
			.item__field.field
				label Ингредиенты
				.control
					multiselect(:options="ingredients", :multiple="true", :hide-selected="true", :placeholder ="'Добавить'", label="name", track-by="slug", :select-label="''", v-model="valueI")
			.item__field.field
				label Оборудование
				.control
					.control
					multiselect(:options="equipments", :multiple="true", :hide-selected="true", :placeholder ="'Добавить'", label="name", track-by="slug", :select-label="''", v-model="valueE")
			.item__field.field
				label Текст
				.control
					textarea.textarea(:value="$route.params.id? item.description: ''")

		.item__edit.item__edit_articles
			.item__field.field
				label Название
				.control
					input.input(type="text", :value="$route.params.id? item.title: ''")
			.item__field.field
				label Slug
				.control
					input.input(type="text", :value="$route.params.id? item.slug: ''")
			.item__field.field
				label Картинка
				.control
					.file.has-name
						label.file-label
							input.file-input(type="file" name="image")
							span.file-cta
								span.file-icon
									i.fas.fa-upload
								span.file-label Choose a file…
							span.file-name
								| Screen Shot 2017-07-29 at 15.54.25.png
			.item__field.field
				label Текст
				.control
					textarea.textarea(:value="$route.params.id? item.description: ''")

		.item__edit.item__edit_ingredients
			.item__field.field
				label Название
				.control
					input.input(type="text", :value="$route.params.id? item.title: ''")
			.item__field.field
				label Slug
				.control
					input.input(type="text", :value="$route.params.id? item.slug: ''")
			.item__field.field
				label Картинка
				.control
					.file.has-name
						label.file-label
							input.file-input(type="file" name="image")
							span.file-cta
								span.file-icon
									i.fas.fa-upload
								span.file-label Choose a file…
							span.file-name
								| Screen Shot 2017-07-29 at 15.54.25.png

		.item__edit.item__edit_equipments
			.item__field.field
				label Название
				.control
					input.input(type="text", :value="$route.params.id? item.title: ''")
			.item__field.field
				label Slug
				.control
					input.input(type="text", :value="$route.params.id? item.slug: ''")
			.item__field.field
				label Картинка
				.control
					.file.has-name
						label.file-label
							input.file-input(type="file" name="image")
							span.file-cta
								span.file-icon
									i.fas.fa-upload
								span.file-label Choose a file…
							span.file-name
								| Screen Shot 2017-07-29 at 15.54.25.png

		.item__field.item__field_btns.field.is-grouped
			.control
				.item__btn.button.is-success.is-outlined(@click="saveItem()") Сохранить
			.control
				.item__btn.button.is-danger.is-outlined(@click="$router.go(-1)") Отмена

</template>

<script>
  /* eslint-disable */

  import _ from 'underscore'
  import axios from 'axios'
  import Multiselect from 'vue-multiselect'

  axios.defaults.baseURL = 'http://localhost:3000/data/'

  export default {
    head () {
      return {
        title: 'Cocktail in Le cocktail'
      }
    },
    components: {
      Multiselect
    },
    data () {
      return {
        title: 'Редактирование элемента: ',
        subtitle: 'Готовьте коктейли дома вместе с Le Cocktail!',
		category: this.$route.params.category,
		valueI: [],
		valueE: [],
		ingredients: [
		  {name: 'Апельсиновый сок', slug: 'orange_juice'},
		  {name: 'Лимон', slug: 'lemon'},
		  {name: 'Лайм', slug: 'lime'}
		],
		equipments: [
		  {name: 'Рокс', slug: 'rox'},
		  {name: 'Стрейнер', slug: 'strainer'},
		  {name: 'Джиггер', slug: 'djigger'},
		  {name: 'Коктейльная ложка', slug: 'cocktail_spoon'}
		],
        item: {
          id: 0,
          slug: 'articles_1',
          title: 'Articles #1',
          short_description: 'Short description of Article#1',
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
          image: require('~/assets/img/article_1.jpg')
        }
      }
    },
    computed: {
      item_model: function () {

	  }
	},
	methods: {
      changeInput: (item, e) => {
        debugger;
	  },
      saveItem: (item) => {
		alert('item was saved');
	  },
	}
  }
</script>

<style lang="css" src="vue-multiselect/dist/vue-multiselect.min.css"></style>

<style lang="sass" scoped>
	@import '~assets/css/vars.sass'

	.control

		.multiselect__tag
			background-color: $blue

		.multiselect

			&__input
				width: 100%
				border-color: #dbdbdb
				height: 2.25em

			//&__select
				&:before
					border: 1px solid #3273dc
					border-right: 0
					border-top: 0
					content: " "
					display: block
					height: 0.5em
					pointer-events: none
					position: absolute
					-webkit-transform: rotate(-45deg)
					transform: rotate(-45deg)
					-webkit-transform-origin: center
					transform-origin: center
					width: 0.5em
					margin-top: -0.375em
					right: 1.125em
					top: 50%
					z-index: 4



			&__element

			&__option
				&--highlight
					background: $blue



	.item
		width: 640px

		&_recepies

			.item__edit_recepies
				display: block

			.item__edit_articles,
			.item__edit_ingredients,
			.item__edit_equipments
				display: none

		&_articles
			.item__edit_articles
				display: block

			.item__edit_recepies,
			.item__edit_ingredients,
			.item__edit_equipments
				display: none

		&_ingredients
			.item__edit_ingredients
				display: block

			.item__edit_recepies,
			.item__edit_articles,
			.item__edit_equipments
				display: none

		&_equipments
			.item__edit_equipments
				display: block

			.item__edit_recepies,
			.item__edit_ingredients,
			.item__edit_articles
				display: none

		&__title
			margin-top: 20px

		&__edit
			margin-top: 20px

		&__field
			width: 100%

			.select
				width: 100%

			input,
			select
				width: 100%

			textarea
				resize: none

			i
				font-family: fontawesome
				font-style: normal

			&_btns
				margin-top: 20px

</style>
