<template>
  <view class="applyform">
    <u-tabs :list="tabs" @click="checkTab"></u-tabs>
    <view class="notice"
      >公告栏：机动车所有人及代理人对申请材料的真实有效性负责</view
    >
    <u-form :model="form" ref="form1" label-width="100">
      <view v-if="isPersonOrder">
      <view class="gap">机动车所有人</view>
      <u-form-item label="姓名" prop="name" :border-bottom="true"
        ><u-input v-model="form.name"
      /></u-form-item>
      <u-form-item label="联系方式" prop="tel" :border-bottom="true">
        <u-input v-model="form.tel" />
      </u-form-item>
      <u-form-item label="收款方式" prop="capType" :border-bottom="true">
        <u-radio-group v-model="form.capType">
          <u-radio
            v-model="item.checked"
            v-for="(item, index) in capTypeList"
            :key="index"
            :name="item.type"
          >
            {{ item.label }}
          </u-radio>
        </u-radio-group>
      </u-form-item>
      <u-form-item
        v-if="form.capType == '1'"
        label="支付宝账号"
        prop="aliNo"
        :border-bottom="true"
      >
        <u-input v-model="form.aliNo" />
      </u-form-item>
      <u-form-item
        label="开户名"
        v-if="form.capType == '2'"
        prop="accountName"
        :border-bottom="true"
      >
        <u-input v-model="form.accountName" />
      </u-form-item>
      <u-form-item
        label="银行卡信息"
        prop="cardInfo"
        :border-bottom="true"
        v-if="form.capType == '2'"
      >
        <u-input v-model="form.cardInfo" />
      </u-form-item>
      <u-form-item label="车主身份证号" prop="idNo" :border-bottom="true">
        <u-input v-model="form.idNo" />
      </u-form-item>
      <u-form-item
        label="上传身份证正面"
        label-width="100%"
        labelPosition="top"
      >
        <u-upload
          style="margin-top: 10px"
          :fileList="fileList"
          @afterRead="afterRead"
          @delete="deletePic"
          name="6"
          multiple
          :maxCount="1"
          width="250"
          height="150"
        >
          <image
            src="https://cdn.uviewui.com/uview/demo/upload/positive.png"
            mode="widthFix"
            style="width: 250px; height: 150px; margin-top: 15px"
          ></image>
        </u-upload>
      </u-form-item>
      <u-form-item
        label="上传身份证反面"
        label-width="100%"
        labelPosition="top"
      >
        <u-upload
          style="margin-top: 10px"
          :fileList="fileList"
          @afterRead="afterRead"
          @delete="deletePic"
          name="6"
          multiple
          :maxCount="1"
          width="250"
          height="150"
        >
          <image
            src="https://cdn.uviewui.com/uview/demo/upload/positive.png"
            mode="widthFix"
            style="width: 250px; height: 150px; margin-top: 15px"
          ></image>
        </u-upload>
      </u-form-item>
    </view>
    <view v-else>
      <view class="gap">机动车联系人</view>
     
      <u-form-item label="公司名称" prop="compname" :border-bottom="true"
        ><u-input v-model="form.compname"
      /></u-form-item>
      <u-form-item label="公司地址" prop="compadress" :border-bottom="true"
        ><u-input v-model="form.compadress"
      /></u-form-item>
      <u-form-item label="代理人姓名" prop="proxyName" :border-bottom="true"
        ><u-input v-model="form.proxyName"
      /></u-form-item>
      <u-form-item label="代理人手机号" prop="proxyTel" :border-bottom="true"
        ><u-input v-model="form.proxyTel"
      /></u-form-item>
      <u-form-item label="公司对公账号" prop="compAccount" :border-bottom="true"
        ><u-input v-model="form.compAccount"
      /></u-form-item>
      <u-form-item
        label="公司授权证明书"
        label-width="100%"
        labelPosition="top"
      >
        <u-upload
          style="margin-top: 10px"
          :fileList="fileList"
          @afterRead="afterRead"
          @delete="deletePic"
          name="6"
          multiple
          :maxCount="1"
          width="200"
          height="100"
        >
        </u-upload>
      </u-form-item>
      <u-form-item
        label="营业执照复印件（副本）需要盖章"
        label-width="100%"
        labelPosition="top"
      >
        <u-upload
          style="margin-top: 10px"
          :fileList="fileList"
          @afterRead="afterRead"
          @delete="deletePic"
          name="6"
          multiple
          :maxCount="1"
          width="200"
          height="100"
        >
        </u-upload>
      </u-form-item>
      <u-form-item
        label="代办人身份证正面"
        label-width="100%"
        labelPosition="top"
      >
        <u-upload
          style="margin-top: 10px"
          :fileList="fileList"
          @afterRead="afterRead"
          @delete="deletePic"
          name="6"
          multiple
          :maxCount="1"
          width="250"
          height="150"
        >
          <image
            src="https://cdn.uviewui.com/uview/demo/upload/positive.png"
            mode="widthFix"
            style="width: 250px; height: 150px; margin-top: 15px"
          ></image>
        </u-upload>
      </u-form-item>
      <u-form-item
        label="代办人身份证反面"
        label-width="100%"
        labelPosition="top"
      >
        <u-upload
          style="margin-top: 10px"
          :fileList="fileList"
          @afterRead="afterRead"
          @delete="deletePic"
          name="6"
          multiple
          :maxCount="1"
          width="250"
          height="150"
        >
          <image
            src="https://cdn.uviewui.com/uview/demo/upload/positive.png"
            mode="widthFix"
            style="width: 250px; height: 150px; margin-top: 15px"
          ></image>
        </u-upload>
      </u-form-item>
    </view>
      <view class="gap">机动车</view>
      <u-form-item label="车牌号" prop="carNo" :border-bottom="true"
        ><u-input v-model="form.carNo"
      /></u-form-item>
      <u-form-item
        label="车辆类型"
        prop="form.carType"
        borderBottom
        @click="showCarType = true"
        ref="item1"
      >
        <u-input
          v-model="form.carType"
          disabled
          disabledColor="#ffffff"
          placeholder="车辆类型"
          border="none"
        ></u-input>
        <u-icon slot="right" name="arrow-right"></u-icon>
      </u-form-item>
      <u-form-item
        label="车辆照片左前45度"
        label-width="100%"
        labelPosition="top"
      >
        <u-upload
          style="margin-top: 10px"
          :fileList="fileList"
          @afterRead="afterRead"
          @delete="deletePic"
          name="6"
          multiple
          :maxCount="1"
          width="200"
          height="100"
        >
        </u-upload>
      </u-form-item>
      <u-form-item label="车辆照片右后" label-width="100%" labelPosition="top">
        <u-upload
          :fileList="fileList"
          style="margin-top: 10px"
          @afterRead="afterRead"
          @delete="deletePic"
          name="6"
          multiple
          :maxCount="1"
          width="200"
          height="100"
        >
        </u-upload>
      </u-form-item>
      <u-form-item
        label="机动车所在地址"
        label-width="130"
        prop="adress"
        :border-bottom="true"
        ><u-input v-model="form.adress"
      /></u-form-item>
      <u-form-item label="配件是否遗失" prop="isNotFound" :border-bottom="true">
        <u-radio-group v-model="form.isNotFound">
          <u-radio
            v-model="item.checked"
            v-for="(item, index) in isNotFoundList"
            :key="index"
            :name="item.type"
          >
            {{ item.label }}
          </u-radio>
        </u-radio-group>
      </u-form-item>
      <view v-if="form.isNotFound">
        <u-form-item label="遗失原因" prop="reason" :border-bottom="true"
          ><u-input v-model="form.reason"
        /></u-form-item>
        <u-form-item label="遗失日期" @click="show=true" prop="date" :border-bottom="true"
          ><u-calendar :show="show" @confirm="hideKeyboard" v-model="form.date"></u-calendar></u-form-item>
        <u-form-item label="遗失信息" prop="info" :border-bottom="true"
          ><u-input v-model="form.info"
        /></u-form-item>
      </view>
      <u-form-item
        label="号牌是否遗失"
        prop="isNotFoundCard"
        :border-bottom="true"
      >
        <u-radio-group v-model="form.isNotFoundCard">
          <u-radio
            v-model="item.checked"
            v-for="(item, index) in isNotFoundList"
            :key="index"
            :name="item.type"
          >
            {{ item.label }}
          </u-radio>
        </u-radio-group>
      </u-form-item>
      <view v-if="form.isNotFoundCard">
        <u-form-item label="遗失日期" prop="carddate" :border-bottom="true"
          ><u-input v-model="form.carddate"
        /></u-form-item>
        <u-form-item label="遗失声明" prop="cardnotice" :border-bottom="true"
          ><u-input v-model="form.cardnotice"
        /></u-form-item>
      </view>

      <u-form-item
        v-else
        label="号牌信息"
        label-width="100%"
        labelPosition="top"
      >
        <u-upload
          style="margin-top: 10px"
          :fileList="fileList"
          @afterRead="afterRead"
          @delete="deletePic"
          name="6"
          multiple
          :maxCount="1"
          width="200"
          height="100"
        >
        </u-upload>
      </u-form-item>
      <u-form-item
        label="行驶证是否遗失"
        label-width="130"
        prop="isNotFoundDriver"
        :border-bottom="true"
      >
        <u-radio-group v-model="form.isNotFoundDriver">
          <u-radio
            v-model="item.checked"
            v-for="(item, index) in isNotFoundList"
            :key="index"
            :name="item.type"
          >
            {{ item.label }}
          </u-radio>
        </u-radio-group>
      </u-form-item>
      <view v-if="form.isNotFoundDriver">
        <u-form-item label="遗失日期" prop="dirverdate" :border-bottom="true"
          ><u-input v-model="form.dirverdate"
        /></u-form-item>
        <u-form-item label="遗失声明" prop="dirvernotice" :border-bottom="true"
          ><u-input v-model="form.dirvernotice"
        /></u-form-item>
      </view>

      <u-form-item
        v-else
        label="行驶证信息"
        label-width="100%"
        labelPosition="top"
      >
        <u-upload
          style="margin-top: 10px"
          :fileList="fileList"
          @afterRead="afterRead"
          @delete="deletePic"
          name="6"
          multiple
          :maxCount="1"
          width="200"
          height="100"
        >
        </u-upload>
      </u-form-item>
      <u-form-item
        label-width="180"
        label="机动车登记证书是否遗失"
        prop="isNotFoundcheckIn"
        :border-bottom="true"
      >
        <u-radio-group v-model="form.isNotFoundcheckIn">
          <u-radio
            v-model="item.checked"
            v-for="(item, index) in isNotFoundList"
            :key="index"
            :name="item.type"
          >
            {{ item.label }}
          </u-radio>
        </u-radio-group>
      </u-form-item>
      <view v-if="form.isNotFoundcheckIn">
        <u-form-item label="遗失日期" prop="checkIndate" :border-bottom="true"
          ><u-input v-model="form.checkIndate"
        /></u-form-item>
        <u-form-item label="遗失声明" prop="checkInnotice" :border-bottom="true"
          ><u-input v-model="form.checkInnotice"
        /></u-form-item>
      </view>
      <u-form-item
        v-else
        label="行驶证信息"
        label-width="100%"
        labelPosition="top"
      >
        <u-upload
          style="margin-top: 10px"
          :fileList="fileList"
          @afterRead="afterRead"
          @delete="deletePic"
          name="6"
          multiple
          :maxCount="1"
          width="200"
          height="100"
        >
        </u-upload>
      </u-form-item>
      <u-form-item label="备注" prop="tips" :border-bottom="true"
        ><u-input v-model="form.tips"
      /></u-form-item>
    </u-form>
    <u-action-sheet
      :show="showCarType"
      :actions="carTypeList"
      title="请选择车辆类型"
      @close="showCarType = false"
      @select="carTypeSelect"
    >
    </u-action-sheet>

    <u-button type="primary" style="margin: 25rpx 0" @click="submit"
      >提交</u-button
    >
  </view>
