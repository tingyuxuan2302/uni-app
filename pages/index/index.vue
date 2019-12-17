<template>
	<view class="container">
		<button @click="linkTo('/pages/demo-tab/index')">tab-demo</button>
		<button @click="linkTo('/pages/demo-image/index')">image-demo</button>
	</view>
</template>

<script>
	export default {
		data() {
			return {}
		},
		methods: {
			linkTo(url) {
				uni.navigateTo({
					url
				})
			}
		}
	}
</script>

<style>

</style>
