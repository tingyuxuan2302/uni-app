<template>
	<image
		:src="defPic"
		:mode="imgMode"
		:lazy-load="imgLazyLoad"
		:fade-show="imgFadeShow"
		@error="MyImgError"
		@load="MyImgLoad"
		:class="className"
	></image>
</template>
	
<script>
	const DEFPHOTO = 'https://timgsa.baidu.com/timg?image&quality=80&size=b9999_10000&sec=1576595941414&di=83f062cc570e15b3a95b94274c018f33&imgtype=0&src=http%3A%2F%2Fcdn.duitang.com%2Fuploads%2Fitem%2F201411%2F23%2F20141123144736_2ntsu.thumb.700_0.jpeg'
	export default {
		name: 'my-photo',
		props: {
			// 图片地址
			imgUrl: {
				type: String,
				default: DEFPHOTO
			},
			// 错误图片默认展示
			errDefImgUrl: {
				type: String,
				default: DEFPHOTO
			},
			className: {
				type: String,
				default: ""
			},
			// 图片裁剪、缩放的模式
			imgMode: {
				type: String,
				default: 'scaleToFill'
			},
			// 图片懒加载。只针对page与scroll-view下的image有效
			imgLazyLoad: {
				type: Boolean,
				default: false
			},
			// 图片显示动画效果
			imgFadeShow: {
				type: Boolean,
				default: true
			},
			imgError: {
				type: Function,
				default: () => {}
			},
			imgLoad: {
				type: Function,
				default: () => {}
			}
		},
		data() {
			return {
				isLoaded: false, // 图片是否加载完成
				defPic: DEFPHOTO
			}
		},

		watch: {
			isLoaded(newVal) {
				this.defPic = newVal ? this.imgUrl : DEFPHOTO
			},
			imgUrl(newUrl) {
				this.defPic = newUrl;
			}
		},
		
		methods: {
			// 当错误发生时，发布到 AppService 的事件名，事件对象event.detail = {errMsg: 'something wrong'}
			MyImgError(e) {
				this.defPic = this.errDefImgUrl;
				this.imgError && this.$emit('imgError', e);
			},
			// 当图片载入完毕时，发布到 AppService 的事件名，事件对象event.detail = {height:'图片高度px', width:'图片宽度px'}
			MyImgLoad(e) {
				this.isLoaded = true;
				this.imgLoad && this.$emit('imgLoad', e);
			}
		}
	}
</script>

<style lang="less">
	image {
		width: 100%;
		height: 100%;
	}
</style>
