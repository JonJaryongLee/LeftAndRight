<template>
  <div id="app">
    <AppLeft></AppLeft>
    <AppRight></AppRight>
    <AppFooter></AppFooter>
  </div>
</template>

<script>
  // bootstrap
  import Vue from 'vue'
  import BootstrapVue from 'bootstrap-vue'
  Vue.use(BootstrapVue);
  import 'bootstrap/dist/css/bootstrap.css'
  import 'bootstrap-vue/dist/bootstrap-vue.css'

  import AppLeft from './components/AppLeft.vue'
  import AppRight from './components/AppRight.vue'
  import AppFooter from './components/AppFooter.vue'

  
  export default{
    components: {
      'AppLeft': AppLeft,
      'AppRight': AppRight,
      'AppFooter':AppFooter
    }
  }
</script>

<style>
#app {
  font-family: 'Nanum Barun Gothic', sans-serif;
}
</style>
