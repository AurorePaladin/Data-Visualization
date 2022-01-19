<template>
    <!-- <v-chart :options="data" :style="{ width: '100%',height: '100%'}"/> -->
    <!-- 以上为教程代码，教程使用的是 vue-echarts V5 版本 但若不指定，现在安装的是 V6 版本，V5 -> V6 最大的区别就是 options -> option -->
    <!-- V6 ()版本正确写法 -->
    <!-- <v-chart :option="data" /> -->
    <!-- v-charts示例 -->
    <ve-line :data="chartData" />
</template>

<script>
/* eslint-disable */
export default {
  components: {
  },
  // data() {
  //     return {
  //       data: {
  //         xAxis: {
  //           type: 'category'
  //         },
  //         yAxis: {},
  //         series: [{
  //           type: 'line',
  //           data: [100, 200, 300, 400]
  //         }]
  //       }
  //    }
  // }
  data: function () {
        return {
          chartData: {
            columns: ['日期', '销售额'],
            rows: [
              { '日期': '1月1日', '销售额': 123 },
              { '日期': '1月2日', '销售额': 1223 },
              { '日期': '1月3日', '销售额': 2123 },
              { '日期': '1月4日', '销售额': 4123 },
              { '日期': '1月5日', '销售额': 3123 },
              { '日期': '1月6日', '销售额': 7123 }
            ]
          }
        }
      }
}
</script>

<style lang="scss" scoped>
  .echarts {
    width: 100%;
    height: 100%;
  }
</style>
