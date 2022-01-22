<template>
  <common-card title="今日交易用户" value="81,014">
    <template v-slot:wrapper>
      <!-- <div id="today-users-chart" :style="{ width: '100%',height: '100%'}"></div> -->
      <v-chart :option="getOptions()" />
    </template>
    <template v-slot:footer>
      <span>退货率</span>
      <span class="emphasis">5.14%</span>
    </template>
  </common-card>
</template>

<script>
import commonCardMixin from '../../mixins/commonCardMixin'
export default {
  mixins: [commonCardMixin],
  methods: {
    getOptions: function () {
      return {
        color: ['blue'],
        xAxis: {
          type: 'category',
          data: [
            '00:00',
            '01:00',
            '02:00',
            '03:00',
            '04:00',
            '05:00',
            '06:00',
            '07:00',
            '08:00',
            '09:00',
            '10:00',
            '11:00',
            '12:00',
            '13:00',
          ],
          show: false,
        },
        yAxis: {
          show: false,
        },
        series: [
          {
            type: 'bar',
            data: [
              410, 82, 200, 334, 390, 330, 220, 150, 82, 200, 290, 134, 290,
              330, 150,
            ],
            barWidth: '60%', // 设置为百分比后 100%无间距刚好展示完，100%以下有间距，100%以上会相互重叠，也可以设置为数字
          },
        ],
        grid: {
          top: 0,
          bottom: 0,
          left: 0,
          right: 0,
        },
      }
    },
  },
  // mounted() {
  //     const chartDom = document.getElementById('today-users-chart')
  //     const chart = this.$echarts.init(chartDom)
  //     chart.setOption({
  //         color: ['#3398DB'],
  //         xAxis: {
  //             type: 'category',
  //             data: ['00:00', '01:00', '02:00', '03:00', '04:00', '05:00', '06:00', '07:00', '08:00', '09:00', '10:00', '11:00', '12:00', '13:00'],
  //             show: false,
  //             barWidth: '60%'
  //         },
  //         yAxis: {
  //             show: false,
  //         },
  //         series: [{
  //             type: 'bar',
  //             data: [410, 82, 200, 334, 390, 330, 220, 150, 82, 200, 290, 134, 290, 330, 150],
  //         }],
  //         grid: {
  //             top: 0,
  //             bottom: 0,
  //             left: 0,
  //             right: 0,
  //         }
  //     })
  // },
}
</script>

<style lang=""></style>
