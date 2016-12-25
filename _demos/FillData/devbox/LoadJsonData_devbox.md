
#### JSON 데이터    

RealGrid의 DataProvider에 입력할 수 있는 JSON 포멧의 데이터는 배열(Array)형 데이터와 동일한 구조를 갖습니다. 즉, 

- 순수한 값(value)의 목록(list)인 구조, 즉 값의 배열
- name: value 쌍으로 이루어진 속성의 집합(collection)인 구조의 배열

위 두 가지 유형의 데이터 포멧은 왼쪽 메뉴 [Array 데이터 가져오기]({{ "/FillData/LoadArrayData/" | prepend: site.baseurl }})에서 `LocalDataProvider.setRows()`함수를 이용해 GridView에 로드 할 수 있다는 사실을 확인 할 수 있습니다.

JSON 포멧의 데이터는 [LocalDataProvider.fillJsonData()](http://help.realgrid.com/api/LocalDataProvider/fillJsonData/)함수를 이용해 조금더 유연하게 데이터를 읽어 올 수 있습니다.
함수의 인자는 `data`와 [DataFillOptions](http://help.realgrid.com/api/types/DataFillOptions/)객체인 `options`가 있습니다.

`options`에 대해서는 아래 `DataFillOptions` 영역의 데모를 확인하세요.    

#### 순수한 값의 목록으로 이루어진 배열

[LocalDataProvider.fillJsonData()](http://help.realgrid.com/api/LocalDataProvider/fillJsonData/)함수를 써서 `값의 목록으로 이루어진 배열`을 그리드에 넣는 코드를 작성해 보겠습니다.

```js
var data = [
  ["국산", "국산", "2", "기아", "15", "더 뉴 K9", "9", "미드나이트 블랙", "2016-01-01", "16", "8620", "대형", "휘발유", "images/215.png", "images/215.png"],
  ["국산", "국산", "5", "르노삼성", "2", "QM6", "3", "이온 실버", "2016-01-01", "71", "3470", "중형SUV", "휘발유", "images/502.png", "images/502.png"],
  ["국산", "국산", "5", "르노삼성", "5", "SM7", "9", "미드나이트 블랙", "2016-01-01", "26", "3820", "준대형", "휘발유", "images/505.png", "images/505.png"]
]

dataProvider.fillJsonData(data, {fillMode: "set"});
```

[LocalDataProvider.fillJsonData()](http://help.realgrid.com/api/LocalDataProvider/fillJsonData/)함수를 써서 값의 목록으로 이루어진 배열을 그리드에 넣는 코드를 작성해 보겠습니다.

<a class="btn primary small round lowercase" id="fillJsonData1">배열형 JSON 데이터 로드</a>

#### name: value 집합 구조의 배열 

```js
var data = [
  {
        "produce": "수입차",
        "country": "유럽",
        "brandNo": "14",
        "brandName": "재규어",
        "modelNo": "3",
        "modelName": "All New XF 20t",
        "colorNo": "3",
        "color": "이온 실버",
        "salesDay": "2016-01-01",
        "salesQty": "3",
        "price": "9090",
        "vehicleType": "중형",
        "fuel": "휘발유",
        "사진파일명": "images/1403.png",
        "판매월": "1"
    },
    {
        "produce": "수입차",
        "country": "유럽",
        "brandNo": "14",
        "brandName": "재규어",
        "modelNo": "5",
        "modelName": "XE 20d",
        "colorNo": "5",
        "color": "소닉 실버",
        "salesDay": "2016-01-01",
        "salesQty": "10",
        "price": "4990",
        "vehicleType": "준중형",
        "fuel": "휘발유",
        "사진파일명": "images/1405.png",
        "판매월": "1"
    }
]

dataProvider.fillJsonData(data, {fillMode: "set"});
```

<a class="btn primary small round lowercase" id="fillJsonData2">name: value형 JSON 데이터 로드</a>


{% include_relative devbox/FillDataOptions.md %}


<script>
$('#fillJsonData1').click(function() {
  var data = [
    ["국산", "국산", "2", "기아", "15", "더 뉴 K9", "9", "미드나이트 블랙", "2016-01-01", "16", "8620", "대형", "휘발유", "images/215.png", "images/215.png"],
    ["국산", "국산", "5", "르노삼성", "2", "QM6", "3", "이온 실버", "2016-01-01", "71", "3470", "중형SUV", "휘발유", "images/502.png", "images/502.png"],
    ["국산", "국산", "5", "르노삼성", "5", "SM7", "9", "미드나이트 블랙", "2016-01-01", "26", "3820", "준대형", "휘발유", "images/505.png", "images/505.png"]
  ];

  dataProvider.fillJsonData(data, {fillMode: "set"});
});

$('#fillJsonData2').click(function() {
  var data2 = [
    {
          "produce": "수입차",
          "country": "유럽",
          "brandNo": "14",
          "brandName": "재규어",
          "modelNo": "3",
          "modelName": "All New XF 20t",
          "colorNo": "3",
          "color": "이온 실버",
          "salesDay": "2016-01-01",
          "salesQty": "3",
          "price": "9090",
          "vehicleType": "중형",
          "fuel": "휘발유",
          "사진파일명": "images/1403.png",
          "판매월": "1"
      },
      {
          "produce": "수입차",
          "country": "유럽",
          "brandNo": "14",
          "brandName": "재규어",
          "modelNo": "5",
          "modelName": "XE 20d",
          "colorNo": "5",
          "color": "소닉 실버",
          "salesDay": "2016-01-01",
          "salesQty": "10",
          "price": "4990",
          "vehicleType": "준중형",
          "fuel": "휘발유",
          "사진파일명": "images/1405.png",
          "판매월": "1"
      }
  ]

  dataProvider.fillJsonData(data2, {fillMode: "set"});
});

</script>