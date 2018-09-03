# leftandright

> A Vue.js project

## Build Setup

``` bash
# install dependencies
npm install

# serve with hot reload at localhost:8080
npm run dev

# build for production with minification
npm run build
```

For detailed explanation on how things work, consult the [docs for vue-loader](http://vuejs.github.io/vue-loader).

## 교수님 의견

김민기 교수님
커서가 움직임에 따라 단어를 하이라이팅해서 클릭 시 반대편 섹션에 바로 관련기사 검색이 가능하게. 

이수원 교수님
우선 타겟을 정해야한다. 모든사람인가? 특정인인가?
현재 두 개의 웹페이지를 섹션에 가두어 띄우는 게 전부다. 단순히 보여주는 것 이상이 필요하다.
하나의 섹션에서 기사를 클릭하면 다른 섹션에서 관련기사를 자동으로 뜨게 하면 어떨까? 이미지검색, 제목의 특정 단어, 기사 내용안의 단어들을 이용해 알고리즘을 짜서 구현하면 될 것.

12 지동춘
검색기능이 있었으면 좋겠다. ex)북한 -> 두 개의 영역에 서로다른 언론사의 기사검색결과가 나오게
스크롤을 동시에 내리면 어떨까?
두 개의 언론사 UI가 통일되어 있지 않아 사용자에게 매력을 느끼게 하지 못한다. 차라리 주요기사를 크롤링해서 리스트하는 게 나을듯.


## 초기작업내용
1. Vue.js Webpack Simple로 초기구성을 하였습니다.
2. Favicon설정 완료
3. 기본 폰트는 나눔바른고딕입니다.
4. Bootstrap Vue 를 Import하였습니다.
5. fontAwesome cdn 추가

## 8월 25일
1. 하단부 버튼 추가. 버튼을 누르면 각 언론사 모바일 창이 뜨도록 설정 (일부 언론사는 pc에서 모바일 주소로 안 들어가짐)
2. 그리드 짜는중

## 8월 27일
1. 헤더 추가
2. 레이아웃 1차 제작
3. 아래 footer 둘로 나누고 위치바꿈
4. 전체 레이아웃에 flex적용
5. 전체 레이아웃 박스사이징 border-box로 설정
6. 왼쪽과 오른쪽 레이아웃에 언론사 홈페이지 이식시킴. iframe size 1by1

## 9월 1일
1. AppRightFooter.vue에서 AppRight.vue 로 데이터 보내기 성공

## 9월 2일
1. AppLeftFooter.vue에서 버튼을 클릭하면 AppRight.vue가 업데이트됨. 성공.
	- 어제는 AppRightFooter.vue에서 생성한 주소를 App.vue를 거쳐 AppRight.vue로 보내버렸는데 AppRight.vue에서 업데이트 인식을 못해서 즉시 연동이 안 되었음. 이에 App.vue에서 직접 AppRight.vue의 iframe src를 바꾸는 명령을 집어넣음. allocateAddress메소드 내부의 document.getElementById("~").src 참고할 것.
2. Left영역도 똑같이 적용.
3. 동아일보 모바일 웹 페이지 적용이 안 되어 문화일보로 변경