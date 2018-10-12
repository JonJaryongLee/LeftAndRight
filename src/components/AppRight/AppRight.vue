<template>
	<div class="moreNews shadow">
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
				<AppRightSearch 
				v-bind:propsdata="journalismName" 
				v-on:changeNewsData="changeNewsData" 
				v-if="searchShow">
				</AppRightSearch>
			</transition>
			<transition name="listAppear">
				<AppRightList 
					v-if="listShow"
					v-on:showPage="showPage"
					v-bind:newsData="newsData"
					v-bind:journalismName="journalismName"
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
				<button class="bigNewsBtn button button-box button-tiny" v-on:click="bigButtonActive">
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
			{
				this.journalismName="한겨레";
				this.newsData[1]=this.journalismName;
			}
			else{
				this.journalismName="조선일보";
				this.newsData[1]=this.journalismName;
			}
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
				undoShow:false,
				searchShow:false,
				listShow:false,
				rightIframeShow: false,
				rightAddress:"",
				journalismName:'',
				changedNewsTitles:[],
				changedNewsUrl:[],
				changedNewsDate:[],
				newsData:[] // 인덱스[0]번은 플래그, [1]번은 데일리 헤드라인 나열을 위한 언론사 이름

			}
		},
		methods: {
			bigButtonActive(){
				this.titleShow=false;
				this.bigBtnShow=false;
				setTimeout(() => this.searchShow = true, 450);
				setTimeout(() => this.listShow = true, 450);
			},
			showPage(address){
				this.listShow=false;
				this.searchShow=false;
				setTimeout(() => this.undoShow = true, 1200);
				this.rightAddress=address;
				setTimeout(() => this.rightIframeShow = true, 1200);
			},
			returnToList(){
				this.undoShow=false;
				this.rightIframeShow=false;
				setTimeout(() => this.searchShow = true, 1200);
				setTimeout(() => this.listShow = true, 1200);
			},
			changeNewsData(receivedTitle,receivedUrl,receivedDate){
				this.listShow=false;
				for(let i=0;i<5;i++){
					this.changedNewsTitles[i]=receivedTitle[i];
					this.changedNewsUrl[i]=receivedUrl[i];
					this.changedNewsDate[i]=receivedDate[i];
				}
				this.newsData[0]='true';
				this.newsData[2]=this.changedNewsTitles;
				this.newsData[3]=this.changedNewsUrl;
				this.newsData[4]=this.changedNewsDate;
				setTimeout(() => this.listShow = true, 1500);
			}
		}
	}

	
</script>



<style scoped>

	.titleFade-leave-active, .bigBtnFade-leave-active {
	  transition: opacity 0.4s;
	}

	.titleFade-leave-to, .bigBtnFade-leave-to,
	.undoBtnAppear-enter, .undoBtnAppear-leave-to,
	.listAppear-enter, .listAppear-leave-to,
	.searchAppear-enter, .searchAppear-leave-to,
	.iframeAppear-enter, .iframeAppear-leave-to
	{
	  opacity: 0;
	}

	.undoBtnAppear-enter-active,
	.listAppear-enter-active, .searchAppear-enter-active
	{
		transition: opacity 2s;
	}

	.undoBtnAppear-enter-to,
	.listAppear-enter-to, .searchAppear-enter-to,
	.iframeAppear-enter-to
	{
		opacity: 1;
	}

	.undoBtnAppear-leave-active,
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