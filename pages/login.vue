<template lang="pug">
	section.login
		h1.title Логин
		.form
			.field
				p.control.has-icons-left.has-icons-right
					input.input(type='email', placeholder='Email')
					span.icon.is-small.is-left
						i.fa.fa-envelope
					span.icon.is-small.is-right
						i.fa.fa-check
			.field
				p.control.has-icons-left
					input.input(type='password', placeholder='Password')
					span.icon.is-small.is-left
						i.fa.fa-lock
			.field
				p.control
					button.button.is-success(v-on:click="sendForm")
						| Login
</template>

<script>
/* eslint-disable */
import axios from '~/plugins/axios'

export default {
	layout: 'admin',
	async asyncData() {
		let {data} = await axios.get('/api/users')
		return {users: data}
	},
	head() {
		return {
			title: 'Recipes of Le cocktail'
		}
	},
	data() {
		return {
			banner_msg: 'Some text for banner',
		}
	},
	methods: {
      sendForm: function() {

	  }
	}
}
</script>

<style lang="sass" scoped>
	@import '../assets/css/vars.sass'

	.login
		width: 100%
		height: 100%
		padding-top: 100px

		h1
			text-align: center

	.form
		width: 520px
		height: 300px
		padding: 30px
		margin: 50px auto
		border: 1px solid $gray

</style>
