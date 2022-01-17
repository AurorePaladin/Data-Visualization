<template>
    <div>
        <div class="title">1</div>
        <div class="value">2</div>
        <div class="chart">3</div>
        <div class="line">4</div>
        <div class="total">
            <today-users />
            <total-users />
            <total-orders/>
        </div>
    </div>
</template>

<script>
import TodayUsers from '../TodayUsers'
import TotalUsers from '../TotalUsers'
import TotalOrders from '../TotalOrders'
export default {
    components: {
        TodayUsers,
        TotalUsers,
        TotalOrders
    }
}
</script>

<style></style>
