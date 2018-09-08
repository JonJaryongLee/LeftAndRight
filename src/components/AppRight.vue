<template>
	<div class="moreNews">
		<article>
			<br>
			<br>
			<br>
			<br>
			<br>
			조선일보 관련기사를 검색할까요?
			<br>
			<br>
		</article>

		<span class="newsContainer">
			<button class="newsBtn button button-box button-tiny" v-on:click="sendPageData">
				<i class="far fa-newspaper"></i>
			</button>
		</span>
	</div>
</template>

<script type="text/javascript">
	export default{
		methods: {
			sendPageData(){
				this.$emit('sendPageData')
			}
		}
	}

	
</script>



<style scoped>

	.moreNews{
		height:910px;
		width:540px;
		border-style:solid;
	}
	article{
		font-family: 'Nanum Barun Gothic', sans-serif;
		font-size: 1.9rem;
		text-align: center;
		padding: 50px;
		
	}

	.newsContainer{
		 display: block; 
		 width: 33%; 
		 height: auto; 
		 margin: 0 auto;
	}

	.newsBtn{
		width: 200px;
		height: 200px;
		font-size: 10rem;
		
	}

</style>

