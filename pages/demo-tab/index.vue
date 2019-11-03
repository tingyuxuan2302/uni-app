<template>
	<view>
		<Tab value="c">
			<TabPanel name="a" label="体育">1111</TabPanel>
			<TabPanel name="b" label="娱乐">2222</TabPanel>
			<TabPanel name="c" label="搞笑">3333</TabPanel>
			<TabPanel name="d" label="新闻">4444</TabPanel>
		</Tab>
	</view>
</template>

<script>
	import TabPanel from '../../components/tab/tabPanel.vue';
	import Tab from '../../components/tab/tabs.vue';
	export default {
		components: {
			Tab,
			TabPanel
		},
		data() {
			return {
				title: 'Hello'
			}
		},
		onLoad() {

		},
		methods: {

		}
	}
</script>

<style>
	.content {
		display: flex;
		flex-direction: column;
		align-items: center;
		justify-content: center;
	}

	.logo {
		height: 200upx;
		width: 200upx;
		margin-top: 200upx;
		margin-left: auto;
		margin-right: auto;
		margin-bottom: 50upx;
	}

	.text-area {
		display: flex;
		justify-content: center;
	}

	.title {
		font-size: 36upx;
		color: #8f8f94;
	}
</style>
