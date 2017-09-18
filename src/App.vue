<template>
	<v-app>
		<!-- <v-container fluid> -->
			<v-layout column style="background:#FFFFFF">
				<v-flex xs12 style="background:#223F6D">
					<div class="pt-1">
						<v-layout row>
							<v-flex xs2></v-flex>
							<v-flex xs5>
								<img class="mr-1 hdrImg" src="/static/facebook_icon.png" href="#" />
								<img class="mr-1 hdrImg" src="/static/Twitter_icon.png" href="#" />
								<img class="mr-1 hdrImg" src="/static/Linkedin_icon.png" href="#" />
								<img class="mr-1 hdrImg" src="/static/Youtube_icon.png" href="#" />
							</v-flex>
						</v-layout>
					</div>
				</v-flex>
				<v-flex xs12>
					<v-layout row class="ma-3">
						<v-flex xs2></v-flex>
						<v-flex class="text-xs-right">
							<v-btn flat style="mergin:6px 0;">ABOUT</v-btn>
							<v-btn flat style="mergin:6px 0;">MEMBERSHIP BENEFITS</v-btn>
							<v-btn flat style="mergin:6px 0;">RESOURCES</v-btn>
							<v-btn flat style="mergin:6px 0;">BLOG</v-btn>
							<v-btn flat style="mergin:6px 0;">CONTACT</v-btn>
							<v-btn style="background:#F1C400;color:#33260F;margin-right:0;">CLAIM FREE REPORT</v-btn>
							<v-btn style="background:#223F6D;color:#FFF;margin-left:0;">LOGIN</v-btn>
						</v-flex>
						<v-flex xs2></v-flex>
					</v-layout>
				</v-flex>
				<v-flex xs12 style="background:#5277AC">
					<v-layout row class="ma-3">
						<v-flex xs2></v-flex>
						<v-flex class="ma-2">
							<v-btn class="amber btncls" active="" @mouseover="hoverEvnt" :style="hoverStyle" outline dark>ALL</v-btn>
							<v-btn class="amber btncls" @hover="hoverEvnt" :style="hoverStyle" outline dark>INVESTMENTS</v-btn>
							<v-btn class="amber btncls" @btn--hover="hoverEvnt" :style="hoverStyle" outline dark>FINANCE</v-btn>
							<v-btn class="amber btncls" outline dark>CREDIT</v-btn>
							<v-btn class="amber btncls" outline dark>OTHER</v-btn>
							<v-btn class="amber btncls" outline dark>MORE</v-btn>
							<v-btn class="amber btncls" outline dark>FAMILY</v-btn>
							<v-btn class="amber btncls" outline dark>RUPEE</v-btn>
						</v-flex>
						<v-flex xs2></v-flex>
					</v-layout>
				</v-flex>
				<v-flex xs12>
					<v-layout row class="mt-3">
						<v-flex xs2></v-flex>
						<v-flex xs10 class="text-xs-right">
							<v-breadcrumbs divider="/" style="justify-content:left;">
								<v-breadcrumbs-item v-for="item in brdCrmbsItms" :key="item.text" :disabled="item.disabled">
									<b v-if="!item.disabled" style="color:#5277AC;">
										{{ item.text }}
									</b>
									<b v-else>
										{{ item.text }}
									</b>
								</v-breadcrumbs-item>
							</v-breadcrumbs>
						</v-flex>
					</v-layout>
				</v-flex>
				<v-flex xs12>
					<v-layout row class="mt-3">
						<v-flex xs2></v-flex>
						<v-flex xs6 class="mr-5">
							<v-card flat v-for="post in posts" :key="post.title" class="grey--text text--darken-2">
								<span style="font-size:32px;" class="mt-3">{{ post.title }}</span>
								<div class="mt-3">
									<span style="color:grey">POSTED BY </span>
									<strong>{{ post.author }}</strong>
									<span style="color:grey"> ON </span>
									<strong>{{ cnvrtDate(post.date) }}</strong>
								</div>
								<v-card-media :src="post.image" height="400px" class="mt-3"></v-card-media>
								<v-card-text style="font-size:16px;">{{ concatStr(post.description) }}</v-card-text>
								<v-card-actions class="mb-3">
									<v-btn :href="post.link" flat style="color:#5277AC;">READ MORE</v-btn>
								</v-card-actions>
							</v-card>
						</v-flex>
						<v-flex xs2 class="ml-5">
							<h4 style="color:#223E6E;">Popular Posts</h4>
							<v-card flat v-for="post in popularPost" :key="post.title">
								<v-card-media :src="post.image" height="170px" class="mt-2"></v-card-media>
								<p style="color:#5277AC;font-size:16px;" class="mt-2">{{ post.title }}</p>
								<p class="grey--text text--darken-1" style="font-size:16px;">{{ post.desc }}</p>
							</v-card>
							<h4 class="grey--text text--darken-1 mt-5">Tasks</h4>
							<v-btn outline style="color:#22426B;border-radius: 5px;" v-for="tag in tags" :key="tag">{{ tag }}</v-btn>
						</v-flex>
						<v-flex xs2></v-flex>
					</v-layout>
						<v-divider style="color:#C4C4C4;height:2px;"></v-divider>
						<v-flex xs12 style="height:50px;"></v-flex>
						<v-layout row>
							<v-flex xs2></v-flex>
							<v-flex xs3 class="mt-5">
								<img src="/static/Blog_Map.jpg" height="100px" class="my-3"/>
								<v-layout row>
									<v-flex xs4>
										<span class="grey--text text--lighten">FOLLOW US</span>
									</v-flex>
									<v-flex xs8>
										<v-spacer></v-spacer>
										<img class="mr-1 fbImg" src="/static/facebook_Blk_icon.png" href="#" />
										<img class="mr-1 fbImg" src="/static/Twitter_Blk_icon.png" href="#" />
										<img class="mr-1 fbImg" src="/static/Linkedin_Blk_icon.png" href="#" />
										<img class="mr-1 fbImg" src="/static/Youtube_Blk_icon.png" href="#" />
									</v-flex>
								</v-layout>
							</v-flex>
							<v-flex xs2>
								<div class="headline mb-3">QUICK LINKS</div>
								<v-list dense>
									<v-list-tile tag="p" v-for="list in ftrList" :key="list.title" :href="list.link">
										<v-list-tile-title>{{ list.title }}</v-list-tile-title>
									</v-list-tile>
								</v-list>
							</v-flex>
							<v-flex xs3 class="mb-5">
								<div class="headline mb-3">DOWNLOAD FREE EBOOK</div>
								<v-form v-model="valid">
									<v-text-field
										box
										label="Name"
										v-model="name"
										prepend-icon="person"
										:rules="nameRules"
										required
									></v-text-field>
									<v-text-field
										box
										label="Email"
										v-model="email"
										prepend-icon="email"
										:rules="emailRules"
										required
									></v-text-field>
									<v-btn @click="submit" style="background:#F1C400;color:#33260F;margin-right:0;width:50%">DOWNLOAD BOOK</v-btn>
								</v-form>
							</v-flex>
						</v-layout>
						<v-layout row>
							<v-flex xs2></v-flex>
							<v-flex xs8>
								<v-divider style="color:#C4C4C4;height:2px;"></v-divider>
								<div class="text-xs-center my-3">2017 © All rights reserved</div>
							</v-flex>
							<v-flex xs2></v-flex>

						</v-layout>
				</v-flex>
			</v-layout>
		<!-- </v-container> -->
	</v-app>
