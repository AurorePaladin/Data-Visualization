<template>
  <div class="home">
    <TopView />
  </div>
</template>
<script>
// @ is an alias to /src
import TopView from '../components/TopView'
export default {
  name: 'Home',
  components: {
    TopView
  }
}
</script>
<style>
  .home {
    width: 100%;
    height: 100%;
    padding: 20px;
    background: #eee;
    box-sizing: border-box;
  }
</style>
