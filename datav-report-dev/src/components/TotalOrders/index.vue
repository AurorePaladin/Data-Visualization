<template>
    <common-card title="累积订单量" value="2,157,420">
    <template v-slot:wrapper>
        <!-- <div id="total-orders-chart" :style="{ width: '100%',height: '100%'}"></div> -->
        <v-chart :option="getOptions()" />
    </template>
    <template v-slot:footer>
        <span>昨日订单量</span>
        <span class="emphasis">￥ 200,000,000</span>
    </template>
    </common-card>
</template>

<script>
import commonCardMixin from '../../mixins/commonCardMixin'
export default {
    mixins: [commonCardMixin],
    methods: {
        getOptions: function() {
            return {
                xAxis: {
                    type: 'category',
                    show: false,
                    boundaryGap: false // 消除X轴两侧边距
                },
                yAxis: {
                    show: false,
                },
                series: [{
                    type: 'line',
                    data: [620, 432, 220, 534, 790, 430, 220, 320, 532, 320, 834, 690, 530, 220, 620],
                    areaStyle: {
                        // 去掉 coLor 默认填充天蓝色
                        // 去掉 areaStyle 无填充色
                        color: 'purple',
                    },
                    lineStyle: {
                        width: 2,
                        color: 'red',
                    },
                    itemStyle: {
                        // 点的透明度
                        opacity: 0.5,
                    },
                    // 折线图平滑
                    smooth: true
                }],
                grid: {
                    top: 0,
                    bottom: 0,
                    left: 0,
                    right: 0,
                }
            }
        }
    }
    // mounted() {
    //     const chartDom = document.getElementById('total-orders-chart')
    //     const chart = this.$echarts.init(chartDom)
    //     chart.setOption({
    //         xAxis: {
    //             type: 'category',
    //             show: false,
    //             boundaryGap: false
    //         },
    //         yAxis: {
    //             show: false,
    //         },
    //         series: [{
    //             type: 'line',
    //             data: [620, 432, 220, 534, 790, 430, 220, 320, 532, 320, 834, 690, 530, 220, 620],
    //             areaStyle: {
    //                 color: 'purple',
    //             },
    //             lineStyle: {
    //                 width: 0
    //             },
    //             itemStyle: {
    //                 opacity: 0
    //             },
    //             smooth: true
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

<style lang="">
</style>
