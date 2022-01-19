<template>
  <!-- <div class="sales-view"> -->
    <!-- 这是SalesView -->
    <!-- <v-chart :options="data" :style="{ width: '100%',height: '100%'}"/> -->
    <!-- 以上为教程代码，教程使用的是 vue-echarts V5 版本 但若不指定，现在安装的是 V6 版本，V5 -> V6 最大的区别就是 options -> option -->
    <v-chart :option="data" :style="{ width: '100%',height: '100%'}"/>
  <!-- <el-row :gutter="20">
    <el-col :span="6">
        <el-card shadow="hover">
          1
        </el-card>
      </el-col>
      <el-col :span="6">
        <el-card shadow="hover">
          2
        </el-card>
      </el-col>
      <el-col :span="6">
        <el-card shadow="hover">
          3
        </el-card>
      </el-col>
      <el-col :span="6">
        <el-card shadow="hover">
          4
        </el-card>
      </el-col>
    </el-row> -->
  <!-- </div> -->
</template>

<script>

export default {
  components: {
  },
  data() {
      return {
        data: {
          xAxis: {
            type: 'category'
          },
          yAxis: {},
          series: [{
            type: 'line',
            data: [100, 200, 300, 400]
          }]
        }
     }
  }
}
</script>

<style lang="scss" scoped>
</style>
