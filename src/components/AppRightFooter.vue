<template>
	<div>
	  		<b-button id="cs" :size="'lg'" :variant="'danger'" v-on:click="allocateAddress('cs')">조선일보</b-button>
	  		<b-button id="ja" :size="'lg'" :variant="'danger'" v-on:click="allocateAddress('ja')">중앙일보</b-button>
	  		<b-button id="da" :size="'lg'" :variant="'danger'" v-on:click="allocateAddress('da')">동아일보</b-button>
	</div>



</template>

<script type="text/javascript">
	export default{
		methods: {
			allocateAddress(id){
				let address;
				if(id=="cs")
				{
					address="http://m.chosun.com";
					this.$emit('allocateAddress',address);
					
				}
				else if(id=="ja")
				{
					address="https://mnews.joins.com";
					this.$emit('allocateAddress',address);
					
				}
				else if(id=="da")
				{
					address="http://m.donga.com";
					this.$emit('allocateAddress',address);
					
				}
			}
		}
	}
</script>

<style type="text/css">
	
</style>
