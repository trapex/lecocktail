<template lang="pug">
	section.page
		//h1.admin__title {{title}}
		.admin__subtitle Категория: {{categoryRu}}
		.list
			.columns.list__item.is-mobile(v-for='item in list', :key='item.id')
				.column.list__item-id {{item.id}}
				.column.is-10.list__item-title {{item.title}}
				.column.columns.is-mobile.list__item-edit
					nuxt-link.column.icon(:to="{path: `/admin/${category}/edit/${item.id}`}", tag="span")
						i.fal.fa-edit
					span.column.icon.icon__cross(@click="deleteItem")
						i.fal.fa-times

</template>

<script>
  /* eslint-disable */
  import axios from '~/plugins/axios'
  import _ from 'underscore'

  var META_CATEGORY = [
    {
      name: 'recepies',
      nameRu: 'рецепты'
    },
    {
      name: 'articles',
      nameRu: 'статьи'
    },
    {
      name: 'ingredients',
      nameRu: 'ингредиенты'
    },
    {
      name: 'equipments',
      nameRu: 'оборудование'
    }
  ]

  export default {
//    async asyncData () {
//      let {data} = await axios.get('/api/users')
//      return {users: data}
//    },
    head () {
      return {
        title: 'Admin of Lecocktail'
      }
    },
	layout: 'admin',
    data () {
      return {
        title: 'Admin of Lecocktail',
		category: this.$route.params.category,
		list: [
		  {
		    id: 1,
			title: 'title 1 title 1 title 1 title 1title 1title 1title',
			slug: 'item_1'
		  },
          {
            id: 2,
            title: 'title 2',
            slug: 'item_2'
          },
          {
            id: 3,
            title: 'title 3',
            slug: 'item_3'
          }
		]
      }
    },
    mounted: () => {

    },
    computed: {
      categoryRu: function() {
        let t = _.findWhere(META_CATEGORY, {name: this.category});
        if (t) {
          return t.nameRu;
		} else {
          return 'неизвестно';
		}
	  }
	},
	methods: {
      deleteItem: () => {
        debugger;
	  }
	}

  }
</script>

<style lang="sass" scoped>
	@import '~assets/css/vars.sass'

	.list
		margin-top: 40px

		&__item

		&__item-edit

			.icon
				cursor: pointer

				&__cross
					line-height: 22px

			i
				font-family: fontawesome
				font-style: normal


</style>
