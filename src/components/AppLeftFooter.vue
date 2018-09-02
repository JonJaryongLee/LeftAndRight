<template>
	<div>
	

			<b-button id="hani" :size="'lg'" :variant="'warning'" v-on:click="allocateAddress('hani')">한겨레</b-button>
	  		<b-button id="gh" :size="'lg'" :variant="'warning'" v-on:click="allocateAddress('gh')">경향신문</b-button>
	  		<b-button id="oh" :size="'lg'" :variant="'warning'" v-on:click="allocateAddress('oh')">오마이뉴스</b-button>
	
	</div>

<!-- button-2.vue -->

</template>

<script type="text/javascript">
	export default{
		methods: {
			allocateAddress(id){
				let address;
				if(id=="hani")
				{
					address="http://m.hani.co.kr";
					this.$emit('allocateAddress',address);
					
				}
				else if(id=="gh")
				{
					address="http://m.khan.co.kr";
					this.$emit('allocateAddress',address);
					
				}
				else if(id=="oh")
				{
					address="http://m.ohmynews.com";
					this.$emit('allocateAddress',address);
					
				}
			}
		}
	}
</script>

<style type="text/css">
	
</style>