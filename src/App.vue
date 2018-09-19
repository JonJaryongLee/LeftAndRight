<template>
  <div id="app">
    <b-container class="layout">
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

  import AppLeft from './components/AppLeft.vue'
  import AppRight from './components/AppRight/AppRight.vue'

  
  export default{
    components: {
      'AppLeft': AppLeft,
      'AppRight': AppRight

    },

    data(){
      return{
        pageData: ''
      }
    },


    methods: {
      sendPageData(){
        this.pageData = document.getElementById("leftIframe");
        console.log(this.pageData);
        axios.post('/find_relation', 
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

.left{
  font-family: 'Ubuntu', sans-serif;
}


</style>
