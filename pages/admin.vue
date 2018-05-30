<template lang="pug">
	section.page
		h1.admin__title {{title}}
		nuxt-child

</template>

<script>
  /* eslint-disable */
  import axios from '~/plugins/axios'
  import CocktailList from '@/components/CocktailList';
  import anime from 'animejs';

  export default {
    head () {
      return {
        title: 'Admin of LeCocktail'
      }
    },
	layout: 'admin',
    mounted() {

    },
    data () {
      return {
        title: 'Admin of LeCocktail!',
      }
    },

  }
</script>

<style lang="sass" scoped>
	@import '~assets/css/vars.sass'

	.admin
		&__title
			text-transform: uppercase

</style>
