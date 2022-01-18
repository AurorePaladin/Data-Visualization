<template>
    <common-card title="今日交易用户" value="81,014">
    <template v-slot:wrapper>
        <div id="total-orders-chart" :style="{ width: '100%',height: '100%'}"></div>
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
    mixins: [commonCardMixin]
}
</script>

<style lang="">
</style>
