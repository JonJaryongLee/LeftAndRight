<template>
  <div id="app">
    <b-container class="layout">
    <b-row>
        <b-col>
            <AppLeft></AppLeft>
        </b-col>
        <b-col>
            <AppRight></AppRight>
        </b-col>
    </b-row>
    <b-row align-v="end">
        <b-col align-self="end">
            <AppFooter></AppFooter>
        </b-col>
    </b-row>
    </b-container>
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
