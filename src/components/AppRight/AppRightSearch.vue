<template>
  <div>
    <article class="searchBoxUpperEmpty">
    </article>
    <article class="searchBox shadow">
      <input type="text" v-model="newSearchData" placeholder="검색어를 입력하세요" v-on:keyup.enter="search">
      <span class="searchContainer" v-on:click="search">
        <article class="searchBtnUpperEmpty"></article>
        <i class="searchBtn fas fa-search" aria-hidden="true"></i>
      </span>
      
      <modal v-if="showModal" @close="showModal=false">
        <span slot="body" @click="showModal=false">
          검색어를 입력하세요.
          <i class="closeModalBtn fas fa-times" aria-hidden="true"></i>
        </span>
      </modal>

    </article>
  </div>
</template>

<script>
import Modal from './common/Modal.vue'
	export default{
    props:['propsdata'],
    created(){
      if(this.propsdata=="한겨레")
        this.journalismName="chosun";
      else
        this.journalismName="hani";
    },
    components:{
      Modal: Modal
    },
    data(){
      return {
        journalismName:'',
        newSearchData:'',
        showModal:false,
        receivedTitle:[],
        receivedUrl:[]
      }
    },
    methods:{
      search(){
        if(this.newSearchData !== "")
        {
          let wordToSearch = this.newSearchData && this.newSearchData.trim();

        axios({
          method: 'post',
          // url: '/search',
          url: '/search_web',
          data: 
            {
              journalism: this.journalismName,
              keyword: wordToSearch
            }

        })
        .then(response =>{
          this.receivedTitle = [];
          this.receivedUrl = [];
          for(let i=0;i<5;i++){
            this.receivedTitle.push(response.data[i].title);
            this.receivedUrl.push(response.data[i].url);
            }
            this.$emit('changeNewsData',this.receivedTitle,this.receivedUrl);
          })
        .catch(function(error) {console.log(error);});
          this.clearSearch();
        } else{
          this.showModal = !this.showModal;
        }
        
    },
    clearSearch() {
      this.newSearchData='';
    }
	}
}
</script>

<style scoped>
  input:focus{
    outline: none;
  }

  .searchBoxUpperEmpty{
    height:34px;
  }
  .searchBox{
    background: white;
    height:50px;
    line-height: 46px;
    border-radius: 5px;
  }
  .searchBox input{
    position: relative;
    left:20px;
    display: inline;
    height:50px;
    width: 450px;
    border-style: none;
    font-family: 'Nanum Barun Gothic', sans-serif; 
    font-size:1.3rem;
  }
  .searchContainer{
    
    float:right;
    background: linear-gradient(to right, #6478FB, #8763FB);
    display: block;
    height:50px;
    width:3rem;
    border-radius: 0 5px 5px 0;
  }
  .searchBtnUpperEmpty{
    height:10px;
  }
  .searchBtn{
    display: block;
    font-size:1.8rem;
    text-align: center;
    color:white;
    height:50px;
    /*vertical-align: middle;*/
  }
  .closeModalBtn{
    color:orange;
  }

</style>



