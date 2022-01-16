<template>
  <div class="bottom-view">
    这是BottomView
     <el-row :gutter="20">
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
    </el-row>
  </div>
</template>

<script>

export default {
  components: {
  }
}
</script>

<style lang="scss" scoped>
</style>
