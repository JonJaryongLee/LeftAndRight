<template>
	<div class="showNews shadow">
    <h1>Left And Right</h1>
		<iframe
      src="http://m.chosun.com/" 
      height="670px" 
      width="530px" 
      id="leftIframe"
    >
      
    </iframe>
  </div>
</template>

<script type="text/javascript">
	export default{

	}
</script>

<style type="text/css">
  .showNews{
    height:780px;
    width:540px;
    border-style:none;
    background-color: #F6F6F8;
  }
  h1{
    font-family: 'Ubuntu', sans-serif;
    font-size:4rem;
    font-weight: bold;
    color: #FF7F00;
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

</style>



