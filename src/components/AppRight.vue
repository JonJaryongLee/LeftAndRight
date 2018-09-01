<template>
	<div>
		<button v-on:click="test">click</button>
  		<!-- <b-embed type="iframe"
          aspect="1by1"
          src=""
          allowfullscreen
  		></b-embed> -->
	</div>
</template>

<script type="text/javascript">
	export default{
		props:['propsdata'],
		data(){
			return{
				
			}
		},
		
		methods: {
			test(){
				console.log(this.propsdata);
			}
		}
	}
</script>

<style type="text/css">
	
</style>

