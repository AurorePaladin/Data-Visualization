<template>
  <div class="sales-radar">
    <div class="sales-radar-inner">
      <vue-echarts :options="options" />
    </div>
  </div>
</template>

<script>
  export default {
    name: 'SalesRadar',
    data () {
      return {
        options: {}
      }
    },
    mounted () {
      // 渲染echarts雷达图
      this.options = {}
    }
  }
</script>

<style lang="scss" scoped>
  .sales-radar {
    position: absolute;
    top: 3250px;
    left: 0;
    z-index: 10;
    width: 100%;
    height: 800px;
    padding: 25px 25px 0;
    box-sizing: border-box;

    .sales-radar-inner {
      width: 100%;
      height: 100%;
      background: rgba(255, 255, 255, .05);
    }
  }
</style>