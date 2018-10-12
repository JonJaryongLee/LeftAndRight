<template>

	<div class="showRightNews">
    <article class="emptyBox"></article>
		<iframe
      	src="http://m.chosun.com/" 
      	height="650px" 
      	width="530px" 
      	id="rightIframe"
    	>
      
    	</iframe>
	</div>
</template>

<script>
	export default{
		props: ['propsdata'],
		mounted(){
			document.getElementById("rightIframe").src=this.propsdata;
		}
	}
</script>

<style>
  .showRightNews{
    height:500px;
    width:530px;
    border-style:none;
    background-color: #F6F6F8;
  }

  #rightIframe
  {
    border-style: none;
  }

  .emptyBox{
    height: 32px;
  }

  @media(max-width: 1025px){
    .showRightNews{
      width:450px;
    }
    iframe{
      width: 450px;
      height:620px;
    }
  }

</style>



