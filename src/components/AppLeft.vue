<template>
	<div class="showNews shadow">
    <h1>Left And Right</h1>
		<iframe
      src="http://m.hani.co.kr" 
      height="650px" 
      width="530px" 
      id="leftIframe"
    >
      
    </iframe>
  </div>
</template>

<script type="text/javascript">
	export default{
    props: ['propsdata'],
    mounted(){
      document.getElementById("leftIframe").src=this.propsdata;
    }

	}
</script>

<style scoped>
  .showNews{
    height:760px;
    width:540px;
    border-style:none;
    background-color: #F6F6F8;
  }
  h1{
    font-family: 'Ubuntu', sans-serif;
    font-size:4rem;
    font-weight: 900;
    color: #4f5b66;
    padding: 10px;
  }
  #leftIframe
  {
    border-style: none;
  }
  .shadow
  {
  box-shadow: 5px 10px 10px rgba(0,0,0,0.03)
  }
  @media(max-width: 1025px){
    .showNews{
      width:450px;
      height: 730px;
    }
    iframe{
      width: 450px;
      height: 620px;
    }
    h1{
      font-size:3.5rem;
    }
  }

</style>



