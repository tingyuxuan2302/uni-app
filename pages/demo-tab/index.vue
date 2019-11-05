<template>
	<view>
		<Tab value="c" @getName="handleChange">
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
			}
		},
		onLoad() {

		},
		methods: {
			handleChange(name, index) {
				console.log(name, index);
			}
		}
	}
</script>

<style>

</style>
