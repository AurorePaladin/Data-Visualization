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
                data: [200],
                barWidth: 10,
                itemStyle: {
                    color: '#45c946'
                },
            },
            {
                type: 'bar',
                stack: '总量',
                data: [250],
                barWidth: 10,
                itemStyle: {
                    color: '#eee'
                },
            },
            {
                type: 'custom',
                stack: '总量',
                data: [200],
                renderItem: (params, api) => {
                    // console.log(params, api);
                    const value = api.value(0)
                    const endPoint = api.coord([value, 0])
                    console.log(endPoint)
                    return {
                        type: 'group',
                        positions: endPoint,
                        children: [{
                            type: 'path',
                            position: endPoint,
                            shape: {
                                d: 'M886.6 694.6c-6.2 6.2-14.4 9.4-22.6 9.4H160c-8.2 0-16.4-3.1-22.6-9.4-6.2-6.2-9.4-14.4-9.4-22.6s3.1-16.4 9.4-22.6l352-352c6.2-6.2 14.4-9.4 22.6-9.4s16.4 3.1 22.6 9.4l352 352c6.2 6.2 9.4 14.4 9.4 22.6s-3.1 16.4-9.4 22.6z',
                                x: -5,
                                y: 7,
                                width: 10,
                                height: 10,
                            },
                            style: {
                                fill: '#45c946'
                            }
                        },
                        {
                            type: 'path',
                            position: endPoint,
                            shape: {
                                d: 'M886.6 329.4c-6.2-6.2-14.4-9.4-22.6-9.4H160c-8.2 0-16.4 3.1-22.6 9.4-6.2 6.2-9.4 14.4-9.4 22.6s3.1 16.4 9.4 22.6l352 352c6.2 6.2 14.4 9.4 22.6 9.4s16.4-3.1 22.6-9.4l352-352c6.2-6.2 9.4-14.4 9.4-22.6s-3.1-16.4-9.4-22.6z',
                                x: -5,
                                y: -17,
                                width: 10,
                                height: 10,
                            },
                            style: {
                                fill: '#45c946'
                            }
                        }],
                    }
                }
            }],
            grid: {
                top: 0,
                bottom: 0,
                left: 0,
                right: 0,
                // M886.6 329.4c-6.2-6.2-14.4-9.4-22.6-9.4H160c-8.2 0-16.4 3.1-22.6 9.4-6.2 6.2-9.4 14.4-9.4 22.6s3.1 16.4 9.4 22.6l352 352c6.2 6.2 14.4 9.4 22.6 9.4s16.4-3.1 22.6-9.4l352-352c6.2-6.2 9.4-14.4 9.4-22.6s-3.1-16.4-9.4-22.6z
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
