<template lang="pug">
	section.page.index
		.index__banner
			svg#example(viewbox='0 0 100% 100%')
				defs
					mask#mask-1(x='0', y='0', width='100%', height='100%')
						rect.part(x='0', y='0', width='0', height='10.2%', fill='#fff')
						rect.part(x='0', y='10%', width='0', height='10.2%', fill='#fff')
						rect.part(x='0', y='20%', width='0', height='10.2%', fill='#fff')
						rect.part(x='0', y='30%', width='0', height='10.2%', fill='#fff')
						rect.part(x='0', y='40%', width='0', height='10.2%', fill='#fff')
						rect.part(x='0', y='50%', width='0', height='10.2%', fill='#fff')
						rect.part(x='0', y='60%', width='0', height='10.2%', fill='#fff')
						rect.part(x='0', y='70%', width='0', height='10.2%', fill='#fff')
						rect.part(x='0', y='80%', width='0', height='10.2%', fill='#fff')
						rect.part(x='0', y='90%', width='0', height='10.2%', fill='#fff')
						rect.full(x='0', y='0', width='100', height='100', fill='#fff', opacity='0')
					mask#mask-2(x='0', y='0', width='100%', height='100%')
						rect.part(x='0', y='0', width='10.2%', height='0', fill='#fff')
						rect.part(x='10%', y='0', width='10.2%', height='0', fill='#fff')
						rect.part(x='20%', y='0', width='10.2%', height='0', fill='#fff')
						rect.part(x='30%', y='0', width='10.2%', height='0', fill='#fff')
						rect.part(x='40%', y='0', width='10.2%', height='0', fill='#fff')
						rect.part(x='50%', y='0', width='102%', height='0', fill='#fff')
						rect.part(x='60%', y='0', width='10.2%', height='0', fill='#fff')
						rect.part(x='70%', y='0', width='10.2%', height='0', fill='#fff')
						rect.part(x='80%', y='0', width='10.2%', height='0', fill='#fff')
						rect.part(x='90%', y='0', width='10.2%', height='0', fill='#fff')
						rect.full(x='0', y='0', width='100%', height='100', fill='#fff', opacity='0')
					mask#mask-3(x='0', y='0', width='100%', height='100%')
						rect.part(x='100%', y='0', width='100%', height='10.2%', fill='#fff')
						rect.part(x='100%', y='10%', width='100%', height='10.2%', fill='#fff')
						rect.part(x='100%', y='20%', width='100%', height='10.2%', fill='#fff')
						rect.part(x='100%', y='30%', width='100%', height='10.2%', fill='#fff')
						rect.part(x='100%', y='40%', width='100%', height='10.2%', fill='#fff')
						rect.part(x='100%', y='50%', width='100%', height='10.2%', fill='#fff')
						rect.part(x='100%', y='60%', width='100%', height='10.2%', fill='#fff')
						rect.part(x='100%', y='70%', width='100%', height='10.2%', fill='#fff')
						rect.part(x='100%', y='80%', width='100%', height='10.2%', fill='#fff')
						rect.part(x='100%', y='90%', width='100%', height='10.2%', fill='#fff')
						rect.full(x='0', y='0', width='100%', height='100', fill='#fff', opacity='0')
					mask#mask-4(x='0', y='0', width='100%', height='100%')
						rect.part(x='0', y='100%', width='10.2%', height='100%', fill='#fff')
						rect.part(x='10%', y='100%', width='10.2%', height='100%', fill='#fff')
						rect.part(x='20%', y='100%', width='10.2%', height='100%', fill='#fff')
						rect.part(x='30%', y='100%', width='10.2%', height='100%', fill='#fff')
						rect.part(x='40%', y='100%', width='10.2%', height='100%', fill='#fff')
						rect.part(x='50%', y='100%', width='10.2%', height='100%', fill='#fff')
						rect.part(x='60%', y='100%', width='10.2%', height='100%', fill='#fff')
						rect.part(x='70%', y='100%', width='10.2%', height='100%', fill='#fff')
						rect.part(x='80%', y='100%', width='10.2%', height='100%', fill='#fff')
						rect.part(x='90%', y='100%', width='10.2%', height='100%', fill='#fff')
						rect.full(x='0', y='0', width='100%', height='100%', fill='#fff', opacity='0')
				image(width='100%', height='100%', xlink:href='../assets/img/banner-bg1.jpg')
				image(width='100%', height='100%', xlink:href='../assets/img/banner-bg2.jpg', mask='url(#mask-1)')
				image(width='100%', height='100%', xlink:href='../assets/img/banner-bg3.jpg', mask='url(#mask-2)')
				image(width='100%', height='100%', xlink:href='../assets/img/banner-bg4.jpg', mask='url(#mask-3)')
				image(width='100%', height='100%', xlink:href='../assets/img/banner-bg1.jpg', mask='url(#mask-4)')
			h1.index__title {{ title }}
			.index__subtitle {{ subtitle }}
			nuxt-link.button(to="/recipes") подобрать
		.index__content
			.index__latest
				h2.index__latest-title Топ коктейлей
				cocktail-list(:list="latestList")
				//.index__latest-list.columns.is-multiline
					.index__latest-item.column.is-one-third-desktop.is-half-tablet(v-for='latestItem in latestList', :key='latestItem.id', @click='goToCocktail(latestItem)')
						.box
							.index__latest-item-img(:style="{backgroundImage: `url(${latestItem.image})`}")
							.index__latest-item-content
								.index__latest-item-title
									| {{latestItem.title}}
									br
									//| {{latestItem.description}}
								.index__latest-item-bottom
									.index__latest-item-info
										.index__latest-item-icon
										.index__latest-item-time
											svg(width='18px', height='19px', viewbox='0 0 18 19', data-reactid='495')
												g#Symbols(stroke='none', stroke-width='1', fill='none', fill-rule='evenodd', stroke-linecap='round', stroke-linejoin='round', data-reactid='496')
													g(id='Block-/-1:3-/-Recepie-Preview', transform='translate(-237.000000, -317.000000)', stroke='#59595b', data-reactid='497')
														g(id='Icon-20-/-Gray-/-Clock', transform='translate(233.000000, 313.000000)', data-reactid='498')
															ellipse#Oval-41(cx='12.9807692', cy='13.5', rx='8.17307692', ry='8.5', data-reactid='499')
															path#Line(d='M12.4699519,14.03125 L16.5564904,14.03125', data-reactid='500')
															path#Line(d='M12.4699519,7.65625 L12.4699519,14.03125', data-reactid='501')
											.index__latest-item-time-text 40 мин
									.index__latest-item-link
							.index__latest-item-hover
								.index__latest-item-hover-title
									| Ингредиенты
								.index__latest-item-hover-ingrefients
									| {{latestItem.description}}

								//a.index__latest-item-link(@click='goToCocktail(latestItem)') смотреть


