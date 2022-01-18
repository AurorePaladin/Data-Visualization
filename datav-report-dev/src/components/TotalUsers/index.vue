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
            color: ['#3398DB'],
            xAxis: {
                type: 'category',
                data: ['00:00', '01:00', '02:00', '03:00', '04:00', '05:00', '06:00', '07:00', '08:00', '09:00', '10:00', '11:00', '12:00', '13:00'],
                show: false,
                barWidth: '60%'
            },
            yAxis: {
                show: false,
            },
            series: [{
                type: 'bar',
                data: [410, 82, 200, 334, 390, 330, 220, 150, 82, 200, 290, 134, 290, 330, 150],
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
