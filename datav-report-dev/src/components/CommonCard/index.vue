<template>
    <div>
        <div class="title">1</div>
        <div class="value">2</div>
        <div class="chart">3</div>
        <div class="line">4</div>
        <div class="total">
            <today-user />
            <total-orders/>
        </div>
    </div>
</template>

<script>
import TodayUser from '../TodayUser'
import TotalOrders from '../TotalOrders'
export default {
    components: {
        TodayUser,
        TotalOrders
    }
}
</script>

<style></style>
