<template>

	<div class="showRightNews">
    <article class="emptyBox"></article>
		<iframe
      	src="http://m.chosun.com/" 
      	height="670px" 
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
    height:510px;
    width:530px;
    border-style:none;
    background-color: #F6F6F8;
  }

  #rightIframe
  {
    border-style: none;
  }

  .emptyBox{
    height: 34px;
  }

</style>



