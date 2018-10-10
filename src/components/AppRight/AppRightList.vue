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
		props:['propsdata']
		,
		data(){
			return{
				dataTitles:["풍등 날린 스리랑카인 '중대과실'? ... 법조계도 '과하다'","[단독] '정도경영' LG의 탈선... 총수일가 10년간 탈세 거래 연루","김진태 의원이 국감장에 '아기 고양이'를 데려온 이유","대법원이 '서초동 지근거리'명동으로 법원행정처 옮기겠다는데...","'자해만 해도 사형?'... 너무 많은 처벌조항"],
				dataAddresses:["http://m.hani.co.kr/arti/society/society_general/865203.html?_fr=mt1","http://m.hani.co.kr/arti/economy/economy_general/865149.html","http://m.hani.co.kr/arti/politics/assembly/865204.html","http://m.hani.co.kr/arti/society/society_general/865193.html","http://m.hani.co.kr/arti/society/society_general/865214.html"],
				dataDates:["2018.10.10","2018.10.10","2018.10.10","2018.10.10","2018.10.10"]
			}

		},
		created(){
			if(this.propsdata[0][5]){
				this.dataTitles=[];
				this.dataAddresses=[];
				for(let i=0; i<5; i++){
				this.dataTitles.push(this.propsdata[0][i]);
				this.dataAddresses.push(this.propsdata[1][i]);
				}
				console.log(this.dataAddresses);
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