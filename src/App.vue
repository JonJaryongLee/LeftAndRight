<template>
  <div id="app">
    <b-container class="layout">
    <b-row>
      <b-col class ="header">
        <AppHeader></AppHeader>
      </b-col>
    </b-row>
    <b-row>
        <b-col class="left">
            <AppLeft></AppLeft>
        </b-col>
        <b-col class="right">
            <AppRight></AppRight>
        </b-col>
    </b-row>
    <b-row>
        <b-col class = "leftFooter">
            <AppLeftFooter></AppLeftFooter>
        </b-col>
        <b-col class ="rightFooter">
            <AppRightFooter></AppRightFooter>
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

  import AppHeader from './components/AppHeader.vue'
  import AppLeft from './components/AppLeft.vue'
  import AppRight from './components/AppRight.vue'
  import AppLeftFooter from './components/AppLeftFooter.vue'
  import AppRightFooter from './components/AppRightFooter.vue'

  
  export default{
    components: {
      'AppHeader': AppHeader,
      'AppLeft': AppLeft,
      'AppRight': AppRight,
      'AppLeftFooter':AppLeftFooter,
      'AppRightFooter': AppRightFooter
    }
  }
</script>

<style>

.layout{
  display:flex;
  flex-direction: column;
  box-sizing:border-box;
}

.header{
  font-family: 'Ubuntu', sans-serif;
  border-bottom:1px solid gray;
  padding:20px;
  text-align: center;

}

.left{
  border-right:1px solid gray;
  padding: 10px;
}

.right{
  padding: 10px;
}

.leftFooter{
  font-family: 'Nanum Barun Gothic', sans-serif;
  border-top:1px solid gray;
  padding:20px;
  text-align: center;
}

.rightFooter{
  font-family: 'Nanum Barun Gothic', sans-serif;
  border-top:1px solid gray;
  padding:20px;
  text-align: center;
}
</style>