</template>

<script>
export default {
  data() {
    return {
      show:false,
      tabs:[{name:'个人订单',isPersonOrder:true},{name:'企业订单',isPersonOrder:false} ],
      showCarType: false,
      fileList: [],
      isPersonOrder:true,
      form: {
        compname:'',
      compadress:'',
      proxyName:'',
      proxyTel:'',
      compAccount:'',
        tips:'',
        name: "",
        tel: "",
        capType: "",
        carType: "",
        aliNo: "",
        accountName: "",
        cardInfo: "",
        sex: "",
        radio: "",
        idNo: "",
        carNo: "",
        adress: "",
        reason: "",
        date: "",
        info: "",
        isNotFoundCard: "",
        carddate: "",
        cardnotice: "",
        checkIndate: "",
        checkInnotice: "",
        isNotFoundCheckin: "",
        isNotFoundDriver: "",
        driverdate: "",
        drivernotice: "",
      },
      carTypeList: [
        { name: "小型汽车", type: "1" },
        { name: "大型汽车", type: "2" },
        { name: "挂车", type: "3" },
        { name: "摩托车", type: "4" },
      ],
      isNotFoundList: [
        { label: "是", type: 1 },
        { label: "否", type: 0 },
      ],

      capTypeList: [
        { label: "支付宝", type: "1" },
        { label: "银行转账", type: "2" },
        { label: "现金", type: "3" },
      ],

      rules: {
        name: [
          {
            required: true,
            message: "请输入姓名",
            trigger: ["change", "blur"],
          },
        ],
        radio: [
          {
            type: "array",
            required: true,
            message: "请选择收款方式",
            trigger: ["blur"],
          },
        ],
      },
    };
  },
  onReady() {
    this.$refs.form1.setRules(this.rules);
  },
  methods: {
    hideKeyboard(){
      this.show = false
    },
    checkTab(v){
      console.log(v)
      this.isPersonOrder = v.isPersonOrder
    },
    carTypeSelect(v) {
      this.form.carType = v.name;
    },
    submit() {
      this.$refs.form1.validate((valid) => {
        console.log(valid);
        if (valid) {
          uni.showToast({
            icon: "none",
            title: "表单验证通过",
          });
        }
      });
    },
  },
};
</script>
<style lang="scss">
.applyform {
  padding: 0 20px 20px;
  .gap {
    height: 30px;
    background: #53c2ff;
    line-height: 30px;
    color: #fff;
    padding: 0 5px;
    display: inline-block;
  }
  .notice {
    position: relative;
    left: 0;
    top: 0;
    background: #e9c9b3ba;
    margin-bottom: 20px;
    padding: 5px;
  }
}
</style>