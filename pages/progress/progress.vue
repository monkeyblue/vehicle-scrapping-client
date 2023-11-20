<template>
  <view class="container-progress">
    <u-steps :list="numList" direction="column" mode="dot">
      <u-steps-item
       
        :title="item.name"
        v-for="item in numList"
        :key="item.name"
      ></u-steps-item>
    </u-steps>
  </view>
</template>

<script>
import uStepsItem from "../../uni_modules/uview-ui/components/u-steps-item/u-steps-item.vue";
export default {
  components: { uStepsItem },
  data() {
    return {
      numList: [
        {
          name: "步骤---1",
        },
        {
          name: "步骤---2",
        },
        {
          name: "步骤---3",
        },
        {
          name: "步骤---4",
        },
        {
          name: "步骤---5",
        },
        {
          name: "步骤---6",
        },
        {
          name: "步骤---7",
        },
      ],
    };
  },
};
</script>

	
<style lang="scss" >
.container-progress {
  font-size: 30rpx;
  padding: 30rpx;
  // display: flex;
  // flex-direction: column;
  // align-items: center;
  // justify-content:flex-start;
}
</style> 
	