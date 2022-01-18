<template>
    <common-card title="累积订单量" value="￥ 2,157,420">
    <template v-slot:footer>
        <span>昨日订单量</span>
        <span class="emphasis">￥ 200,000,000</span>
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
