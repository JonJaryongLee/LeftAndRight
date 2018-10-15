# Left and Right (좌우)
다른 성향의 두 언론사를 쉽게 비교하는 웹 앱

# 개발동기
진보와 보수로 나뉘어진 대한민국 언론 진영에선 관심 가지는 분야도, 하나의 사건을 바라보는 관점도 다릅니다. 나와 다른 생각에 좀 더 쉽게 접근하고자 이 앱을 제작하였습니다.

# 개발자
경상대 12 front-end:이자룡 (Vue)
경상대 14 back-end: 박성흠(Django)

# How to use
1.  인트로페이지에서 원하는 언론사를 선택합니다.

2.  해당 언론사 모바일페이지가 왼쪽 영역에 보여집니다. 만약 반대 성향의 언론 기사를 보고싶다면 오른쪽 버튼을 클릭합니다.

3.  타 언론사의 데일리 헤드라인 기사가 리스트업되고 검색창이 보여집니다. 아무것도 입력하지 않고 검색을 시도하면 경고 모달이 나타나며, 키워드를 입력 후 검색하면 http통신을 이용해 서버로 검색어를 보내고, 서버는 사용자에게 검색어와 가장 관련성이 높은 5개의 기사 정보를 전송합니다. 이후 클라이언트 영역에서 화면을 갱신합니다.

4.  나열된 기사 버튼을 클릭하면 리스트와 검색창이 사라지고 해당 기사의 URL이 이식된 iframe창이 나타납니다. 이전 과정으로 돌아가고 싶다면 뒤로 가기 버튼을 누릅니다.


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

