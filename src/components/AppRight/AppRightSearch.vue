<template>
  <div>
    <article class="searchBoxUpperEmpty"></article>
    <article class="searchBox shadow">
      <input type="text" v-model="newSearchData" placeholder="검색어를 입력하세요" v-on:keyup.enter="search">
      <span class="searchContainer" v-on:click="search">
        <article class="searchBtnUpperEmpty"></article>
        <i class="searchBtn fas fa-search" aria-hidden="true"></i>
      </span>
    </article>
  </div>
</template>

<script>
	export default{
    data(){
      return {
        newSearchData:''
      }
    },
    methods:{
      search(){
        if(this.newSearchData !== "")
        {
          let value = this.newSearchData && this.newSearchData.trim();
          localStorage.setItem(this.newSearchData,this.newSearchData);
          this.clearSearch();
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

</style>



