<template>
  <view class="comp">
    <!-- <view class="title"> 选择回收公司 </view> -->
    <view class="list">
      <view class="item">
        <view class="top">
          <view class="com-name">{{ comp.name }}</view>
          <view class="com-sub">{{ comp.subtitle }}</view>
        </view>
        <view class="btm">
          <view>公司简介或报价 {{ comp.info }}</view>
          <view>地址{{ comp.adress }}</view>
          <view>联系方式{{ comp.tel }}</view>
        </view>
      </view>
    </view>
    <button class="mt25" @click="routerPush">下一步</button>
  </view>
</template>

<script>
var vk = uni.vk
export default {
  data() {
    return {
      comp: {
        name: "xxxx回收公司",
        subtitle: "sss",
        info: "xxxx回收公司xxxx回收公司xxxx回收公司xxxx回收公司xxxx回收公司xxxx回收公司xxxx回收公司xxxx回收公司",
        adress: "xxxxxxxxxxxxx",
        tel: "xxxxxxxx",
      },
    };
  },
  methods:{
    routerPush(){
      vk.navigateTo('/pages/applyForm/applyForm');
    }
  }
};
</script>

<style lang="scss" scoped>
.comp {
  padding: 30rpx;
  .title {
    font-size: 34rpx;
    text-align: center;
    line-height: 70rpx;
    height: 70rpx;
    margin-bottom: 30rpx;
  }
  .top {
    text-align: center;
    .com-name {
      line-height: 35rpx;
      height: 35rpx;
      font-size: 35rpx;
    }
    .com-sub {
      line-height: 40rpx;
      height: 40rpx;
      font-size: 30rpx;
    }
  }
  .btm {
    line-height: 48rpx;
    white-space: pre-wrap;
    font-size: 30rpx;
  }
  .item {
    border: 1rpx solid #ccc;
    border-radius: 15rpx;
    padding: 20rpx;
  }
  .mt25 {
    margin-top: 25rpx;
    background: #4e6ef2;
    color: #fff;
    font-size: 28rpx;
  }
}
</style>
