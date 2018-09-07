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
            <AppRight v-on:sendPageData="sendPageData"></AppRight>
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
  import AppSearched from './components/AppSearched.vue'

  
  export default{
    components: {
      'AppHeader': AppHeader,
      'AppLeft': AppLeft,
      'AppRight': AppRight,
      'AppSearched': AppSearched
    },

    data(){
      return{
        pageData: ''
      }
    },


    methods: {
      sendPageData(){
        this.pageData = document.getElementById("left");
        console.log(this.pageData);
        axios.post('/url', 
          this.pageData)
        .then(function(response) {console.log(response);})
        .catch(function(error) {console.log(error);});
      }
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
  padding:15px;
  text-align: center;

}
</style>
