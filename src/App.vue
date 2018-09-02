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
            <AppLeftFooter v-on:allocateAddress="allocateAddress"></AppLeftFooter>
        </b-col>
        <b-col class ="rightFooter">
            <AppRightFooter v-on:allocateAddress="allocateAddress"></AppRightFooter>
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
    data(){
      return {
        address:'no address'
      }
    },
    methods: {
      allocateAddress(receivedAddress){
        this.address=receivedAddress;
        
        //만약 조중동 중 하나이면 오른쪽 화면을 업데이트, 아니면 왼쪽으로 업데이트
        if(
            this.address=="http://m.chosun.com"||
            this.address=="https://mnews.joins.com/"||
            this.address=="http://m.munhwa.com/"
          ) 
        {
          document.getElementById("right").src = this.address;
        }
        else{
          document.getElementById("left").src = this.address;
        }

      }
    },
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
