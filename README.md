node-red-contrib-navershopping
================

Node-RED node for navershopping



## Install

To install the stable version use the `Menu - Manage palette - Install`
option and search for node-red-contrib-navershopping, or run the following
command in your Node-RED user directory, typically `~/.node-red`

    npm install node-red-contrib-navershopping

## Wrapper naver shopping  API  
- https://developers.naver.com/docs/serviceapi/search/shopping/shopping.md
- 네이버 쇼핑 검색 API

## Sample parameters
```js

msg.url = 'https://openapi.naver.com/v1/search/shopping.json';

msg.params = {};
msg.params.query = '후드티셔츠'; // # 검색어
msg.params.display = "3" // # 검색 결과 출력 건수 지정, 10(기본값), 100(최대)
msg.params.sort = 'date' //# 정렬 옵션: sim (기본:유사도순), date (날짜순), asc(가격오름차순) ,dsc(가격내림차순)
msg.params.start = "1" //# 검색 시작 위치로 최대 1000까지 가능,  1(기본값), 1000(최대)

return msg;

```
## Sample flows
```json
[{"id":"5c0da6a5.202e48","type":"navershopping","z":"fbe560b0.5c19f","name":"","query":"후드티셔츠","display":"2","sort":"sim","start":"1","creds":"c3445ce8.7914d","x":460,"y":260,"wires":[["9a632ad0.8c7068"]]},{"id":"f14c5780.0e37a8","type":"inject","z":"fbe560b0.5c19f","name":"","props":[{"p":"payload"},{"p":"topic","vt":"str"}],"repeat":"","crontab":"","once":false,"onceDelay":0.1,"topic":"","payload":"","payloadType":"date","x":140,"y":260,"wires":[["b0bf9df0.b9368"]]},{"id":"9a632ad0.8c7068","type":"debug","z":"fbe560b0.5c19f","name":"","active":true,"tosidebar":true,"console":false,"tostatus":false,"complete":"payload","targetType":"msg","statusVal":"","statusType":"auto","x":670,"y":260,"wires":[]},{"id":"b0bf9df0.b9368","type":"function","z":"fbe560b0.5c19f","name":"","func":"msg.params = {};\nmsg.params.query = '후드티셔츠'; // # 검색어\nmsg.params.display = \"3\" // # 검색 결과 출력 건수 지정\nmsg.params.sort = 'date' //# 정렬 옵션: sim (유사도순), date (날짜순), asc(가격오름차순) ,dsc(가격내림차순)\nmsg.params.start = \"1\" //# 검색 시작 위치로 최대 1000까지 가능\nreturn msg;","outputs":1,"noerr":0,"initialize":"","finalize":"","x":280,"y":260,"wires":[["5c0da6a5.202e48"]]},{"id":"c3445ce8.7914d","type":"navershoppingApiKey","name":""}]
```

## Sample Results
```json
{"lastBuildDate":"Tue, 27 Apr 2021 07:31:39 +0900","total":5061752,"start":1,"display":2,"items":[{"title":"남자 봄 7부 블랙 레터링 오버핏 반팔 박스 <b>후드티</b>","link":"https://search.shopping.naver.com/gate.nhn?id=81813683218","image":"https://shopping-phinf.pstatic.net/main_8181368/81813683218.1.jpg","lprice":"19800","hprice":"","mallName":"서번트","productId":"81813683218","productType":"2","brand":"","maker":"","category1":"패션의류","category2":"남성의류","category3":"티셔츠","category4":""},{"title":"나이키 남성용 NSW 클럽 BB 풀오버 <b>후드티</b> BV2654 100","link":"https://search.shopping.naver.com/gate.nhn?id=23135095393","image":"https://shopping-phinf.pstatic.net/main_2313509/23135095393.20200921155548.jpg","lprice":"32360","hprice":"","mallName":"네이버","productId":"23135095393","productType":"1","brand":"나이키","maker":"나이키","category1":"패션의류","category2":"남성의류","category3":"티셔츠","category4":""}]}
```
