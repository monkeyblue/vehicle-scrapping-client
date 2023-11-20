<template>
	<view class="zombieCar">
		
		<u-upload
		accept="image"
		:previewFullImage="true"
		:fileList="fileList"
		@before-upload="befores"
		@afterRead="afterRead"
		@delete="deletePic"
		name="1"
		multiple
		:maxCount="10"
	></u-upload>
	</view>
</template>
<script>
	export default {
		data() {
			return {
				fileList:[]
			};
		},
		methods:{
			befores(){
				console.log(123)
			},
			deletePic(){

			},
			afterRead(){
				console.log('2')
			}
		}
	}
</script>
<style lang="scss">
	.zombieCar {
		padding: 30rpx;

		
		}
		</style>