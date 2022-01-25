<template>
  <div class="bottom-view">
    <div class="view">
      <el-card shadow="hover">
        <template v-slot:header>
          <div class="title-wrapper">关键词搜索</div>
        </template>
        <template>
          <div class="chart-wrapper">
            <div class="chart-inner">
              <div class="chart">
                <div class="chart-title">搜索用户数</div>
                <div class="chart-data">93634</div>
                <v-chart :option="searchUserOption" />
              </div>
              <div class="chart">
                <div class="chart-title">搜索量</div>
                <div class="chart-data">198782</div>
                <v-chart :option="searchUserOption" />
              </div>
            </div>
            <div class="table-wrapper">
              <el-table :data="tableData">
                <el-table-column prop="rank" label="排名" />
                <el-table-column prop="keyword" label="关键词" />
                <el-table-column prop="count" label="总搜索量" />
                <el-table-column prop="users" label="搜索用户数" />
                <el-table-column prop="range" label="搜索占比" />
              </el-table>
              <el-pagination
                layout="prev, pager, next"
                :total="100"
                :page-size="4"
                background
                @current-change="onPageChange"
              />
            </div>
          </div>
        </template>
      </el-card>
    </div>
    <div class="view">
      <el-card shadow="hover">
        <template v-slot:header>
          <div class="title-wrapper">
            <div class="title">分类销售排行</div>
            <div class="radio-wrapper">
              <el-radio-group v-model="radioSelect" size="small">
                <el-radio-button label="品类"></el-radio-button>
                <el-radio-button label="商品"></el-radio-button>
              </el-radio-group>
            </div>
          </div>
        </template>
        <template>
          <div class="chart-wrapper">
            <v-chart :option="categoryOption" />
          </div>
        </template>
      </el-card>
    </div>
  </div>
</template>

<script>

export default {
  data() {
    return {
      searchUserOption: {
        xAxis: {
          type: 'category',
          boundaryGap: false // 消除X轴两侧边距
        },
        yAxis: {
          show: false,
        },
        series: {
          type: 'line',
          data: [100, 150, 200, 250, 200, 150, 100, 50, 100, 150],
          areaStyle: {
            color: 'rgba(95,187,255,.5)' // 图表区域填充色
          },
          lineStyle: {
            color: 'skyblue'
          },
          itemStyle: {
            opacity: 0 // 点的透明度
          },
          smooth: true,
        },
        grid: {
            top: 10,
            right: 0,
            bottom: 0,
            left: 0,
        }
      },
      searchNumberOption: {},
      tableData: [
        { id: 1, rank: 1, keyWord: '北京', count: 100, users: 90, range: '90%' }, // range 表示点击率
        { id: 2, rank: 2, keyWord: '北京', count: 90, users: 80, range: '80%' },
        { id: 3, rank: 3, keyWord: '北京', count: 80, users: 70, range: '70%' },
        { id: 4, rank: 4, keyWord: '北京', count: 70, users: 60, range: '60%' }
      ],
      radioSelect: '品类',
      categoryOption: {}
    }
  },
  methods: {
    onPageChange(page) {
      console.log(page)
    },
    renderPieChart() {
      const mockData = [
        {
          legendname: '米粥',
          value: 67,
          percent: '15.48%',
          itemStyle: { // 饼图块的颜色
            color: 'pink'
          },
          name: '米粥 | 15.48',
        },
        {
          legendname: '蛋挞',
          value: 97,
          percent: '22.30',
          itemStyle: {
            color: 'purple'
          },
          name: '蛋挞 | 22.30%',
        },
        {
          legendname: '饼干',
          value: 92,
          percent: '21.15',
          itemStyle: {
            color: 'blue'
          },
          name: '饼干 | 21.15%',
        },
      ]
      this.categoryOption = {
        title: [{
          text: '品类分布',
          textStyle: {
            fontSize: 14,
            color: 'gray',
          },
          left: 20,
          top: 20,
        },
        {
          text: '累计订单量',
          subtext: '320', // 当加上 subtext 属性后会变成 副标题
          x: '34.5%',
          y: '42.5%',
           textStyle: {
            fontSize: 14,
            color: 'gold',
          },
          textAlign: 'center',
        }],
        series: [{
          name: '品类分布',
          type: 'pie',
          data: mockData,
          label: {
            directly: {
              show: true,
              position: 'outter', // legendname 在饼图里的显示位置
              formatter: function(params) { // params 指代 mockData
                return params.data.legendname
              }
            }
          },
          center: ['35%', '55%'], // 饼图圆心的 X Y坐标; % 是【画布的长、宽中 最小 的值，比如画布是 400*300 就以 300 为基准】，以下相同
          radius: ['45%', '60%'], // 45%是内半径，60%是外半径，所以图表为 （外半径60% - 内半径45%） 的环状空心饼图
          labelLine: { // 饼图标签旁边的线条
            directly: {
              length: 5, // 斜线
              length2: 3, // 横线
              smooth: true
            },
            clockwise: true, // 以12点钟方向为基准， true 为顺时针, false 为逆时针
            itemStyle: { // 饼状块加边距，在浏览器里就会显示为白色间隔
              borderWidth: 4,
              borderColor: '#fff'
            }
          },
        }],
        lengend: {
          type: 'scroll', // 滑动
          orient: 'vertical', // 垂直排列
          height: 250,
          left: '70%',
          top: 'middle',
          textStyle: {
            color: '#8c8c8c'
          },
          tooltip: { // 鼠标移上去显示的信息
            trigger: 'item', // 默认属性，鼠标移上去就触发下面的 formatter()
            formatter: function(params) {
              const str = params.seriesName + '<br />' + params.marker + params.data.legendname + '<br />' + '数量：' + params.data.value + '<br />' + '占比：' + params.data.percent + '%' // marker 是自有的小圆点 颜色跟饼状块的color一致
              return str
            }
          }
        },
      }
    }
  },
  mounted() {
    this.renderPieChart()
  }
}
</script>

<style lang="scss" scoped>
  .bottom-view {
    display: flex;
    margin-top: 20px;

    .view {
      flex: 1;
      width: 50%;
      box-sizing: border-box;

      &:first-child {
        padding: 0 10px 0 0;
      }

      &:last-child {
        padding: 0 0 0 10px;
      }

      .title-wrapper {
        display: flex;
        align-items: center;
        height: 60px;
        box-sizing: border-box;
        border-bottom: 1px solid #eee;
        font-size: 14px;
        font-weight: 500;
        padding: 0 0 0 20px;

        .radio-wrapper {
          flex: 1;
          display: flex;
          justify-content: flex-end;
          padding-right: 20px;
        }
      }

      .chart-wrapper {
        display: flex;
        flex-direction: column;
        height: 452px;

        .chart-inner {
          display: flex;
          padding: 0 10px;
          margin-top: 20px;

          .chart {
            flex: 1;
            padding: 0 10px;

            .chart-title {
              color: #999;
              font-size: 14px;
            }

            .chart-data {
              font-size: 22px;
              color: #333;
              font-weight: 500;
              letter-spacing: 2px;
            }

            .echarts {
              height: 50px;
            }
          }
        }

        .table-wrapper {
          flex: 1;
          margin-top: 20px;
          padding: 0 20px 20px;

          .el-pagination {
            display: flex;
            justify-content: flex-end;
            margin-top: 15px;
          }
        }
      }
    }
  }
</style>
