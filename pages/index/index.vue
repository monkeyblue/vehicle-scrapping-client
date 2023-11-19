<template>
	<view class="container">
    <view class="top">
      <view class="title center">车辆注销一件事</view>
      <view class="subtitle center">安全出行 文明交通</view>
    </view>
    <view class="bottom">
      <view class="item" @click="routerPush('/pages/notice/notice')">
        <view class="btn-text">车辆注销申请</view>
        <view class="btn-sub">前往注销></view>
      </view>
      <view class="item" @click="routerPush('/pages/search/search')">
        <view class="btn-text">我的业务</view>
        <view class="btn-sub">点击查看></view>
      </view>
      <view class="item">
        <view class="btn-text"  @click="routerPush('/pages/zombieCar/zombieCar')">僵尸车线索提供</view>
        <view class="btn-sub">点击上传照片></view>
      </view>
    </view>
  </view>
</template>


<script>
	var vk = uni.vk;
	export default {
		data() {
			// 页面数据变量
			return {
				// init请求返回的数据
				data:{
					
				},
				// 表单请求数据
				form1:{
					
				},
				scrollTop:0,
			}
		},
		onPageScroll(e) {
			this.scrollTop = e.scrollTop;
		},
		// 监听 - 页面每次【加载时】执行(如：前进)
		onLoad(options = {}) {
			vk = uni.vk;
			this.options = options;
			this.init(options);
		},
		// 监听 - 页面【首次渲染完成时】执行。注意如果渲染速度快，会在页面进入动画完成前触发
		onReady(){
			
		},
		// 监听 - 页面每次【显示时】执行(如：前进和返回) (页面每次出现在屏幕上都触发，包括从下级页面点返回露出当前页面)
		onShow() {
			
		},
		// 监听 - 页面每次【隐藏时】执行(如：返回)
		onHide() {
			
		},
		// 监听 - 点击右上角转发时
		onShareAppMessage(options) {
			
		},
		// 函数
		methods: {
			// 页面数据初始化函数
			init(options){
				// vk.reLaunch("/pages_template/uni-id/index/index");
			},
			routerPush(path){
				vk.navigateTo(path);
			},
			
		},
		// 监听器
		watch:{
			
		},
		// 计算属性
		computed:{
			
		}
	}
</script>
<style lang="scss" scoped>
.container {
	.center {
  text-align: center;
}
.title {
  font-size: 50rpx;
}
.subtitle {
  font-size: 34rpx;
}
  display: flex;
  flex-direction: column;
  color: white;
  background-color: #10aeff;
  .top {
    height: 20vh;
    display: flex;
    flex-direction: column;
    justify-content: center;
  }
  .bottom {
    flex:1;
    background-color: white;
    border-radius: 50rpx 50rpx 0 0;
    display: flex;
    flex-direction: column;
    align-items: center;

    .item {
      width: 80vw;
      background: #10aeff;
      margin-top: 6vh;
      padding: 10rpx;
      text-align: center;
      border-radius: 15rpx 15rpx 15rpx 15rpx;
      .btn-text {
        font-size: 35rpx;
      }
      .btn-sub {
        font-size: 24rpx;
      }
    }
  }
}

</style>
