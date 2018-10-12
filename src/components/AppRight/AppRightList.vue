<template>
	<div>
		<article>
			<br>
				<button class="button button-rounded button-tiny" v-for="i in 5" v-on:click="showPage(dataTitles[i-1])">
					{{dataTitles[i-1]}} 
					<br> 
					<b-badge>{{dataDates[i-1]}}</b-badge>
				</button>
		</article>
	</div>
</template>

<script>
	export default{
		props: ['newsData']

		,
		data(){
			return{
				haniDailyDataTitles:["국감: 전직 아나운서 \"화려하다? 노동조건 엉망\"","\"교비로 성인용품 구매\"...'비리 유치원' 실명 공개","이재명 자택 및 신체 압수수색...이 지사 \"6년 지나, 납득 어렵다\"","\"생계형\"이라더니...MB, 2009년 살인범 320명 '특별사면' 왜?","'만 10살 이하 집주인'8139명...세습사회 문턱에 선 한국"],
				haniDailyDataAddresses:["http://m.hani.co.kr/arti/politics/assembly/865528.html","http://m.hani.co.kr/arti/politics/assembly/865512.html","http://m.hani.co.kr/arti/society/area/865564.html","http://m.hani.co.kr/arti/society/society_general/865572.html","http://m.hani.co.kr/arti/economy/economy_general/865523.html"],
				csDailyDataTitles:["'회복세' 진단 포기한 정부, \"경기 하방리스크 확대\"","\"청와대 지시다, 단기 일자리 빨리 만들어라\"","문대통령 \"서해 NLL 계속 피로 지킬 수 없어\"","미 재무부 대북 제재 준수 요청... 금감원 책임론 불거져","제주기지 결정 때 청와대 실장이었는데... 이젠 \"절차에 문제\""],
				csDailyDataAddresses:["http://m.chosun.com/svc/article.html?sname=biz&contid=2018101201254","http://m.chosun.com/svc/article.html?sname=biz&contid=2018101200265","http://m.chosun.com/svc/article.html?sname=news&contid=2018101201466","http://m.chosun.com/svc/article.html?sname=news&contid=2018101201622","http://m.chosun.com/svc/article.html?sname=news&contid=2018101200304"],
				dataTitles:[],
				dataAddresses:[],
				dataDates:["2018.10.12","2018.10.12","2018.10.12","2018.10.12","2018.10.12"]
			}

		},
		created(){


			if(this.newsData[1]=='한겨레'){
				for(let i=0; i<5; i++){
					this.dataTitles.push(this.haniDailyDataTitles[i]);
					this.dataAddresses.push(this.haniDailyDataAddresses[i]);
				}
			}
			if(this.newsData[1]=='조선일보'){
				for(let i=0; i<5; i++){
					this.dataTitles.push(this.csDailyDataTitles[i]);
					this.dataAddresses.push(this.csDailyDataAddresses[i]);
				}
			}
			if(this.newsData[0]){
				this.dataTitles=[];
				this.dataAddresses=[];
				this.dataDates=[];
				for(let i=0; i<5; i++){
				this.dataTitles.push(this.newsData[2][i]);
				this.dataAddresses.push(this.newsData[3][i]);
				this.dataDates.push(this.newsData[4][i]);
				}
			}
		},

		methods: {
			showPage(dataTitle){
				let address;
				for(let i=0; i<this.dataTitles.length;i++){
					if (dataTitle==this.dataTitles[i]) {
						address=this.dataAddresses[i];
						this.$emit('showPage',address);
					}
				}
			}
		}
	}

</script>

<style scoped>
	button{
		font-family: 'Nanum Barun Gothic', sans-serif;
		font-size:1.4rem;
		line-height: 1.5em;
		font-weight:bold;
		float:left;
		text-align: right;
		width: 511px;
		height:95px;
		margin: 10px;
	}
</style>