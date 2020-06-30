<template>
  <div style="display: inline-block">
    <el-date-picker
      :style="{width: inputWidth + 'px'}"
      v-model="values[0]"
      align="right"
      type="date"
      placeholder="选择日期1"
      value-format="yyyy-MM-dd"
      :picker-options="pickerOptions1"
    ></el-date-picker>
    <span style="padding: 0 3px; color: #999999">-</span>
    <el-date-picker
      :style="{width: inputWidth + 'px'}"
      v-model="values[1]"
      align="right"
      type="date"
      placeholder="选择日期2"
      value-format="yyyy-MM-dd"
      :picker-options="pickerOptions2"
    ></el-date-picker>
  </div>
</template>

<script>
export default {
  props: {
    values: {
      type: Array,
      default: []
    },
    inputWidth: {
      type: Number,
      default: 200
    }
  },
  data() {
    return {
      gmtString: " GMT+0800",
      pickerOptions1: {
        disabledDate: date => {
          // 因为value-format= "yyyy-MM-dd"，要和date比较就要转换，转换之后是UTC时间，而date是本地时区的时间
          // 如果没有设置alue-format= "yyyy-MM-dd"，则可以直接比较：return this.values[1] ? date > this.values[1]: false;
          return this.values[1]
            ? date > new Date(this.values[1] + this.gmtString)
            : false;
        }
      },
      pickerOptions2: {
        disabledDate: date => {
          return this.values[0]
            ? date < new Date(this.values[0] + this.gmtString)
            : false;
        }
      }
    };
  },
  created() {
    let gmt = new Date().getTimezoneOffset() / 60;
    this.gmtString = gmt <= 0 ? " GMT+" + -gmt : " GMT-" + gmt;
  },
};
</script>