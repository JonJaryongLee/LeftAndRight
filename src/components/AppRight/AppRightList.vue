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
		data(){
			return{
				articleDatas:
				[
					[
						"'고용참사' 실업자수 1999년 이후 최대…청년부터 4050까지 모두 일자리 줄었다(재종합)",
						"http://m.chosun.com/svc/article.html?sname=biz&contid=2018091201096",
						"2018.09.12"
					],
					[
						"실업자 113만명 외환위기후 최대...8월 취업자 증가폭 고작 3000명(종합)",
						"http://m.chosun.com/svc/article.html?sname=biz&contid=2018091200643",
						"2018.09.12"
					],
					[
						"8월 청년 실업률 10.0%…1999년 8월 이후 최고",
						"http://m.chosun.com/svc/article.html?sname=biz&contid=2018091200465",
						"2018. 9. 12"
					],
					[
						"\"만성질환 넵병\" 오피스 모큐멘터리 '회사가기싫어' 12일 첫 방송",
						"http://m.chosun.com/svc/article.html?sname=news&contid=2018091000963",
						"2018. 9. 10"
					],
					[
						"'일본 취업' 바늘구멍은 넓다… 월급봉투는 생각보다 얇다",
						"http://m.chosun.com/svc/article.html?sname=biz&contid=2018091000007",
						"2018. 9. 10"
					]
				],

				dataTitles:[],
				dataAddresses:[],
				dataDates:[]
			}

		},
		created(){
			for(let i=0; i<this.articleDatas.length; i++){
				this.dataTitles.push(this.articleDatas[i][0]);
				this.dataAddresses.push(this.articleDatas[i][1]);
				this.dataDates.push(this.articleDatas[i][2]);
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