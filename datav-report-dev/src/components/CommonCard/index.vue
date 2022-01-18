<template>
    <div>
        <div class="title">{{title}}</div>
        <div class="value">{{value}}</div>
        <div class="chart">
            <slot name="wrapper"></slot>
        </div>
        <div class="line" />
        <div class="total">
            <slot name="footer"></slot>
        </div>
    </div>
</template>

<script>
export default {
    props: {
        title: String,
        value: String
    }
}
</script>

<style lang="scss" scoped>
    .title {
        font-size: 12px;
        color: #999;
    }
    .value {
        font-size: 25px;
        color: #000;
        margin-top: 5px;
        letter-spacing: 1px;
    }
    .chart {
        height: 50px;
    }q
    .line {
        margin: 10px 0;
        border-bottom: 1px solid #000;
    }
    .total {
        font-size: 12px;
        color: #666;
    }
</style>

<style lang="scss">
    .emphasis {
        margin-left: 5px;
        color: #333;
        font-weight: 700;
    }
</style>
