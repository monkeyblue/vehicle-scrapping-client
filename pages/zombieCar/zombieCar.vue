<template>
	<view class="content">
		<view class="top">
			<view class="title center">僵尸车线索提供</view>
		</view>
		<view class="bottom">
			<view class="cross">+</view>
			<view class="cross">+</view>
		</view>
	</view>
</template>
<script>
	export default {
		data() {
			return {

			};
		}
	}
</script>
<style lang="scss">
	.content {
		height: 100vh;
		

		.top {
			height: 40px;
			text-align: center;
			font-size:20px;
			line-height: 40px;
		}

		.bottom {
			padding-top: 30px;
			height: calc(100vh - 80px);
			background-color: white;
			display: flex;
			flex-direction: row;
			justify-content: space-around;
		}

		.cross {
			width: 100px;
			height: 100px;
			font-size: 40px;
			background: lightblue;
			display: flex;
			flex-direction: row;
			align-items: center;
			justify-content: center;
		}
		}
		</style>