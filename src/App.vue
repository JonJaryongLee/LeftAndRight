<template>
  <div id="app">
    <LeftAndRightHeader></LeftAndRightHeader>
    <LeftAndRightInput></LeftAndRightInput>
    <LeftAndRightList></LeftAndRightList>
    <LeftAndRightFooter></LeftAndRightFooter>
  </div>
</template>

<script>
  // bootstrap
  import Vue from 'vue'
  import BootstrapVue from 'bootstrap-vue'
  Vue.use(BootstrapVue);
  import 'bootstrap/dist/css/bootstrap.css'
  import 'bootstrap-vue/dist/bootstrap-vue.css'

  import LeftAndRightHeader from './components/LeftAndRightHeader.vue'
  import LeftAndRightInput from './components/LeftAndRightInput.vue'
  import LeftAndRightList from './components/LeftAndRightList.vue'
  import LeftAndRightFooter from './components/LeftAndRightFooter.vue'

  
  export default{
    components: {
      'LeftAndRightHeader': LeftAndRightHeader,
      'LeftAndRightList': LeftAndRightList,
      'LeftAndRightInput':LeftAndRightInput,
      'LeftAndRightFooter':LeftAndRightFooter
    }
  }
</script>

<style>
#app {
  font-family: 'Nanum Barun Gothic', sans-serif;
}
</style>
