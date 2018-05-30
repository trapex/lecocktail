<template lang="pug">
	nuxt-child
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
        title: 'Admin of Lecocktail'
      }
    },
	layout: 'admin',
    data () {
      return {
        title: 'Admin of Lecocktail',
      }
    },
  }
</script>

<style lang="sass" scoped>
	@import '~assets/css/vars.sass'

</style>
