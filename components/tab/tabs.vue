<template>
<view class="tabs-box">
	<view class="tabs-bar">
		<view
			:class="['tabs-tab',{'tabs-active': item.name === currentName}]"
			@click="handleChange(index)"
			v-for="(item, index) in navList"
			:key="item.name">{{item.label}}</view>
	</view>
	<view class="tabs-content">
		<slot></slot>
	</view>
		
</view>
	
</template>
<script>
	export default {
		name: 'tab',
		props: {
			// 默认展示的tab标签,对应panel的name值
			value: {
				type: String,
				default: ''
			}
		},
		data() {
			return {
				//将panel的标题保存到数组中
				navList: [],
				//保存父组件的value到currentName变量中，以便在本地维护
				currentName: this.value
			}
			
		},
		mounted() {
			this.updateNav();
		},
		methods: {
			// 获取有效标签
			getTabs() {
				return this.$children.filter(item => item.$options.name === 'panel')
			},
			// 渲染tab标签并展示对应的panel；
			updateNav() {
				this.navList = [];
				const _this = this;
				this.getTabs().forEach((panel, index) => {
					_this.navList.push({
						label: panel.label,
						name: panel.name
					});
					//设置第一个tab为当前显示的tab
					if(index === 0 && _this.currentName === "") {
						_this.currentName = panel.name;
					}
				});
				this.updateStatus();
			},
			// 更新实例的show状态
			updateStatus() {
				let tabs = this.getTabs(),
				_this = this;
				//显示当前选中的tab对应的panel组件，隐藏没有选中的
				tabs.forEach(function(tab) {
					return tab.show = tab.name === _this.currentName;
				});
				console.log(tabs);
			},
			//点击tab标题触发
			handleChange(index) {
				var nav = this.navList[index];
				var name = nav.name;
				//改变当前选中的tab，触发watch
				this.currentName = name;
				this.$emit('getName', name);
			}
		},
		watch: {
			currentName: function() {
				//tab发生变化时，更新panel的显示状态
				this.updateStatus();
			}
		}
	}
</script>
<style lang="less">
	@import './tab.less';
</style>


