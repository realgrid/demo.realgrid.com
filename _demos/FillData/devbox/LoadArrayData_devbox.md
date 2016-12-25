
#### Array 데이터    

아래와 같은 배열형 데이터를 GridView에 담을 수 있습니다.

```js
[
  ["국산", "국산", "2", "기아", "15", "더 뉴 K9", "9", "미드나이트 블랙", "Fri Jan 01 2016 00:00:00 GMT+0900 (KST)", "16", "8620", "대형", "휘발유", "images/215.png", "images/215.png"],
  ["국산", "국산", "5", "르노삼성", "2", "QM6", "3", "이온 실버", "Fri Jan 01 2016 00:00:00 GMT+0900 (KST)", "71", "3470", "중형SUV", "휘발유", "images/502.png", "images/502.png"],
  ["국산", "국산", "5", "르노삼성", "5", "SM7", "9", "미드나이트 블랙", "Fri Jan 01 2016 00:00:00 GMT+0900 (KST)", "26", "3820", "준대형", "휘발유", "images/505.png", "images/505.png"]
]
```   

javascript 배열형 데이터를 그리드에 담기 위해 [LocalDataProvider.setRows()](http://help.realgrid.com/api/LocalDataProvider/setRows/) 함수를 사용합니다.
배열 데이터는 필드의 순서대로 입력이 되며, 필드보다 데이터가 많던 적던 오류없이 입력됩니다.

```js
var data = [
  ["국산", "국산", "2", "기아", "15", "더 뉴 K9", "9", "미드나이트 블랙", "Fri Jan 01 2016 00:00:00 GMT+0900 (KST)", "16", "8620", "대형", "휘발유", "images/215.png", "images/215.png"],
  ["국산", "국산", "5", "르노삼성", "2", "QM6", "3", "이온 실버", "Fri Jan 01 2016 00:00:00 GMT+0900 (KST)", "71", "3470", "중형SUV", "휘발유", "images/502.png", "images/502.png"],
  ["국산", "국산", "5", "르노삼성", "5", "SM7", "9", "미드나이트 블랙", "Fri Jan 01 2016 00:00:00 GMT+0900 (KST)", "26", "3820", "준대형", "휘발유", "images/505.png", "images/505.png"]
]

dataProvider.setRows(data);
```

<a class="btn primary small round lowercase" id="setRows">배열형 데이터 추가</a>

#### Object Array 데이터    

`setRows()`함수는 javascript객체를 배열에 담아 그리드에 추가 할 수 도 있습니다. 

```js
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

dataProvider.setRows(data);

```

버튼을 눌러 실행하기 전에 왼쪽 그리드의 툴바에서 `필드`를 펼쳐 그리드에 적용된 필드 이름을 확인 하세요.
객체의 `name: value`에서 속성명인 `name`은 필드 이름과 매핑되며 해당 `value`가 필드의 값으로 입력됩니다. 아래 버튼을 눌러 동작을 확인하세요.

<a class="btn primary small round lowercase" id="setRows2">객체 배열 데이터 추가</a>

#### LocalDataProvider.setRows() 함수

[LocalDataProvider.setRows()](http://help.realgrid.com/api/LocalDataProvider/setRows/)함수는 DataProvider에 들어 있던 기존의 데이터를 모두 초기화한 다음 새로운 데이터를 추가합니다.
 
- `start` - 입력할 데이터의 시작 행
- `count` - 입력할 데이터의 행 수

인자를 이용해 데이터의 입력 위치 및 갯수를 제한 할 수 있습니다. 링크된 도움말 사이트를 참고하세요.

<script>
$('#setRows').click(function() {
  var data = [
    ["국산", "국산", "2", "기아", "15", "더 뉴 K9", "9", "미드나이트 블랙", "2016-01-01", "16", "8620", "대형", "휘발유", "images/215.png", "images/215.png"],
    ["국산", "국산", "5", "르노삼성", "2", "QM6", "3", "이온 실버", "2016-01-01", "71", "3470", "중형SUV", "휘발유", "images/502.png", "images/502.png"],
    ["국산", "국산", "5", "르노삼성", "5", "SM7", "9", "미드나이트 블랙", "2016-01-01", "26", "3820", "준대형", "휘발유", "images/505.png", "images/505.png"]
  ];

  dataProvider.setRows(data);
});

$('#setRows2').click(function() {
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

  dataProvider.setRows(data2);
});

</script>