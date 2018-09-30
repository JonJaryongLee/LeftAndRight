<template>
  <div class="start">
    <transition name="welcomeAppear">
      <div class ="welcome" v-if="welcomeShow">
        <h1 id="welcomeTitle">Left And Right</h1>
        <p id="welcomeMessage">환영합니다. 언론사를 선택하세요.</p>
        <button class="chosun button button-glow button-rounded button-caution" v-on:click="gotoMain('chosun')">조선일보</button>
        <button class="hani button button-glow button-rounded button-highlight" v-on:click="gotoMain('hani')">&nbsp&nbsp한겨레&nbsp&nbsp</button>
        
        
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

  import AppLeft from './AppLeft.vue'
  import AppRight from './AppRight/AppRight.vue'
  
  export default{
    name:'AppStart',
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
        setTimeout(() => this.mainShow = true, 1200);
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

.welcome{
    padding: 230px 0;
    border: none;
    text-align: center;
}

#welcomeTitle{
    font-family: 'Ubuntu', sans-serif;
    font-size:6rem;
    font-weight: 900;
    color: orange;
  }

#welcomeMessage{
  font-family:'Nanum Barun Gothic', sans-serif;
  font-size:2rem;
  padding: 50px;
}

.hani, .chosun {
  font-family: 'Nanum Barun Gothic', sans-serif;
}

.welcomeAppear-leave-active, 
.mainAppear-enter-active{
  transition: opacity 1s;
}

.welcomeAppear-leave-to, .mainAppear-enter{
  opacity: 0;
}

.mainAppear-enter-to{
  opacity: 1;
}



</style>