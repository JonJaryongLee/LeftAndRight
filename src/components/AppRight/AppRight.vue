<template>
	<div class="moreNews shadow">
		<transition name="smallBtnAppear">
			<span v-if="smallBtnShow" class="smallNewsContainer">
				<button class="smallNewsBtn button button-box button-tiny" v-on:click="smallSendPageData">
					<i class="far fa-newspaper"></i>
				</button>
			</span>
		</transition>

		<transition name="undoBtnAppear">
			<span v-if="undoShow" class="undoContainer">
				<button class="undoBtn button button-box button-tiny" v-on:click="returnToList">
					<i class="fas fa-undo"></i>
				</button>
			</span>
		</transition>
			<br>
			<br>
			<br>
			<transition name="iframeAppear">
				<AppRighIframe v-if="rightIframeShow" v-bind:propsdata="rightAddress" ></AppRighIframe>
			</transition>
			<transition name="listAppear">
				<AppRightList 
					v-if="listShow"
					v-on:showPage="showPage"
				></AppRightList>
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
				undoShow:false,
				listShow:false,
				rightIframeShow: false,
				rightAddress:""
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
			},
			showPage(address){
				this.listShow=false;
				this.smallBtnShow=false;
				setTimeout(() => this.undoShow = true, 1200);
				this.rightAddress=address;
				setTimeout(() => this.rightIframeShow = true, 1200);
			},
			returnToList(){
				this.undoShow=false;
				setTimeout(() => this.smallBtnShow = true, 1200);
				this.rightIframeShow=false;
				setTimeout(() => this.listShow = true, 1200);
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

	.smallBtnAppear-leave-active {
	  transition: opacity 1s;
	}
	.smallBtnAppear-leave-to {
	  opacity: 0;
	}

	.undoBtnAppear-enter
	{
		opacity: 0;
	}

	.undoBtnAppear-enter-active
	{
		transition: opacity 2s;
	}
	.undoBtnAppear-enter-to
	{
		opacity: 1;
	}

	.undoBtnAppear-leave-active {
	  	transition: opacity 1s;
	}
	.undoBtnAppear-leave-to {
		opacity: 0;
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

	.listAppear-leave-active {
	  transition: opacity 1s;
	}
	.listAppear-leave-to {
	  opacity: 0;
	}

	.iframeAppear-enter
	{
		opacity: 0;
	}

	.iframeAppear-enter-active
	{
		transition: opacity 3s;
	}
	.iframeAppear-enter-to
	{
		opacity: 1;
	}
	.iframeAppear-leave-active {
	  transition: opacity 1s;
	}
	.iframeAppear-leave-to {
	  opacity: 0;
	}

	.moreNews{
		height:780px;
		width:540px;
		border-style:none;
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
		width: 90px;
		height: 80px;
		font-size: 5rem;
		
	}
	.undoContainer{
		border-radius: 10px 10px 10px 10px;
		float: right;

	}
	.undoBtn{
		width: 90px;
		height: 70px;
		font-size: 4rem;
		
	}

  .shadow{
 		 box-shadow: 5px 10px 10px rgba(0,0,0,0.03)
	}
</style>

