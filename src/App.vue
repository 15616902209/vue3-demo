<template>
  <Index/>
<!--  <Test/>-->
  <ChangeColor/>
</template>

<script>
import Index from './components/Index.vue'
// import Test from './components/page/Test.vue'
import ChangeColor from './components/page/ChangeColor.vue'
export default {
  name: 'App',
  components: {
    Index,
    // Test,
    ChangeColor
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
