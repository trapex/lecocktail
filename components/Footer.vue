<template lang="pug">
	footer
		p Created by Malysh and Zaynechka
</template>

<style lang="sass" scoped>
	@import '../assets/css/vars.sass'

	footer
		position: absolute
		width: 100%
		bottom: 0
		background-color: $gray--dark
		padding: 20px 0
		border-top: 1px solid #e1e1e1
		color: $white
		//@include font(400)

		@media #{$desktop}
			margin-top: 20px

</style>
