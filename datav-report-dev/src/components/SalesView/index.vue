<template>
    <!-- <v-chart :options="data" :style="{ width: '100%',height: '100%'}"/> -->
    <!-- 以上为教程代码，教程使用的是 vue-echarts V5 版本 但若不指定，现在安装的是 V6 版本，V5 -> V6 最大的区别就是 options -> option -->
    <!-- V6 ()版本正确写法 -->
    <!-- <v-chart :option="data" /> -->
    <!-- v-charts示例 -->
    <!-- <ve-line :data="chartData" /> -->
    <div class="sales-view">
      <el-card shadow="hover">
        <template v-slot:header>
          <div class="menu-wrapper">
            <el-menu :default-active="activeIndex" mode="horizontal" @select="onMenuSelect">
              <el-menu-item index="1">销售额</el-menu-item>
              <el-menu-item index="2">访问量</el-menu-item>
            </el-menu>
            <div class="menu-right">
              <el-radio-group v-model="radioSelect" size="small">
                <el-radio-button label="今日" />
                <el-radio-button label="本周" />
                <el-radio-button label="本月" />
                <el-radio-button label="今年" />
              </el-radio-group>
              <el-date-picker
                type="daterange"
                size="small"
                v-model="date"
                range-separator="至"
                start-placeholder="开始日期"
                end-placeholder="结束日期"
                :picker-options="pickerOptions"
              />
            </div>
          </div>
        </template>
        <template>
          <div>
            222
          </div>
        </template>
      </el-card>
    </div>
</template>

<script>
/* eslint-disable */
export default {
  data(){
    return {
      activeIndex: '1',
      radioSelect: "今日",
      date: null,
      pickerOptions: {
        shortcuts: [
          { text: '最近一周', onClick(picker){} },
          { text: '最近一个月', onClick(picker){}},
          { text: '最近三个月', onClick(picker){}}
        ]
      }
    }
  },
  methods: {
    onMenuSelect(index){
        this.activeIndex = index
        console.log(this.activeIndex);
    }
  },
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
  // },
  // data: function () {
  //       return {
  //         chartData: {
  //           columns: ['日期', '销售额'],
  //           rows: [
  //             { '日期': '1月1日', '销售额': 123 },
  //             { '日期': '1月2日', '销售额': 1223 },
  //             { '日期': '1月3日', '销售额': 2123 },
  //             { '日期': '1月4日', '销售额': 4123 },
  //             { '日期': '1月5日', '销售额': 3123 },
  //             { '日期': '1月6日', '销售额': 7123 }
  //           ]
  //         }
  //       }
  //     }
}
</script>

<style lang="scss" scoped>
.sales-view{
  margin-top: 20px;
  .menu-wrapper {
    display: flex;
  }
}
</style>
