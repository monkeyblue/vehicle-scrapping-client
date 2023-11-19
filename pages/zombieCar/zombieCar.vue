<template>
	<view class="zombieCar">
		
		<u-upload
		:fileList="fileList"
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
			deletePic(){

			},
			afterRead(){

			}
		}
	}
</script>
<style lang="scss">
	.zombieCar {
		padding: 30rpx;

		
		}
		</style>