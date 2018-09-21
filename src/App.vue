<template>
  <div id="app">
    <transition name="welcomeAppear">
      <div class ="welcome" v-if="welcomeShow">
        <h1 id="welcomeTitle">LeftAndRight</h1>
        <p id="welcomeMessage">환영합니다. 언론사를 선택하세요.</p>
        <button id="chosun" v-on:click="gotoMain('chosun')">조선일보</button>
        <button id="hani" v-on:click="gotoMain('hani')">한겨레</button>
      </div>
    </transition>
    <transition name="mainAppear">
      <div v-if="mainShow">
        <b-container class="layout">
          <b-row>
              <b-col class="left">
                <AppLeft v-bind:propsdata="journalismAddress"></AppLeft>
              </b-col>
              <b-col class="right">
                  <AppRight v-bind:propsdata="journalismAddress" v-on:sendPageData="sendPageData" ></AppRight>
              </b-col>
          </b-row>
        </b-container>
      </div>
    </transition>
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
        journalismAddress:'',
        journalismName:'',
        welcomeShow: true,
        mainShow: false,
        pageData: ''
      }
    },


    methods: {
      sendPageData(){
        this.pageData = document.getElementById("leftIframe");
        console.log(this.pageData);
        if(this.journalismAddress=="http://m.hani.co.kr")
          this.journalismName="hani";
        else
          this.journalismName="chosun";
        console.log(this.journalismAddress);
        console.log(this.journalismName);
        axios({
          method: 'post',
          url: 'http://find_relation',
          data:
            {
              journalism: this.journalismName,
              iframeInfo: this.pageData
            }
        })
        .then(function(response) {console.log(response);})
        .catch(function(error) {console.log(error);});
      },
      gotoMain(receivedJournalism){
        if(receivedJournalism=="hani")
        {
          this.journalismAddress="http://m.hani.co.kr"
        }
        else{
          this.journalismAddress="http://m.chosun.com/"
        }
        this.welcomeShow=false;
        this.mainShow=true;
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


</style>
