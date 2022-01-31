<template>
  <v-chart :option="options" />
</template>

<script>
import 'echarts/extension/bmap/bmap'
  export default {
    data() {
      return {
        options: {}
      }
    },
    mounted() {
      this.options = {
        bmap: {
          key: 'G1LFyjrNGIkns5OfpZnrCGAKxpycPLwb',
          center: [104.114129, 37.550339],
          zoom: 5, // 缩放比例
          roam: false, // 是否允许缩放
          // mapStyle: {}
        }
      }
    }
  }
</script>

<style lang="scss" scoped>
</style>
