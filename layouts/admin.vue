<template lang="pug">
	.website.admin
		my-panel
		.admin__content
			nuxt

</template>

<script>
  import MyPanel from '~/components/Panel.vue'

  export default {
    components: {
      MyPanel
    },
  }
</script>

<style lang="sass" src="bulma"></style>

<style lang="sass" scoped>
	@import '../assets/css/vars.sass'

	.website
		width: 100%
		margin: 0 auto
		color: $black
		@include font(400)

		@media #{$desktop}
			width: 1280px

	.admin
		padding-left: 260px

		&__content
			padding: 20px

</style>
