<template>
  <view class="notice">
	<view class="title">申请告知</view>
    <view class="text">
1、《机动车登记规定》第四十二条规定提交的证明、凭证无效的，车辆被查封、扣押、抵押、质押和被盗抢的，车辆信息不符的等情形之一的，不予办理注销登记。
2、申请人对申请材料的真实有效性和申请行为负责，因信息虚假产生的一切责任由申请人承担。
3、审核不通过时，不予办理。 
4、申请使用原机动车号牌号码应当符合下列条件：
    （1）在办理机动车迁出、共同所有人变更、转让登记或者注销登记后两年内提出申请；
    （2）机动车所有人拥有原机动车且使用原号牌号码一年以上；
    （3）涉及原机动车的道路交通安全违法行为和交通事故处理完毕。
    </view>
    <button class="mt25" @click="routerPush">同意</button>
  </view>
</template>

<script>
var vk =uni.vk
export default {
  data() {
    return {};
  },
  methods:{
    routerPush(){
      vk.navigateTo('/pages/changeComp/changeComp');
    }
  }
};
</script>

<style lang="scss">
.notice {
  padding: 30rpx;
  .title{
	font-size: 38rpx;
	text-align: center;
	line-height: 60rpx;
	height: 60rpx;
	margin-bottom: 10rpx;
  }
  .text {
    line-height: 48rpx;
    font-size: 30rpx;
    white-space: pre-wrap;
  }
  .mt25 {
    margin-top: 25rpx;
    background: #4e6ef2;
    color: #fff;
    font-size: 28rpx;
  }
}
</style>
