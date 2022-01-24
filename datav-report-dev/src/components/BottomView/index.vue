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
    }
  }
}
</script>

<style lang="scss" scoped>
</style>
