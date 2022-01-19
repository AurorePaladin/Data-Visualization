<template>
    <common-card title="累计用户数" value="1,087,503">
    <template v-slot:wrapper>
        <div id="total-users-chart" :style="{ width: '100%',height: '100%'}"></div>
    </template>
    <template v-slot:footer>
        <div class="total-users-footer">
            <span>日同比</span>
            <span class="emphasis">8.73%</span>
            <div class="increase" />
            <span class="month">月同比</span>
            <span class="emphasis">35.91%</span>
            <div class="decrease" />
        </div>
    </template>
    </common-card>
</template>

<script>
import commonCardMixin from '../../mixins/commonCardMixin'
export default {
    mixins: [commonCardMixin],
    mounted() {
        const chartDom = document.getElementById('total-users-chart')
        const chart = this.$echarts.init(chartDom)
        chart.setOption({
            xAxis: {
                type: 'value',
                show: false,
            },
            yAxis: {
                type: 'category',
                show: false,
            },
            series: [{
                type: 'bar',
                stack: '总量',
                data: [350],
                barWidth: 10,
                itemStyle: {
                    color: '#45c946'
                },
            },
            {
                type: 'bar',
                stack: '总量',
                data: [200],
                barWidth: 10,
                itemStyle: {
                    color: '#eee'
                },
            }],
            grid: {
                top: 0,
                bottom: 0,
                left: 0,
                right: 0,
            }
        })
    },
}
</script>

<style lang="scss">
    .total-users-footer {
        display: flex;
        align-items: center;
        .month {
            margin-left: 10px;
        }
    }
</style>
