# 安装
`npm install uni-app-component`  
# 引用(在项目中引入对应组件)
`import ComponentName from 'uni-app-component/components/xxx/xxx.vue';` 
# 组件
## *1.tab*(demo：/pages/demo-tab)
```
	<template>
		<Tab value="c">
			<TabPanel name="a" label="体育">1111</TabPanel>
			<TabPanel name="b" label="娱乐">2222</TabPanel>
			<TabPanel name="c" label="搞笑">3333</TabPanel>
			<TabPanel name="d" label="新闻">4444</TabPanel>
		</Tab>
	</template>
    <script>
		import Tab from 'uni-app-component/components/tab/tabs.vue';
		import TabPanel from 'uni-app-component/components/tab/tabPanel.vue'; 
	</script>
```
组件参数：
---
tab
---  
参数|类型|默认值|描述
---|--|--|---
value|String|""|默认需要选中的tab标签
getName|Function|(name, index) => {}|标签选中的回调；  name: 对应标签的name；  index:对应标签的下标
---
tabPanel  
---
参数|类型|默认值|描述
---|--|--|---
name|String|""|设置panel的标识,对应tab的value
label|String|""|tab标签标题
className|String|""|class名