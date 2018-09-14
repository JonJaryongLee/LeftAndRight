<template>
	<div class="moreNews">
		<transition name="smallBtnAppear">
			<span v-if="smallBtnShow" class="smallNewsContainer">
				<button class="smallNewsBtn button button-box button-tiny" v-on:click="smallSendPageData">
				<i class="far fa-newspaper"></i>
				</button>
			</span>
		</transition>
			<br>
			<br>
			<br>
			<transition name="listAppear">
				<AppRightList v-if="listShow"></AppRightList>
			</transition>
			<br>
			<br>
			<article>
			<transition name="titleFade">
				<p v-if="titleShow">조선일보 관련기사를 검색할까요?
				</p>
			</transition>
			</article>
			<br>
			<br>
		<transition name="bigBtnFade">
			<span v-if="bigBtnShow" class="bigNewsContainer">
				<button class="bigNewsBtn button button-box button-tiny" v-on:click="bigSendPageData">
					<i class="far fa-newspaper"></i>
				</button>
			</span>
		</transition>
	</div>
</template>

<script type="text/javascript">
	import AppRightList from './AppRightList'
	import AppRighIframe from './AppRightIframe'
	export default{
		components:{
			'AppRightList':AppRightList,
			'AppRighIframe':AppRighIframe
		}
		,
		data(){
			return{
				bigBtnShow:true,
				titleShow:true,
				smallBtnShow:false,
				listShow:false
			}
		},
		methods: {
			bigSendPageData(){
				this.titleShow=false;
				this.bigBtnShow=false;
				this.smallBtnShow=true;
				this.$emit('sendPageData')
				setTimeout(() => this.listShow = true, 450);
			},
			smallSendPageData(){
				this.$emit('sendPageData')
			}
		}
	}

	
</script>



<style scoped>

	.titleFade-leave-active {
	  transition: opacity 0.4s;
	}
	.titleFade-leave-to {
	  opacity: 0;
	}

	.bigBtnFade-leave-active{
		transition: opacity 0.4s;
	}
	.bigBtnFade-leave-to{
		opacity: 0;
	}

	.smallBtnAppear-enter
	{
		opacity: 0;
	}

	.smallBtnAppear-enter-active
	{
		transition: opacity 2s;
	}
	.smallBtnAppear-enter-to
	{
		opacity: 1;
	}

	.listAppear-enter
	{
		opacity: 0;
	}

	.listAppear-enter-active
	{
		transition: opacity 2s;
	}
	.listAppear-enter-to
	{
		opacity: 1;
	}

	.moreNews{
		height:780px;
		width:540px;
		border-style:solid;
		background-color: #F6F6F8;
	}
	article{
		font-family: 'Nanum Barun Gothic', sans-serif;
		font-size: 1.9rem;
		text-align: center;
		padding: 50px;
		
	}

	.bigNewsContainer{
		 border-radius: 10px 10px 10px 10px;
		 display: block; 
		 width: 33%; 
		 height: auto; 
		 margin: 0 auto;
	}

	.bigNewsBtn{
		width: 165px;
		height: 200px;
		font-size: 8rem;
		
	}

	.smallNewsContainer{
		border-radius: 10px 10px 10px 10px;
		float: right;

	}
	.smallNewsBtn{
		width: 100px;
		height: 90px;
		font-size: 5rem;
		
	}

</style>

