<template lang="pug">
	.website
		my-header
		nuxt
		my-footer

</template>

<script>
  import MyHeader from '~/components/Header.vue'
  import MyFooter from '~/components/Footer.vue'

  export default {
    head: {
      htmlAttrs: {
        lang: 'ru'
      },
      css: [
        'https://fonts.googleapis.com/css?family=Open+Sans:300,400,600,700',
        'https://fonts.googleapis.com/css?family=Montserrat|Open+Sans:300,400,600'
      ]
    },
    components: {
      MyHeader,
      MyFooter
    }
  }
</script>

<style lang="sass" src="bulma"></style>

<style lang="sass" scoped>
	@import '../assets/css/vars.sass'

	.website
		position: relative
		min-height: 100vh
		height: 100%
		width: 100%
		overflow: hidden
		margin: 0 auto
		color: $gray--dark
		@include font(400)
		background-color: $gray--light

		@media #{$desktop}

	.container
		margin: 0
		width: 100%
		padding: 100px 0
		text-align: center

	.button, .button:visited
		display: inline-block
		color: black
		letter-spacing: 1px
		background-color: #fff
		border: 2px solid #000
		text-decoration: none
		text-transform: uppercase
		padding: 15px 45px

	.button:hover, .button:focus
		color: #fff
		background-color: #000

	.title
		color: #000
		font-weight: 300
		font-size: 2.5em
		margin: 0

</style>