</template>

<script>
  /* eslint-disable */
  import axios from '~/plugins/axios'
  import CocktailList from '@/components/CocktailList';
  import anime from 'animejs';
//  import CocktailItem from '@/components/CocktailItem';

  export default {
//    async asyncData () {
//      let {data} = await axios.get('/api/users')
//      return {users: data}
//    },
    head () {
      return {
        title: 'Le cocktail'
      }
    },
    mounted() {
      let timeline = anime.timeline({
        loop: true
      });
      this.title = 'Welcome welcome to Le cocktail!';
      timeline
        .add({
          targets: '#mask-1 .part',
          width: '100%',
          easing: 'easeInOutQuad',
          delay: function(el, i, l) {
            return 700 * Math.random();
          }
        })
        .add({
          targets: '#mask-2 .part',
          height: '100%',
          easing: 'easeInOutQuad',
          delay: function(el, i, l) {
            return 700 * Math.random();
          }
        })
        .add({
          targets: '#mask-3 .part',
          x: 0,
          easing: 'easeInOutQuad',
          delay: function(el, i, l) {
            return 700 * Math.random();
          }
        })
        .add({
          targets: '#mask-4 .part',
          y: 0,
          easing: 'easeInOutQuad',
          delay: function(el, i, l) {
            return 700 * Math.random();
          }
        });
    },
    components: {
      'cocktail-list': CocktailList,
//      'item': CocktailItem
	},
    data () {
      return {
        title: 'Welcome to Le cocktail!',
        subtitle: 'Подобрать коктейль и приготовить дома',
        latestList: [
          {
            id: 1,
			slug: 'cocktail_1',
            title: 'Cocktail #1',
            description: 'Lorem ipsum dolor sit amet, consectetur adipiscing elit. Aenean efficitur sit amet massa fringilla egestas. Nullam condimentum luctus turpis.',
            image: require('../assets/img/cocktail1.jpg'),
			icon: require('../assets/img/cocktail-shot-icon.png'),
			time: '30',
			level: '',
            url: '@johnsmith',
          },
          {
            id: 2,
            slug: 'cocktail_2',
            title: 'Cocktail #2',
            description: 'Lorem ipsum dolor sit amet, consectetur adipiscing elit. Aenean efficitur sit amet massa fringilla egestas. Nullam condimentum luctus turpis.',
            image: require('../assets/img/cocktail2.jpg'),
            icon: require('../assets/img/cocktail-glass-icon.png'),
            time: '20',
            level: '',
            url: '@paulsmith',
          },
          {
            id: 3,
            slug: 'cocktail_3',
            title: 'Cocktail #3',
            description: 'Lorem ipsum dolor sit amet, consectetur adipiscing elit. Aenean efficitur sit amet massa fringilla egestas. Nullam condimentum luctus turpis.',
            image: require('../assets/img/cocktail3.jpg'),
            icon: require('../assets/img/cocktail-vine-icon.png'),
            time: '15',
            level: '',
            url: '@mikesmith',
          },
          {
            id: 4,
            slug: 'cocktail_4',
            title: 'Cocktail #4',
            description: 'Lorem ipsum dolor sit amet, consectetur adipiscing elit. Aenean efficitur sit amet massa fringilla egestas. Nullam condimentum luctus turpis.',
            image: require('../assets/img/cocktail4.jpg'),
            icon: require('../assets/img/cocktail-martini-icon.png'),
            time: '40',
            level: '',
            url: '@alexsmith',
          },
          {
            id: 5,
            slug: 'cocktail_5',
            title: 'Cocktail #5',
            description: 'Lorem ipsum dolor sit amet, consectetur adipiscing elit. Aenean efficitur sit amet massa fringilla egestas. Nullam condimentum luctus turpis.',
            image: require('../assets/img/cocktail5.jpg'),
            icon: require('../assets/img/cocktail-shot-icon.png'),
            time: '20',
            level: '',
            url: '@alexsmith',
          },
          {
            id: 6,
            slug: 'cocktail_6',
            title: 'Cocktail #6',
            description: 'Lorem ipsum dolor sit amet, consectetur adipiscing elit. Aenean efficitur sit amet massa fringilla egestas. Nullam condimentum luctus turpis.',
            image: require('../assets/img/cocktail2.jpg'),
            icon: require('../assets/img/cocktail-vine-icon.png'),
            time: '10',
            level: '',
            url: '@mikesmith',
          },
          {
            id: 7,
            slug: 'cocktail_7',
            title: 'Cocktail #7',
            description: 'Lorem ipsum dolor sit amet, consectetur adipiscing elit. Aenean efficitur sit amet massa fringilla egestas. Nullam condimentum luctus turpis.',
            image: require('../assets/img/cocktail5.jpg'),
            icon: require('../assets/img/cocktail-glass-icon.png'),
            time: '15',
            level: '',
            url: '@alexsmith',
          },
          {
            id: 8,
            slug: 'cocktail_8',
            title: 'Cocktail #8',
            description: 'Lorem ipsum dolor sit amet, consectetur adipiscing elit. Aenean efficitur sit amet massa fringilla egestas. Nullam condimentum luctus turpis.',
            image: require('../assets/img/cocktail4.jpg'),
            icon: require('../assets/img/cocktail-martini-icon.png'),
            time: '40',
            level: '',
            url: '@alexsmith',
          },
        ]
      }
    },

  }