</template>

<script>
import moment from 'moment'
export default {
	data: () => ({
		hoverStyle: '',
		brdCrmbsItms: [
			{
				text: 'HOME',
				disabled: false
			},
			{
				text: 'BLOG',
				disabled: true
			}
		],
		posts: [
			{
				title: 'Lorem Ipsum is simply dummy text of the printing and typesetting industry',
				image: '/static/Blog_pic.jpg',
				author: 'MANISH CHAUHAN',
				date: '2016-02-12T03:16:00Z',
				description: 'Lorem Ipsum is simply dummy text of the printing and typesetting industry. Lorem Ipsum has been the industry\'s standard dummy text ever since the 1500s, when an unknown printer took a galley of type and scrambled it to make a type specimen book. It has survived not only five centuries, but also the leap into electronic typesetting, remaining essentially unchanged. It was popularised in the 1960s with the release of Letraset sheets containing Lorem Ipsum passages, and more recently with desktop publishing software like Aldus PageMaker including versions of Lorem Ipsum.',
				link: '#'
			},
			{
				title: 'Lorem Ipsum is simply dummy text of the printing and typesetting industry',
				image: '/static/Blog_pic1.jpg',
				author: 'MANISH CHAUHAN',
				date: '2016-12-12T10:32:00Z',
				description: 'Lorem Ipsum is simply dummy text of the printing and typesetting industry. Lorem Ipsum has been the industry\'s standard dummy text ever since the 1500s, when an unknown printer took a galley of type and scrambled it to make a type specimen book. It has survived not only five centuries, but also the leap into electronic typesetting, remaining essentially unchanged. It was popularised in the 1960s with the release of Letraset sheets containing Lorem Ipsum passages, and more recently with desktop publishing software like Aldus PageMaker including versions of Lorem Ipsum.',
				link: '#'
			},
			{
				title: 'Lorem Ipsum is simply dummy text of the printing and typesetting industry',
				image: '/static/Blog_pic2.jpg',
				author: 'MANISH CHAUHAN',
				date: '2017-01-27T17:51:00Z',
				description: 'Lorem Ipsum is simply dummy text of the printing and typesetting industry. Lorem Ipsum has been the industry\'s standard dummy text ever since the 1500s, when an unknown printer took a galley of type and scrambled it to make a type specimen book. It has survived not only five centuries, but also the leap into electronic typesetting, remaining essentially unchanged. It was popularised in the 1960s with the release of Letraset sheets containing Lorem Ipsum passages, and more recently with desktop publishing software like Aldus PageMaker including versions of Lorem Ipsum.',
				link: '#'
			},
			{
				title: 'Lorem Ipsum is simply dummy text of the printing and typesetting industry',
				image: '/static/Blog_pic3.jpg',
				author: 'MANISH CHAUHAN',
				date: '2017-01-27T17:51:00Z',
				description: 'Lorem Ipsum is simply dummy text of the printing and typesetting industry. Lorem Ipsum has been the industry\'s standard dummy text ever since the 1500s, when an unknown printer took a galley of type and scrambled it to make a type specimen book. It has survived not only five centuries, but also the leap into electronic typesetting, remaining essentially unchanged. It was popularised in the 1960s with the release of Letraset sheets containing Lorem Ipsum passages, and more recently with desktop publishing software like Aldus PageMaker including versions of Lorem Ipsum.',
				link: '#'
			}
		],
		popularPost: [
			{
				image: '/static/Blog_img.jpg',
				title: 'What people consider themselves?',
				desc: '70% investors are "Asset Poor" - What about you?'
			},
			{
				image: '/static/Blog_img1.jpg',
				title: 'What people consider themselves?',
				desc: '70% investors are "Asset Poor" - What about you?'
			},
			{
				image: '/static/Blog_img2.jpg',
				title: 'What people consider themselves?',
				desc: '70% investors are "Asset Poor" - What about you?'
			},
			{
				image: '/static/Blog_img3.jpg',
				title: 'What people consider themselves?',
				desc: '70% investors are "Asset Poor" - What about you?'
			}
		],
		tags: ['Investments','Finance','Tradings','Insurance','Webinars','Financial Planning','Mutual Funds','eBooks','Memberships'],
		ftrList: [
			{
				title: 'Existing Members? Login',
				link: '#'
			},
			{
				title: 'Blogs',
				link: '#'
			},
			{
				title: 'Webinars',
				link: '#'
			},
			{
				title: 'Videos',
				link: '#'
			},
			{
				title: 'eBooks',
				link: '#'
			},
			{
				title: 'Customer Service',
				link: '#'
			}
		]
	}),
	methods: {
		hoverEvnt () {
			this.hoverStyle = 'background-color:red;'
		},
		concatStr (str) {
			return str.substring(0,300) + ' ...'
		},
		cnvrtDate (date) {
			return moment(date).utcOffset(-0, false).format('ddd, MMM Do YYYY, hh:mm A')
		}
	}
}
</script>

<style>
	.btncls {
		margin: 6px -2px;
		border-radius: 0;
		font-size:17px;
		min-width: 130px;
	}
	.btn:focus {
		background-color: #F1C400;
	}
	.fbImg {
		border-radius:50%;
		border:2px solid #C4C4C4;
		padding: 5px;
	}
	.fbImg:hover {
		opacity: 0.5;
		cursor: pointer;
	}
	.hdrImg:hover {
		opacity: 0.7;
		cursor: pointer;
	}
</style>
