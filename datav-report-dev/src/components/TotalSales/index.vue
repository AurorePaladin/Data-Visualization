<template>
    <common-card title="累积销售额" value="￥ 32,039,165">
    <template v-slot:wrapper>
        <div class="compare-wrapper">
            <div class="compare">
          <span>日同比</span>
          <span class="emphasis">7.33%</span>
        </div>
        <div class="compare">
          <span>月同比</span>
          <span class="emphasis">38.79%</span>
        </div>
        </div>
    </template>
    <template v-slot:footer>
        <span>昨日销售额</span>
        <span class="emphasis">￥ 300,000,000</span>
    </template>
    </common-card>
</template>

<script>
import commonCardMixin from '../../mixins/commonCardMixin'
export default {
    mixins: [commonCardMixin]
}
</script>

<style lang="scss" scoped>
    .compare {
        display: flex;
        align-items: center;
        font-size: 12px;
        margin-top: 3px;
        color: #666;
    }
</style>
