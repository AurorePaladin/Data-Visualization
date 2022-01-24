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
                <v-chart :options="searchUserOption" />
              </div>
              <div class="chart">
                <div class="chart-title">搜索量</div>
                <div class="chart-data">198782</div>
                <v-chart :options="searchNumberOption" />
              </div>
            </div>
          </div>
          <div class="table-wrapper">
             <el-table :data="tableData">
                <el-table-column />
              </el-table>
              <el-pagination />
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
            <v-chart :options="categoryOption" />
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
      searchUserOption: {},
      searchNumberOption: {},
      tableData: {},
      radioSelect: '品类',
      categoryOption: {}
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
    }
}
</style>
