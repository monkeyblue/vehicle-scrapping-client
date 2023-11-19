<template>
  <view class="container">
    <view class="top">
      <view class="uni-input-wrapper">
        <input
          class="uni-input"
          placeholder="输入车牌号/身份证/手机号均可查询"
          :value="value"
        />
      </view>
    </view>
    <view class="bottom">
      <view>
        <scroll-view
          :scroll-top="scrollTop"
          scroll-y="true"
          class="scroll-Y"
          @scrolltoupper="upper"
          @scrolltolower="lower"
          @scroll="scroll"
        >
          <view @click="routerPush" v-for="(item,i) in data" :key="i" class="item">{{item.name}}</view>
        </scroll-view>
      </view>
    </view>
  </view>
</template>
  
  <script>
  var vk = uni.vk;
export default {
  
  data() {
    return {
      value: "",
      scrollTop: 0,
      old: {
        scrollTop: 0,
      },
	  data:[
	  {name:'asdasdasd'},
		{name:'asdasdasd'},
		{name:'asdasdasd'},
		{name:'asdasdasd'},
		{name:'asdasdasd'},
		{name:'asdasdasd'},
		{name:'asdasdasd'},
		{name:'asdasdasd'},
		{name:'asdasdasd'},
		{name:'asdasdasd'},
		{name:'asdasdasd'},
		{name:'asdasdasd'},
		{name:'asdasdasd'},
		{name:'asdasdasd'},
		{name:'asdasdasd'},
		{name:'asdasdasd'}
	  ]
    };
  },
  methods: {
	routerPush(){
		vk.navigateTo('/pages/progress/progress')
	},
    upper: function (e) {
      console.log(e);
    },
    lower: function (e) {
      console.log(e);
    },
    scroll: function (e) {
      console.log(e);
      this.old.scrollTop = e.detail.scrollTop;
    },
    goTop: function (e) {
      // 解决view层不同步的问题
      this.scrollTop = this.old.scrollTop;
      this.$nextTick(function () {
        this.scrollTop = 0;
      });
      uni.showToast({
        icon: "none",
        title: "纵向滚动 scrollTop 值已被修改为 0",
      });
    },
  },
};
</script>
  
  <style lang="scss" scoped>
.container {
  padding: 15px;
  height: 100vh;
  .top {
    .uni-input-wrapper {
      border-radius: 9px;
      border: 1px solid #ccc;
      padding: 10px 8px;
      width: 100%;
      box-sizing: border-box;
    }
  }
  .bottom {
	margin-top: 25px;
    .scroll-Y {
      height: calc(80vh - 25px);
    }
    .scroll-view_H {
      white-space: nowrap;
      width: 100%;
    }
    
	.item{
		border: 1px solid  #ccc;
		border-radius: 10px;
		height: 60px;
		margin-bottom: 20px;
		text-align: center;
		line-height: 60px;
  background-color: #10aeff;
  color: #fff;
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
  