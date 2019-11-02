<template>
	<view :class="['panel', className]" v-show="show">
		<slot></slot>
	</view>
	
</template>

<script>
	export default {
	    name: 'panel',
	    props: {
			//设置panel的标识
			name:{
				type:String,
			},
			//label是设置标题
			label:{
				type:String,
				default:''
			},
			className: String
	    },
		data() {
			return {
				show: true
			}
		},
		// mounted(){
		// 	//初始化tabs
		// 	this.$parent.updateNav();
		// }
	}
</script>