</script>

<style lang="sass" scoped>
	@import '~assets/css/vars.sass'

	.index

		#example
			position: absolute
			display: none
			top: 0
			left: 0
			right: 0
			bottom: 0
			/*width: 100%*/
			min-width: 100%
			min-height: 100%
			/*box-shadow: 0 0 20px rgba(0, 0, 0, .7)*/

			@media #{$tabletdesk}
				display: block

			image
				position: absolute
				top: 0
				left: 0
				width: auto
				min-width: 100%
				height: auto
				min-height: 100%

				@media #{$tabletdesk}
					width: 100%
					height: auto

		&__content
			background-color: $white

			@media #{$desktop}
				max-width: 1280px
				margin: 20px auto 40px auto
				border-radius: 5px
				box-shadow: 0 15px 15px rgba(0,0,0,0.15)

		&__banner
			position: relative
			width: 100%
			height: 360px
			background-color: #e1e1e1
			background-image: url(../assets/img/banner-bg.jpg)
			background-position: center 30%
			background-repeat: no-repeat
			background-size: cover

			@media #{$mobile}
				padding: 50px 0

			@media #{$tablet}
				padding: 80px 0

			@media #{$desktop}
				padding: 80px 0

		&__title
			position: relative
			font-weight: 500
			text-align: center
			color: $white
			text-transform: uppercase

			@media #{$mobile}
				font-size: 36px

			@media #{$tablet}
				font-size: 36px

			@media #{$desktop}
				font-size: 48px

		&__subtitle
			position: relative
			font-weight: 300
			text-align: center
			color: $white

			@media #{$mobile}
				margin-top: 20px
				font-size: 18px

		&__latest
			padding: 20px 20px 40px 20px

			@media #{$desktop}
				padding: 20px 20px 60px 20px

		&__latest-title

			@media #{$mobile}
				font-size: 24px

			@media #{$tablet}
				font-size: 36px

			@media #{$desktop}
				font-size: 36px

		&__latest-list
			margin-top: 10px

		.button
			display: block

			@media #{$mobile}
				margin: 30px auto 0 auto
				@include customBtn(150px, 40px, $blue, $white)

			@media #{$tablet}
				margin: 50px auto 0 auto
				@include customBtn(140px, 40px, $blue, $white)

			@media #{$desktop}
				margin: 50px auto 0 auto
				@include customBtn(150px, 40px, $blue, $white)



</style>
