<template>
	<div>
		<MyImage
			:imgUrl="imgUrl_1"
			className="img"
			:errDefImgUrl="imgUrl_2"
		></MyImage>
		<MyImage
			:imgUrl="imgUrl"
			className="img"
			@imgError="imgError"
		></MyImage>
		<MyImage
			:imgUrl="imgUrl_2"
			className="img"
			@imgError="imgError"
		></MyImage>
		<MyImage
			:imgUrl="imgUrl"
			className="img"
			@imgError="imgError"
		></MyImage>
		<MyImage
			:imgUrl="imgUrl"
			className="img"
			@imgError="imgError"
		></MyImage>
	</div>
	
</template>

<script>
	import MyImage from '@/components/my-image/my-image.vue';
	export default {
		components: {
			MyImage
        },
        data() {
            return {
				// 不可用图片
                imgUrl: 'http://dmimg.5054399.com/allimg/pkm/pk/22.jpg',
				imgUrl_1: 'http://dmimg.5054399.com/allimg/pk/22.jpg',
				// 可用图片
                imgUrl_2: 'https://wapimg.66826.com/Thumb/2018/1225/a72091ef04391b7d8b7b89fb5e74ec13.jpg',
            }
        },
		methods: {
			imgError(e) {
                console.log(e);
            }
		}
	}
</script>

<style lang="less">
    .img {
        width: 200px;
        height: 200px;
    }
</style>
