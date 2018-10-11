# leftandrightwebpack

> A Vue.js project

## Build Setup

``` bash
# install dependencies
npm install

# serve with hot reload at localhost:8080
npm run dev

# build for production with minification
npm run build

# build for production and view the bundle analyzer report
npm run build --report

# run unit tests
npm run unit

# run e2e tests
npm run e2e

# run all tests
npm test
```

For a detailed explanation on how things work, check out the [guide](http://vuejs-templates.github.io/webpack/) and [docs for vue-loader](http://vuejs.github.io/vue-loader).

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

## 9월 4일 회의내용
1. 밑에 버튼 없앨 것
2. 첫 이용시 사용자가 좌파와 우파 신문 중에 뭘 볼지 결정하게 하고 그걸 쿠키로 써서 다음에 그대로 보게 적용 (문윤기가 할 일)
3. 한쪽 진영의 페이지를 서핑하다 기사를 클릭하면 반대편 칸에 이 기사와 관련한 상대진영 기사를 리스트업
4. 그 중 하나를 클릭하면 그 기사로 이동한다.
5. 누른 기사 주소나 제목을  백엔드로 준다.

## 9월 4일 작업내용
1. 아래 버튼 삭제

## 9월 7일 작업내용
1. 오른쪽 레이아웃을 결과가 뜨는 페이지로 변경, 레이아웃 창 크기 늘림.

## 9월 8일 작업내용
전체적인 스타일을 바꿀 계획임. header를 없애고 제목을 left로 뺐음. 

## 9월 11일
1.사용자 최초 사용시 큰 아이콘과 설명이 뜨게 함. 아이콘을 누를 경우 작은 아이콘으로 바뀜.
2.버튼 누르면 리스트 뜨게 만듦
3. 문제는 리스트 페이지로 바뀌기 전에 두 개의 엘리먼트가 겹쳐서 틩기는 현상 발생. 추후 수정예정

## 9월 13일 작업내용
1. 리스트를 버튼으로 예쁘게 꾸밈
2. 버튼을 누르면 해당 신문기사가 새 창으로 뜨게 함. 추후 아이프레임에 뜨도록 조치할 예정
3. 날짜 뱃지 부착함

## 9월 14일 작업내용
1. 화면 전환이 부자연스러운 문제 해결. 두 개의 엘리먼트가 겹치면서 제목과 버튼이 버튼 클릭하자마자 아래로 밀려내려갔는데, setTimeOut함수를 통해 나타날 엘리먼트를 고의적으로 지연시킴.

## 9월 15일 작업내용
1. 리스트를 누르면 해당 기사의 아이프레임이 뜨게 조치함. 

## 9월 19일 작업내용
1. undo버튼 만듦.
2. left와 right iframe의 높이 맞춤.

## 9월 20일 작업내용
1. 화살표 바꿈
2. axios 손보는중
3. 검색기능 제작중
4. 모달 제작중

## 9월 21일 작업내용
1. right부분 css내용 확 줄임
2. 검색어 미입력시 모달 뜨게 함.
3. 검색어 axios로 전송
4. 웰컴페이지 제작중
5. 서버로 전송하는 데이터 수정.

## 9월 22일 작업내용
1. 인트로페이지 제작완료. css로 백그라운드 전체를 채우고 싶었으나 그냥 포기
2. 웹팩심플에서 웹팩으로 옮겨버림. 두 가지 문제를 발견함
	1. 자꾸 unexpected token에러가 발생함. 원인불명
	2. 조선일보가 최초 아이프레임에 이식되면 모바일로 인식되어져 클릭이 잘 안됨.

## 9월 23일 작업내용
1. 어제 기술한 두 가지 에러 해결함. vue파일 구조 바꿈.
2. 웹팩으로 dev서버로 올리는 게 아니라 빌드시켜봄. /dist파일에 저장되나 파일을 클릭한다고 실행되는건 아님. 메모리에 바로 저장된다고 함.

## 9월 30일 작업내용
1. 초기화면 뒷배경 없애버림
2. axios연동 성공했으나 iframe정보는 못 보내는중. 일단 search기능에만 집중하기로.
3. 위에 공백 만듦

##10월 10일 작업내용
1. 서버 테스트중
2. 제목 맨 마지막에 pdf다운로드 고칠 것
3. 현재 리스트업되며 보이는 자료가 영 안 예쁨. 정렬방식을 바꾸던지 할 것.
4. 다음과 같은 에러 발생함
<!-- vue.esm.js:1741 TypeError: Cannot read property '5' of undefined
    at a.created (AppRightList.vue:27)
    at $e (vue.esm.js:2921)
    at a.t._init (vue.esm.js:4630)
    at new a (vue.esm.js:4798)
    at vue.esm.js:4310
    at init (vue.esm.js:4131)
    at vue.esm.js:5608
    at d (vue.esm.js:5555)
    at a.__patch__ (vue.esm.js:6130)
    at a.t._update (vue.esm.js:2670)
 -->
    해당 에러 원인분석에 힘쓸 것. 
5. 현재는 검색기능에 집중하고 있으며, 해당 아이프레임 정보를 받아오는 것은 미루고 있음. 아마 객체 자체를 전달해서 전송이 안 되는 게 아닐까 생각되는데, 문자열로 통째로 바꿔서 보내보도록 노력해 볼 것.
6. 전송방법에 사소한 문제가 있는데, 현재 데이터가 변경되었다는 플래그를 보내기 위해 title[5]에다가 플래그를 넣어 보내고 있음. 나중에 이 때문에 알 수 없는 오류가 생길 수 있으므로 플래그를 꼭 변경할 것.

## 10월 11일 작업내용
1. iframe정보를 못 보내는 이유는 객체를 스트링으로 바꾸지 않아서였음. 수정해서 테스트중.

