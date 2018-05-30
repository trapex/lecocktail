<template lang="pug">
	.admin__content
		h2 Some text
		p Choose some of the category
		button(@click="$store.commit('increment')") {{ $store.state.counter }}
		nuxt-child
</template>

<script>
  /* eslint-disable */

  export default {
    head () {
      return {
        title: 'Cocktail in Le cocktail'
      }
    },
    data () {
      return {
        title: 'Welcome to Le cocktail2!',
      }
    },
  }
</script>

<style lang="sass" scoped>

</style>
