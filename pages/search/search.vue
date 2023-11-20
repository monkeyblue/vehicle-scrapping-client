<template>
  <view class="container">
    <view class="top">
      <u-sticky><u-search
        placeholder="输入车牌号/身份证/手机号均可查询"
        :show-action="false"
        v-model="keyword"
      ></u-search></u-sticky>
      
    </view>
    <u-list class="bottom">
    
      <u-list-item  v-for="(item, index) in setList(data,keyword)" :key="index">
        <u-cell @click="routerPush(item)" :title="item.ordername" value="2022-12-01"> </u-cell>
      </u-list-item>
    </u-list>
  </view>
</template>
  
  <script>
var vk = uni.vk;
export default {
  data() {
    return {
      keyword: "",
      scrollTop: 0,
      old: {
        scrollTop: 0,
      },
      data: [
        {
          url: "https://cdn.uviewui.com/uview/album/1.jpg",
          ordername: "订单1",
        },
        {
          url: "https://cdn.uviewui.com/uview/album/2.jpg",
          ordername: "订单2",
        },
        {
          url: "https://cdn.uviewui.com/uview/album/3.jpg",
          ordername: "订单3",
        },
        {
          url: "https://cdn.uviewui.com/uview/album/2.jpg",
          ordername: "订单4",
        },
        {
          url: "https://cdn.uviewui.com/uview/album/2.jpg",
          ordername: "订单5",
        },
        {
          url: "https://cdn.uviewui.com/uview/album/2.jpg",
          ordername: "订单6",
        },
        {
          url: "https://cdn.uviewui.com/uview/album/2.jpg",
          ordername: "订单7",
        },
      ],
    };
  },
  computed: {
    setList: () => {
      return (list, keyword) => {
        let data = list.filter((item) => {
          return item.ordername.includes(keyword);
        });
        return data;
      };
    },
  },
  methods: {
    routerPush(v) {
      console.log(v)
      vk.navigateTo("/pages/progress/progress");
    },
  },
};
</script>
  
  <style lang="scss" scoped>
.container {
  margin: 30rpx;
}
</style>
  