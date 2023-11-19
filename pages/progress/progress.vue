<template>
  <view class="container">
    
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
          <view
            v-for="(item, i) in data"
            :key="i"
            :class="item.status + ' item'"
            >步骤{{ i+1 }} {{ item.status }}</view
          >
        </scroll-view>
      </view>
    </view>
  </view>
</template>
	
	<script>
export default {
  data() {
    return {
      value: "",
      scrollTop: 0,
      old: {
        scrollTop: 0,
      },
      data: [
        { name: "asdasdasd", status: "success" },
        { name: "asdasdasd", status: "success" },
        { name: "asdasdasd", status: "success" },
        { name: "asdasdasd", status: "success" },
        { name: "asdasdasd", status: "success" },
        { name: "asdasdasd", status: "success" },
        { name: "asdasdasd", status: "success" },
        { name: "asdasdasd", status: "success" },
        { name: "asdasdasd", status: "success" },
        { name: "asdasdasd", status: "waiting" },
        { name: "asdasdasd", status: "success" },
        { name: "asdasdasd", status: "success" },
        { name: "asdasdasd", status: "success" },
        { name: "asdasdasd", status: "success" },
        { name: "asdasdasd", status: "success" },
        { name: "asdasdasd", status: "fail" },
      ],
    };
  },
  methods: {
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
  padding:0 15px;
  
  .bottom {
    .scroll-Y {
      height: calc(100vh - 69px);
    }
    .scroll-view_H {
      white-space: nowrap;
      width: 100%;
    }

    .item {
      
      border-radius: 10px;
      height: 60px;
      margin-top: 20px;
      text-align: center;
      line-height: 60px;
      background-color: #10aeff;
      color: #fff;
    }
	.success{
		background: #07c160;
	}
	.waiting{
		background: #ffc300;
	}
	.fail{
		background: #f76260;
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
	