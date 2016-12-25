
#### FillDataOptions    

그리드에 데이터를 로드하기 위한 세 함수가 있습니다.

- [fillJsonData(data, options)](http://help.realgrid.com/api/LocalDataProvider/fillJsonData/)
- [fillXmlData(data, options)](http://help.realgrid.com/api/LocalDataProvider/fillXmlData/)
- [fillCsvData(data, options)](http://help.realgrid.com/api/LocalDataProvider/fillCsvData/)

이 함수들에는 공통적으로 [DataFillOptions](http://help.realgrid.com/api/types/DataFillOptions/)형의 `options`라는 두번째 인자가 정의되어 있습니다.

[DataFillOptions](http://help.realgrid.com/api/types/DataFillOptions/)를 이용해 그리드를 데이터에 로드하기 위한 여러가지 옵션을 설정 할 수 있습니다.

`fillMode`속성으로 데이터를 채우는 방법을 선택 할 수 있습니다.


그리드의 모든 데이터를 지우고 아래 `data`를 채웁니다.

<a class="btn primary small round lowercase" id="fillModeSet">SET으로 채우기</a>

```js
var data = [
    ["수입차", "유럽", "15", "랜드로버", "7", "Range Rover 3.0 TDV6", "4", "슬릭 실버", "2016-01-03", "5", "16780", "대형SUV", "경유", "images/1507.png", "images/1507.png"],
    ["수입차", "유럽", "17", "랜드로버", "6", "IS 200t", "5", "소닉 실버", "2016-01-03", "5", "5730", "중형", "휘발유", "images/1706.png", "images/1706.png"],
    ["수입차", "유럽", "18", "랜드로버", "2", "Accord 3.5", "9", "미드나이트 블랙", "2016-01-03", "1", "4260", "준대형", "휘발유", "images/1802.png", "images/1802.png"],
    ["수입차", "유럽", "19", "랜드로버", "8", "370Z", "4", "슬릭 실버", "2016-01-03", "9", "5190", "스포츠카", "휘발유", "images/1908.png", "images/1908.png"]
]

dataProvider.fillJsonData(jsonData, 
  {fillMode: "set"}
);
```

<a class="btn primary small round lowercase" id="fillModeAppend">APPEND로 추가하기</a>

그리드의 마지막행 뒤에 `jsonData`의 첫 번째 행에서 두개 행(`BMW 데이터`)을 가져와 `추가(Append)` 합니다. 이 작업을 위해 `DataFillOptions`의 `start`, `count`속성을 사용합니다. 

```js
var jsonData = [
    ["수입차", "유럽", "7", "BMW", "1", "520D", "2", "화이트 크림", "2016-01-01", "7", "6370", "준대형", "경유", "images/701.png", "images/701.png"],
    ["수입차", "유럽", "7", "BMW", "5", "730Ld", "7", "커피 빈", "2016-01-03", "1", "13270", "대형", "경유", "images/705.png", "images/705.png"],
    ["수입차", "유럽", "8", "벤츠", "10", "SL400", "11", "폴리시드 메탈", "2016-11-14", "1", "13200", "스포츠카", "휘발유", "images/810.png", "images/810.png"]", "
    ["수입차", "유럽", "8", "벤츠", "4", "CLS 400", "1", "크리스탈 화이트", "2016-11-15", "3", "16990", "준대형", "휘발유", "images/804.png", "images/804.png"]", "
    ["수입차", "유럽", "9", "아우디", "3", "A7 40TDI", "10", "팬텀 블랙", "2016-05-12", "2", "7880", "준대형", "경유", "images/903.png", "images/903.png"]", "
    ["수입차", "유럽", "9", "아우디", "6", "A8 50TDI", "3", "이온 실버", "2016-05-13", "2", "12670", "대형", "경유", "images/906.png", "images/906.png"]
]

dataProvider.fillXmlData(jsonData, 
  {fillMode: "append", start: 0, count: 2}
);
```

`jsonData`에서 `벤츠` 데이터를 가져와 2행 위치에 `삽입(Insert)` 합니다. 

<a class="btn primary small round lowercase" id="fillModeInsert">INSERT로 삽입하기</a>

```js
dataProvider.fillJsonData(jsonData, 
  {fillMode: "insert", start: 2, count: 2, fillPos: 2}
);
```

`jsonData`에서 `아우디` 데이터를 가져와 5행 위치에 있는 데이터를 `덮어쓰기(Update)` 합니다.

<a class="btn primary small round lowercase" id="fillModeUpdate">UPDATE로 덮어쓰기</a>

```js
dataProvider.fillJsonData(jsonData, 
  {fillMode: "update", start: 4, count: 2, fillPos: 4}
);
```

<script>
    var jsonData1 = [
        ["수입차", "유럽", "15", "랜드로버", "7", "Range Rover 3.0 TDV6", "4", "슬릭 실버", "2016-01-03", "5", "16780", "대형SUV", "경유", "images/1507.png", "images/1507.png"],
        ["수입차", "유럽", "17", "랜드로버", "6", "IS 200t", "5", "소닉 실버", "2016-01-03", "5", "5730", "중형", "휘발유", "images/1706.png", "images/1706.png"],
        ["수입차", "유럽", "18", "랜드로버", "2", "Accord 3.5", "9", "미드나이트 블랙", "2016-01-03", "1", "4260", "준대형", "휘발유", "images/1802.png", "images/1802.png"],
        ["수입차", "유럽", "19", "랜드로버", "8", "370Z", "4", "슬릭 실버", "2016-01-03", "9", "5190", "스포츠카", "휘발유", "images/1908.png", "images/1908.png"]
    ]

    var jsonData2 = [
        ["수입차", "유럽", "7", "BMW", "1", "520D", "2", "화이트 크림", "2016-01-01", "7", "6370", "준대형", "경유", "images/701.png", "images/701.png"],
        ["수입차", "유럽", "7", "BMW", "5", "730Ld", "7", "커피 빈", "2016-01-03", "1", "13270", "대형", "경유", "images/705.png", "images/705.png"],
        ["수입차", "유럽", "8", "벤츠", "10", "SL400", "11", "폴리시드 메탈", "2016-11-14", "1", "13200", "스포츠카", "휘발유", "images/810.png", "images/810.png"],
        ["수입차", "유럽", "8", "벤츠", "4", "CLS 400", "1", "크리스탈 화이트", "2016-11-15", "3", "16990", "준대형", "휘발유", "images/804.png", "images/804.png"],
        ["수입차", "유럽", "9", "아우디", "3", "A7 40TDI", "10", "팬텀 블랙", "2016-05-12", "2", "7880", "준대형", "경유", "images/903.png", "images/903.png"],
        ["수입차", "유럽", "9", "아우디", "6", "A8 50TDI", "3", "이온 실버", "2016-05-13", "2", "12670", "대형", "경유", "images/906.png", "images/906.png"]
    ]

$("#fillModeSet").click(function() {
    dataProvider.fillJsonData(jsonData1, {fillMode: "set"});    
});

$("#fillModeAppend").click(function() {
    dataProvider.fillJsonData(jsonData2, {fillMode: "append", start: 0, count: 2});    
});

$("#fillModeInsert").click(function() {
    dataProvider.fillJsonData(jsonData2, {fillMode: "insert", start: 2, count: 2, fillPos: 2});
});

$("#fillModeUpdate").click(function() {
    dataProvider.fillJsonData(jsonData2, {fillMode: "update", start: 4, count: 2, fillPos: 4});
});
</script>