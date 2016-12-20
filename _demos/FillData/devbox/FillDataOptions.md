
#### FillDataOptions    

그리드에 데이터를 로드하기 위한 세 함수가 있습니다.

- [fillJsonData(data, options)](http://help.realgrid.com/api/LocalDataProvider/fillJsonData/)
- [fillXmlData(data, options)](http://help.realgrid.com/api/LocalDataProvider/fillXmlData/)
- [fillCsvData(data, options)](http://help.realgrid.com/api/LocalDataProvider/fillCsvData/)

이 함수들에는 공통적으로 [DataFillOptions](http://help.realgrid.com/api/types/DataFillOptions/)형의 `options`라는 두번째 인자가 정의되어 있습니다.

[DataFillOptions](http://help.realgrid.com/api/types/DataFillOptions/)를 이용해 그리드를 데이터에 로드하기 위한 여러가지 옵션을 설정 할 수 있습니다.

`fillMode`속성으로 데이터를 채우는 방법을 선택 할 수 있습니다.


<a class="btn primary small round lowercase" id="fillModeSet">SET으로 채우기</a>

그리드의 모든 데이터를 지우고 `jsonData`를 채웁니다.

```js
var jsonData = [
  ["국산", "국산", "2", "기아", "15", "더 뉴 K9", "9", "미드나이트 블랙", "Fri Jan 01 2016 00:00:00 GMT+0900 (KST)", "16", "8620", "대형", "휘발유", "images/215.png", "images/215.png"],
  ["국산", "국산", "5", "르노삼성", "2", "QM6", "3", "이온 실버", "Fri Jan 01 2016 00:00:00 GMT+0900 (KST)", "71", "3470", "중형SUV", "휘발유", "images/502.png", "images/502.png"],
  ["국산", "국산", "5", "르노삼성", "5", "SM7", "9", "미드나이트 블랙", "Fri Jan 01 2016 00:00:00 GMT+0900 (KST)", "26", "3820", "준대형", "휘발유", "images/505.png", "images/505.png"]
]

dataProvider.fillJsonData(jsonData, {fillMode: "set"});
```

<a class="btn primary small round lowercase" id="fillModeSet">APPEND로 추가하기</a>

데이터를 마지막행 뒤에 `추가(Append)` 합니다.

```js
var xmlData = 
' \
<xml> \
';

dataProvider.fillXmlData(xmlData, {fillMode: "Append"});
```

<a class="btn primary small round lowercase" id="fillModeSet">INSERT로 삽입하기</a>

데이터를 2행에 `삽입(Insert)` 합니다.

```js
var dajsonObjectDatata = [
  {
        "국산/수입": "수입차",
        "국가": "유럽",
        "브랜드번호": "14",
        "브랜드명": "재규어",
        "모델번호": "3",
        "모델명": "All New XF 20t",
        "색상번호": "3",
        "색상": "이온 실버",
        "판매날짜": "2016-01-01",
        "판매수량": "3",
        "차량가격": "9090",
        "차종": "중형",
        "연료": "휘발유",
        "사진파일명": "images/1403.png",
        "판매월": "1"
    },
    {
        "국산/수입": "수입차",
        "국가": "유럽",
        "브랜드번호": "14",
        "브랜드명": "재규어",
        "모델번호": "5",
        "모델명": "XE 20d",
        "색상번호": "5",
        "색상": "소닉 실버",
        "판매날짜": "2016-01-01",
        "판매수량": "10",
        "차량가격": "4990",
        "차종": "준중형",
        "연료": "휘발유",
        "사진파일명": "images/1405.png",
        "판매월": "1"
    }
]

dataProvider.fillJsonData(jsonObjectData, {fillMode: "insert", fillPos: 2, count: 1});
```


<a class="btn primary small round lowercase" id="fillModeSet">UPDATE로 덮어쓰기</a>

데이터를 3행에 `덮어쓰기(Update)`합니다.

```js
var dajsonObjectData = [
  {
        "국산/수입": "수입차",
        "국가": "유럽",
        "브랜드번호": "14",
        "브랜드명": "재규어",
        "모델번호": "3",
        "모델명": "All New XF 20t",
        "색상번호": "3",
        "색상": "이온 실버",
        "판매날짜": "2016-01-01",
        "판매수량": "3",
        "차량가격": "9090",
        "차종": "중형",
        "연료": "휘발유",
        "사진파일명": "images/1403.png",
        "판매월": "1"
    },
    {
        "국산/수입": "수입차",
        "국가": "유럽",
        "브랜드번호": "14",
        "브랜드명": "재규어",
        "모델번호": "5",
        "모델명": "XE 20d",
        "색상번호": "5",
        "색상": "소닉 실버",
        "판매날짜": "2016-01-01",
        "판매수량": "10",
        "차량가격": "4990",
        "차종": "준중형",
        "연료": "휘발유",
        "사진파일명": "images/1405.png",
        "판매월": "1"
    }
]

dataProvider.fillJsonData(jsonObjectData, {fillMode: "update", fillPos: 2, count: 1});
```