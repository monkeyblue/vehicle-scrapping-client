<template>
  <view class="container">
    <view class="top">
      <view class="title center">车辆注销一件事</view>
      <view class="subtitle center">安全出行 文明交通</view>
    </view>
    <view class="bottom">
      <view class="item">
        <view class="btn-text">车辆注销申请</view>
        <view class="btn-sub">前往注销></view>
      </view>
      <view class="item" @click="routerPush">
        <view class="btn-text">我的业务</view>
        <view class="btn-sub">点击查看></view>
      </view>
      <view class="item">
        <view class="btn-text">僵尸车线索提供</view>
        <view class="btn-sub">点击上传照片></view>
      </view>
    </view>
  </view>
</template>

<script>
export default {
  data() {
    return {};
  },
  methods:{
	routerPush(){
		this.$router.push('/pages_template/search/search')
	}

  }
};
</script>

<style lang="scss" scoped>
.container {
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
    border-radius: 50px 50px 0 0;
    display: flex;
    flex-direction: column;
    align-items: center;

    .item {
      width: 80vw;
      background: #10aeff;
      margin-top: 6vh;
      padding: 10px;
      text-align: center;
      border-radius: 15px 15px 15px 15px;
      .btn-text {
        font-size: 22px;
      }
      .btn-sub {
        font-size: 14px;
      }
    }
  }
}
.center {
  text-align: center;
}
.title {
  font-size: 30px;
}
.subtitle {
  font-size: 20px;
}
</style>
