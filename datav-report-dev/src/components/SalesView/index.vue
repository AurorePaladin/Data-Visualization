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
            <el-menu :default-active="activeIndex" mode="horizontal" @select="onMenuSelect" class="sales-view-menu">
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
                class="sales-view-date-picker"
                unlink-panels
              />
            </div>
          </div>
        </template>
        <template>
          <div class="sales-view-chart-wrapper">
          <v-chart :options="chartOption" />
          <div class="sales-view-list">
            <div class="sales-view-title">排行榜</div>
            <div class="list-item-wrapper">
              <div class="list-item" v-for="item in rankData" :key="item.no">
                <div :class="['list-item-no', +item.no <= 3 ? 'top-no' : '']">{{item.no}}</div>
                <div class="list-item-name">{{item.name}}</div>
                <div class="list-item-money">{{item.money}}</div>
              </div>
            </div>
          </div>
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
          { text: '最近一周', onClick(picker) {
              const start = new Date()
              const end = new Date()
              start.setTime(start.getTime() - 3600 * 24 * 1000 * 7)
              picker.$emit('pick', [start, end])
            } },
          { text: '最近一个月', onClick(picker) {
              const start = new Date()
              const end = new Date()
              start.setTime(start.getTime() - 3600 * 24 * 1000 * 30)
              picker.$emit('pick', [start, end])
            }},
          { text: '最近三个月', onClick(picker) {
              const start = new Date()
              const end = new Date()
              start.setTime(start.getTime() - 3600 * 24 * 1000 * 90)
              picker.$emit('pick', [start, end])
            }}
        ]
      },
      chartOption: {
        title:{
          text: '年度销售额',
          textStyle: {
            fontSize: 12,
            color: '#666'
          }
        },
        xAxis: {
          type: 'category',
          data:['1月', '2月', '3月','4月', '5月', '6月', '7月', '8月', '9月','10月', '11月', '12月']
        },
        yAxis: {
          axisLine: {
              show: false
            },
            axisTick: {
              show: false // 辅助线【刻度】关闭
            },
            splitLine: {
              lineStyle: {
                type: 'dotted',
                color: '#eee'
              }
            }
        },
        series: [{
          type: 'bar',
          barWidth: '35%',
          data: [
              200, 250, 300, 350, 300, 250, 200, 250, 300, 350, 300, 250
            ],
          color: ['blue']
        }],
        grid:{
          top: 70,
          right: 60,
          bottom: 50,
          left: 60,
        }
      },
      rankData: [
        {
          no: 1,
          name: '麦当劳',
          money: '323.234',
        },
        {
          no: 2,
          name: '麦当劳',
          money: '323.234',
        },
        {
          no: 3,
          name: '麦当劳',
          money: '323.234',
        },{
          no: 4,
          name: '麦当劳',
          money: '323.234',
        },{
          no: 5,
          name: '麦当劳',
          money: '323.234',
        },{
          no: 6,
          name: '麦当劳',
          money: '323.234',
        },
        {
          no: 7,
          name: '麦当劳',
          money: '323.234',
        }
      ],
    }
  },
  methods: {
    onMenuSelect(index){
        this.activeIndex = index
        if (index === '1') {
          // this.render(this.orderFullYear, this.orderFullYearAxis, '年度销售额')
        } else {
          // this.render(this.userFullYear, this.userFullYearAxis, '年度用户访问量')
        }
    },
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
    .sales-view-menu {
        width: 100%;
        padding-left: 20px;

        .el-menu-item {
          height: 50px;
          line-height: 50px;
          margin: 0 20px;
        }
    }
  }
   .menu-right {
        position: absolute;
        top: 0;
        right: 20px;
        height: 50px;
        display: flex;
        align-items: center;
        justify-content: flex-end;

        .sales-view-date-picker {
          margin-left: 20px;
        }
    }
  .sales-view-chart-wrapper {
      display: flex;
      height: 270px;

      .echarts {
        flex: 0 0 70%;
        width: 70%;
        height: 100%;
      }

      .sales-view-list {
        flex: 1;
        width: 100%;
        height: 100%;
        overflow: hidden;

        .sales-view-title {
          margin-top: 20px;
          font-size: 12px;
          color: #666;
          font-weight: 500;
        }

        .list-item-wrapper {
          margin-top: 15px;

          .list-item {
            display: flex;
            align-items: center;
            font-size: 12px;
            height: 20px;
            padding: 6px 20px 6px 0;

            .list-item-no {
              display: flex;
              align-items: center;
              justify-content: center;
              width: 20px;
              height: 20px;
              color: #333;

              &.top-no {
                background: #000;
                border-radius: 50%;
                color: #fff;
                font-weight: 500;
              }
            }

            .list-item-name {
              margin-left: 10px;
              color: #333;
            }

            .list-item-money {
              flex: 1;
              text-align: right;
            }
          }
        }
      }
    }
}
</style>
