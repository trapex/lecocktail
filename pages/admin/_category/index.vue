<template lang="pug">
	.admin__content
		h2 Some category

</template>

<script>
  /* eslint-disable */

  export default {
    head () {
      return {
        title: 'Admin of Lecocktail'
      }
    },
	layout: 'admin',
	props: ['category'],
    data () {
      return {
        title: 'Admin of Lecocktail',
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
    mounted() {

    },

  }
</script>

<style lang="sass" scoped>
	@import '~assets/css/vars.sass'

</style>
