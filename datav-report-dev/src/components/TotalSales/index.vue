<template>
    <common-card title="累积销售额" value="￥ 32,039,165">
    <template v-slot:footer>
        <span>昨日销售额</span>
        <span>￥ 300,000,000</span>
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
