<template>
  <div class="energy-container">
    <div class="energy-content">
      <!-- 导航列表 -->
      <VTabs />
      <!-- 汽车展示列表 -->
      <CarList />
      <!-- 轮播图 -->
      <CarSwapper />
    </div>
  </div>
</template>

<script lang="ts">
import VTabs from '../../components/v-tabs/index.vue'
import CarList from './components/carList.vue'
import CarSwapper from './components/carSwapper.vue'

export default {
  name: 'index',
  components: {
    VTabs,
    CarList,
    CarSwapper,
  },
  data () {
    return {
    }
  },
  methods: {

  },
};
</script>

<style lang="scss">
.energy{
  &-container{
    width: 100%;
  }
  &-content{
    width: 1200px;
    margin: 0 auto;
  }
}
</style>
