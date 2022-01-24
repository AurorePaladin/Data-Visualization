<template>
  <div class="bottom-view">
    这是BottomView
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
          <div class="view">
      <el-card shadow="hover">
        <template v-slot:header>
          <div class="title-wrapper">
            <div class="title">分类销售排行</div>
            <div class="radio-wrapper">
              <el-radio-group v-model="radioSelect" size="small" @change="onCategoryChange">
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
          smooth: true
        }
      },
      searchNumberOption: {},
      tableData: [
        { id: 1, rank: 1, keyWord: '北京', count: 100, users: 90, range: '90%'}, // range 表示点击率
        { id: 2, rank: 2, keyWord: '北京', count: 90, users: 80, range: '80%'},
        { id: 3, rank: 3, keyWord: '北京', count: 80, users: 70, range: '70%'},
        { id: 4, rank: 4, keyWord: '北京', count: 70, users: 60, range: '60%'}
      ],
      radioSelect: '品类',
      categoryOption: {}
    }
  },
  methods: {
    onPageChange(page) {
      console.log(page)
    }
  }
}
</script>

<style lang="scss" scoped>
.bottom-view {
    display: flex;
    margin-top: 20px;

    .view {
      flex: 1;

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
      }

      .radio-wrapper {
          flex: 1;
          display: flex;
          justify-content: flex-end;
          padding-right: 20px;
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
