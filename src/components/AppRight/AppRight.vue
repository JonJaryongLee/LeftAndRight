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
					<i class="fas fa-arrow-left"></i>
				</button>
			</span>
		</transition>
			<br>
			<br>
			<br>
			<transition name="iframeAppear">
				<AppRightIframe v-if="rightIframeShow" v-bind:propsdata="rightAddress" ></AppRightIframe>
			</transition>
			<transition name="searchAppear">
				<AppRightSearch v-bind:propsdata="journalismName" v-if="searchShow"></AppRightSearch>
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
				<p v-if="titleShow">{{
					journalismName}} 관련기사를 검색할까요?
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
	import AppRightIframe from './AppRightIframe'
	import AppRightSearch from './AppRightSearch'
	export default{
		props:['propsdata'],
		created(){
			if(this.propsdata=="http://m.chosun.com/")
				this.journalismName="한겨레"
			else
				this.journalismName="조선일보"
		},
		components:{
			'AppRightList':AppRightList,
			'AppRightIframe':AppRightIframe,
			'AppRightSearch':AppRightSearch
		}
		,
		data(){
			return{
				bigBtnShow:true,
				titleShow:true,
				smallBtnShow:false,
				undoShow:false,
				searchShow:false,
				listShow:false,
				rightIframeShow: false,
				rightAddress:"",
				journalismName:''
			}
		},
		methods: {
			bigSendPageData(){
				this.titleShow=false;
				this.bigBtnShow=false;
				this.smallBtnShow=true;
				this.$emit('sendPageData')
				setTimeout(() => this.searchShow = true, 450);
				setTimeout(() => this.listShow = true, 450);
			},
			smallSendPageData(){
				this.$emit('sendPageData')
			},
			showPage(address){
				this.listShow=false;
				this.searchShow=false;
				this.smallBtnShow=false;
				setTimeout(() => this.undoShow = true, 1200);
				this.rightAddress=address;
				setTimeout(() => this.rightIframeShow = true, 1200);
			},
			returnToList(){
				this.undoShow=false;
				setTimeout(() => this.smallBtnShow = true, 1200);
				this.rightIframeShow=false;
				setTimeout(() => this.searchShow = true, 1200);
				setTimeout(() => this.listShow = true, 1200);
			}
		}
	}

	
</script>



<style scoped>

	.titleFade-leave-active, .bigBtnFade-leave-active {
	  transition: opacity 0.4s;
	}

	.titleFade-leave-to, .bigBtnFade-leave-to,
	.smallBtnAppear-enter, .smallBtnAppear-leave-to,
	.undoBtnAppear-enter, .undoBtnAppear-leave-to,
	.listAppear-enter, .listAppear-leave-to,
	.searchAppear-enter, .searchAppear-leave-to,
	.iframeAppear-enter, .iframeAppear-leave-to
	{
	  opacity: 0;
	}

	.smallBtnAppear-enter-active, .undoBtnAppear-enter-active,
	.listAppear-enter-active, .searchAppear-enter-active
	{
		transition: opacity 2s;
	}

	.smallBtnAppear-enter-to, .undoBtnAppear-enter-to,
	.listAppear-enter-to, .searchAppear-enter-to,
	.iframeAppear-enter-to
	{
		opacity: 1;
	}

	.smallBtnAppear-leave-active, .undoBtnAppear-leave-active,
	.listAppear-leave-active, .searchAppear-leave-active,
	.iframeAppear-leave-active
	 {
	  transition: opacity 1s;
	}

	.iframeAppear-enter-active
	{
		transition: opacity 3s;
	}


	.moreNews{
		height:760px;
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