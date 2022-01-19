<template>
  <div class="sales-view">
    这是SalesView
    <v-chart :options="data" :style="{ width: '100%',height: '100%'}"/>
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
  </div>
</template>

<script>

export default {
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
